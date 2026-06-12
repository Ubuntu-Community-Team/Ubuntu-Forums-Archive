---
title: "pgsql support disabled in php"
date: 2005-04-19
forum: Server Platforms
---

### Post by sbalea on 2005-04-19
Hi all,

I'm having some problem with php4 and pgsql support on a new kubuntu installation. Apparently the support for pgsql was left out when the php package was built (--without-pgsql). I'm guessing this is due to the inclusion of the dbx extension which made all previous DB support modules redundant. 

However, we have an application that relies on pgsql. Is there any easy way to enable it, short of recompiling php4? If I do need to recompile, what is the apt-get friendly way of doing it? I'm new to debian based distros, I've spent my last 10 years in rpm land....

Thanks in advance

Mihai

---

### Post by HungSquirrel on 2005-04-19
Have you tried installing the php4-pgsql package?  From the description:

> This package provides a module for PostgreSQL database connections
directly from PHP scripts.

I assume that's what you're looking for.

---

### Post by ebrowne on 2005-04-20
I'm not using Kubuntu but installing that package worked for me php4-pgsql  I'm running egroupware on postgresql

---

### Post by sbalea on 2005-04-20
[QUOTE=ebrowne]I'm not using Kubuntu but installing that package worked for me php4-pgsql  I'm running egroupware on postgresql[/QUOTE]
 I have the php4-pgsql extension installed. When I do a php_info(), the configure command shows '--without-pgsql'. Does the extension work even if it is disabled in the core? Could anybody please check if php_info() shows pgsql enabled on their systems?

Thanks

---

### Post by sbalea on 2005-04-20
All right, I solved the problem. I was looking at the wrong php.ini file... I was used to it being in /etc when in fact it was in /etc/php4/apache. It seems to work fine now

Thanks for your help
Mihai

---

