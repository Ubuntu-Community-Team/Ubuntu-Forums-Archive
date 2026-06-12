---
title: "ProFTP / Windows Share"
date: 2009-09-09
forum: Server Platforms
---

### Post by kgatan on 2009-09-09
Hi,
 
Im trying to get a mounted windows share to be accessible from ProFTP.
I have mounter the share in the ftp folder and can access it through any ftp client.
But when i download a file in the share i just recive an empty file. The mount works perfectly in linux and all files are working.
 
Mount:
mount -t cifs //ip/share /target -o ro,iocharset=utf8,username=user,password=psw
 
Ftp config is default, proftpd.
 
It probably sound like a stupid idee to start with but after trying the ftp on the windows machine which broke some features in exchange for some strange reason i have given up on the windows machine.
 
Any help or suggestions are greatly appreciated!
 
Ubuntu 9.04

---

### Post by hal10000 on 2009-09-09
> mount -t cifs //ip/share /target -o **ro**,iocharset=utf8,username=user,password=psw
you have mounted it ro (read-only). the correct command may be: [COLOR="Red"]mount -t cifs //ip/share /target -o **rw**,iocharset=utf8,username=user,password=psw[/COLOR].

you can try to remount it with [COLOR="Red"]mount /target -o remount,rw[/COLOR]

---

### Post by kgatan on 2009-09-09
Thanks for your reply.
 
The folder is supposed to be read only since the purpose of this connection is to share a large folder on the windows server machine through linux.
 
I tried your mount but the result was the same. It is when i download files from the ftp that all i get is empty files.

---

### Post by kgatan on 2009-09-09
I gave up on the ftp sollution since it was a pictures library.
went with a web server instead and [www.phpalbum.net](www.phpalbum.net).

Worked like a charm to mount the windows share in the picture library for phpalbum.:KS

---

