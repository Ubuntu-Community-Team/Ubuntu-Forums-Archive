---
title: "Apache 2.2.14 apache.conf is lost"
date: 2009-11-26
forum: Server Platforms
---

### Post by zennix on 2009-11-26
Hi there, I'm new at Ubuntu. I need help please to get a fresh copy of apache2.conf (Server version 2.2.14 (as I missed up with my copy of the file :) ) 

Moreover, it would be nice if there is some white-paper guide to help in the explanation of the apache2.conf contents. 

Many thanks in advance :)

---

### Post by munky99999 on 2009-11-26
[https://help.ubuntu.com/9.10/serverguide/C/httpd.html](https://help.ubuntu.com/9.10/serverguide/C/httpd.html)

sudo apt-get --reinstall apache2

should restore the file you are missing.

---

### Post by zennix on 2009-11-26
Thanks man, I appreciate your help. The file has been restored. 

 Actually, I'm reading the URL now, but is there any other white paper that would go line-to-line description for the apache2.conf file. the problem is that I'm a newbie at Linux world.

Anyway you've provided a great deal of help, thanks :)

---

### Post by Vegan on 2009-11-26
On my site, in the forum, I have a piece on Apache and how to get it up with minimal fuss. See the LAMP area of Linux IT.

---

### Post by munky99999 on 2009-11-26
> **zennix said:**
> Thanks man, I appreciate your help. The file has been restored. 

 Actually, I'm reading the URL now, but is there any other white paper that would go line-to-line description for the apache2.conf file. the problem is that I'm a newbie at Linux world.

Anyway you've provided a great deal of help, thanks :)

[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

probably the closest. Personally I just google what I dont know. Gets you right to what you want. Sadly Programmers dont like to document.

---

