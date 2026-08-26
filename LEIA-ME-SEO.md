# O que eu mudei no seu projeto (já pronto, sem passos manuais)

## Domínio usado
Encontrei `conservadorapaulista.com.br` no e-mail de contato do site (Sobre.html, index.html
etc.) e usei `https://www.conservadorapaulista.com.br` em todas as tags de SEO. Se o domínio
real for outro, me avisa que eu gero de novo em segundos com o certo.

## O que foi adicionado
- **`posts/` (70 arquivos .html)** — uma página própria por artigo do blog, com título e
  meta description únicos, Open Graph, dados estruturados (JSON-LD) e o conteúdo já escrito
  direto no HTML (o Google não depende mais de JavaScript rodar pra ver o artigo).
- **`sitemap.xml`** e **`robots.txt`** na raiz — apontando pra todas as 70 páginas de post +
  7 páginas de listagem do blog. Não existiam antes.

## O que foi substituído
- **`blog.html`** (e as novas `blog-2.html` até `blog-7.html`) — a listagem do blog, que antes
  era montada 100% via JavaScript (`innerHTML`), agora é HTML estático de verdade, com links
  `<a href="posts/...">` reais em vez de `onclick` + `localStorage`.

## O que foi removido do lugar (não apagado)
- **`post.html`** e **`post.js`** — o sistema antigo, que dependia de `localStorage` pra
  mostrar o conteúdo do post (por isso o Google não indexava nada individualmente). Movi os
  dois pra `_sistema-antigo-post-backup/`, só de garantia — nenhuma outra página do site
  dependia deles, então isso não quebra nada. Pode apagar essa pasta quando quiser.

## Uma limpeza extra que fiz nos dados
As descrições dos 68 posts mais antigos vinham cortadas no meio de uma palavra (ex:
"Separamos os demais mo ..."), porque foi assim que o conteúdo original do outro site foi
copiado. Eu limpei automaticamente esse corte em todas as páginas (removi a palavra quebrada
e fechei a frase com ponto), mas o texto continua sendo o resumo original — só não termina
mais no meio de uma palavra.

## Único ponto que ainda vale melhorar (não é bloqueio pra indexar)
O corpo de cada artigo usa o mesmo "esqueleto" de texto, trocando só o título e o resumo
inicial/final. Isso já é suficiente pra o Google indexar cada post com URL, título e
descrição próprios — mas, com o tempo, vale reescrever o corpo dos posts mais importantes
com conteúdo mais específico, pra reduzir a repetição entre eles.

## Pra subir no ar
1. Suba a pasta inteira (como está) pro seu servidor/hospedagem, substituindo a versão atual.
2. Envie o `sitemap.xml` pro Google Search Console (Sitemaps → adicionar novo sitemap).
