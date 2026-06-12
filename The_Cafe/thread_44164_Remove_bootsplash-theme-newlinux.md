---
title: "Remove bootsplash-theme-newlinux"
date: 2005-06-24
forum: The Cafe
---

### Post by tasca on 2005-06-24
Hi,

somebody knows to decide this?

tasca@softsul:~ $ sudo dpkg --remove bootsplash-theme-newlinux
(Lendo banco de dados ... 74073 arquivos e diretórios atualmente instalados.)
Removendo bootsplash-theme-newlinux ...
dpkg: erro processando bootsplash-theme-newlinux (--remove):
 subprocesso pre-removal script retornou código de saída de error 10
Erros foram encontrados durante processamento de:
 bootsplash-theme-newlinux
tasca@softsul:~ $

and

tasca@softsul:~ $ sudo apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Corrigindo dependências... Pronto
Os pacotes a seguir serão REMOVIDOS:
  bootsplash-theme-newlinux
0 pacotes atualizados, 0 pacotes novos instalados, 1 a serem removidos e 537 não atualizados.
2 pacotes não totalmente instalados ou removidos.
É preciso fazer o download de 0B de arquivos.
Depois de desempacotar, 877kB de espaço em disco serão liberados.
Quer continuar? [S/n]s
(Lendo banco de dados ... 74073 arquivos e diretórios atualmente instalados.)
Removendo bootsplash-theme-newlinux ...
dpkg: erro processando bootsplash-theme-newlinux (--remove):
 subprocesso pre-removal script retornou código de saída de error 10
Erros foram encontrados durante processamento de:
 bootsplash-theme-newlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
tasca@softsul:~ $

I do not obtain to remove this maledeto


congratulations...   tasca

---

