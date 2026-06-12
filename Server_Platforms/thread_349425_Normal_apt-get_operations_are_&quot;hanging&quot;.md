---
title: "Normal apt-get operations are &quot;hanging&quot;"
date: 2007-01-30
forum: Server Platforms
---

### Post by thiago_moreira on 2007-01-30
Hi, 

I'm currently installing and configuring an Ubuntu i686 server, and today I'm experiencing a problem with apt-get operations (install, update, dist-upgrade, etc.). Every time, that I'm trying to perform one of these operations, the system stays inactive. :( 

One example: when I try to perform an "apt-get update" operation:

root@ead:~# apt-get update
0% [Waiting for headers] [Waiting for headers]

Another example: when I try to perform an "apt-get install xxxxxx" operation:

root@ead:~# apt-get install php5-pgsql
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências
Reading state information... Pronto
Os NOVOS pacotes a seguir serão instalados:
  php5-pgsql
0 pacotes atualizados, 1 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso fazer o download de 41,7kB de arquivos.
Depois de desempacotamento, 164kB adicionais de espaço em disco serão usados.
AVISO : Os pacotes a seguir não podem ser autenticados !
  php5-pgsql
Instalar estes pacotes sem verificação [s/N] ? s
0% [Aguardando por cabeçalhos]

(sorry, but it is in Brazilian Portuguese, the default language chosen on the installation... but I think you guys understood my problem...)

And this is it. It stays on this state, and nothing else is performed. The strangest is that other networking operations such as "ping", "wget" or when I access a web site using the "links" web browser, all of them work just fine.

At a first moment, I thought the repositories were down, but I'm accessing them normally via web browser, or on the "links" web browser.

Anybody already have experienced this problem? Can anybody help me with that?

Thanks in advance, folks. :)

---

### Post by jimbren on 2007-01-30
I'm totally reaching, but I'm curious to know if there's a problem somewhere with a package installation.  

Have you tried using the -f option to find and fix any broken packages?

```
sudo apt-get install -f
```

Also, what happens if you invoke aptitude instead of apt-get?

[CODEsudo aptitude install whatever-package[/CODE]

jimbo

---

### Post by thiago_moreira on 2007-01-30
The problem is there aren't any broken packages within the installation. Yesterday (monday), everything was working fine. And now I can't use the apt-get commands properly.

I tried to invoke the "aptitude" command, instead of the "apt-get" ones, but it still doesn't work... :(

Note that the other services that involve network access are working, such as "ping" or "wget", for example.

---

### Post by Surgeon General on 2007-01-30
could it be with your sources.list ? have you tried different servers?

---

### Post by thiago_moreira on 2007-01-31
Well, I've tried to change some servers on the "sources.list" file, but I got some mixed results.

The "apt-get", as well as "aptitude" operations are working fine with some packages, but when I try to install a package like "php5-pgsql", for example, the operation is still hanging.

root@ead:~# apt-get install php5-pgsql
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências
Reading state information... Pronto
Os NOVOS pacotes a seguir serão instalados:
  php5-pgsql
0 pacotes atualizados, 1 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso fazer o download de 41,7kB de arquivos.
Depois de desempacotamento, 164kB adicionais de espaço em disco serão usados.
0% [Aguardando por cabeçalhos]

And this is it... The operations work with some packages, but not all of them...

Any other ideas would be very appreciated. :) 

Thanks in advance, folks.

---

