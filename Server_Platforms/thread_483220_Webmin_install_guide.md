---
title: "Webmin install guide?"
date: 2007-06-24
forum: Server Platforms
---

### Post by Catsworth on 2007-06-24
Hey Guys,

Last time I built my server I installed Ubuntu Server 6.10, with Webmin for graphical management, using an installation guide I'd found somewhere on the web.  The problem is that I haven't got a clue where I found it, and I can't remember what I had to do to get it running ok.

Can anybody point me at a good installation guide for installing Ubuntu Server with Webmin?

Thanks.

---

### Post by bmathis on 2007-06-24
its really simple

go to webmin.com and download the deb file, in a terminal type the following in```
sudo dpkg --install webmin.xxx.deb
``` once that is complete you should be able to connect to it using the ip address of the machine and port 10000, it should look like 192.168.1.100:10000.

If for some reason you might not be able to reach it, try installing apache2

---

### Post by jdbg on 2007-06-26
will it work for upgrading?

---

### Post by Aberrix on 2007-06-26
```
sudo apt-get install webmin
```

works as well.

---

### Post by jdbg on 2007-06-26
yes, thanks - i upgraded to 1.350 ;)

---

