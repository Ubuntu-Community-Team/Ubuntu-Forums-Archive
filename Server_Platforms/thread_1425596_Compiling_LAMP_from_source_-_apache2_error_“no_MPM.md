---
title: "Compiling LAMP from source - apache2 error “no MPM package installed”"
date: 2010-03-09
forum: Server Platforms
---

### Post by kenny99 on 2010-03-09
Hi, I've compiled LAMP from source on a Ubuntu VPS. I had to remove a previously installed version of Apache then I manually compiled all the packages, which seems to have worked up unto a point - however, when I try to run commands like "/etc/init.d/apache2 restart" I get the following error - No apache MPM package installed. I have installed mpm-prefork so I don't know why i'm getting this problem. My configure command is as follows:

./configure --enable-so --enable-modules=most --with-mpm=prefork

I have deliberately not used apt-get to install anything and want to avoid this if possible.

Anyone have any guidance on how to resolve this error? Thanks in advance

---

