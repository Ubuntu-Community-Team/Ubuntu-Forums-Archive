---
title: "php5 installation directory"
date: 2010-06-09
forum: Server Platforms
---

### Post by fouadk on 2010-06-09
hey everyone...

i have installed LAMP on ubuntu server 10.04
where can i find the installation folder...the extension folder and so on ?
i tried the command locate php but it didnt return the path i wanted.

thanks in advance

---

### Post by Bachstelze on 2010-06-09
Normally, you shouldn't worry about that because the package manager deals with installation of extensions, etc.. If you really have to install extensions manually, put them in /usr/lib/php5.

---

### Post by fouadk on 2010-06-09
thanks again...
i need to add browscap support for php
i need to specify a location to browscap file in php.ini
i thought about putting the browscap file in /etc/php5/apache2/ but i was wondering if it were the right place to place it

---

