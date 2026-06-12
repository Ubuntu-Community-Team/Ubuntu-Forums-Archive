---
title: "Oracle Forms 6 installation and Ubuntu"
date: 2009-09-24
forum: Server Platforms
---

### Post by chrissk_2 on 2009-09-24
Hello, 

i am a long time user of Linux and software development manager in a very large software company. I just got a request from an extremely large customer (600 shops with 1-50 pc each) who wants to move from Windows 95-98-2000-XP platforms to open source (Linux) including Ubuntu.

He wants to setup about 600 servers (1 for each sale area) and as many desktops as possible to Linux. The servers will be some flavor of Red Hat and the desktops all Ubuntu.

The applications that need to be converted are Oracle DB(easy to convert from Windows to Linux), a large number of small utilities (not required to convert immediately or at all, they can remain in a small number of windows PCs), a huge number of POS(Point of Sales) which can not be converted (at the moment) and a rather large number of back office clients running Oracle Forms. The later is the biggest problem and the reason i ask for assistance.

I just read the installation manual of Oracle Forms and it requires glibc 2.1.1 or later, kernel 2.2.5 or later and a number of X libs (libX11, libXext, libXmu, libXp, libXpm, libXt, libXtst).

Since the client asks for a recent version of ubuntu (probably 9.04 or even 10.4 LTS when it is released) i would like to know if Ubuntu can support the above requirements. Oracle Forms 6 is currently unsupported by Oracle but the software is running for many years on the customer and can not be rewritten. 

I googled a bit and i read that a few people had problems with the installation due to unresolved symbols in Libc. Also the path that it expects to find the X libs (/usr/X11R6/lib) does not exist. 

What steps do i have to take to ensure that i will not have any problems deploying the software ?? Is Ubuntu compatible with such ancient setups ??

Is there any person qualified to answer these questions from the Ubuntu team ??
If so please post an e-mail to contact privately since i can not post any more info in public mails 

Thanks in advance

---

