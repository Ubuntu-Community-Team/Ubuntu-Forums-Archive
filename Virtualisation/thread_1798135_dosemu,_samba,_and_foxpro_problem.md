---
title: "dosemu, samba, and foxpro problem"
date: 2011-07-05
forum: Virtualisation
---

### Post by vaizero on 2011-07-05
Dear all,

I have database foxpro 2.6 in windows 2003 server. I want my ubuntu  client connect to windows server and run foxpro, I am using ubuntu 10.04. I have install dosemu,  and already mount using samba to the foxpro directory at server 2003 using this command in terminal:

sudo mount -t smbfs //[192.168.0.11/foxpro]("http://192.168.0.11/foxpro") /mnt/foxpro -o username=user,password=password

//[192.168.0.11/foxpro]("http://192.168.0.11/foxpro") is my windows 2003 server. and then
 /mnt/foxpro is my ubuntu directory.

at dosemu config file, i use lredir command to mount  /mnt/foxpro as drive d: with this syntax

lredir d: linux\fs/mnt/foxpro

at dosemu...when i change to drive d, all database is listed, but when  run foxpro.exe, the error message is "File 'D:foxpro.exe' does not exist"

but if I copy all foxpro database to my local ubuntu, foxpro is running well.
anybody can help me...thank you very much.

---

### Post by Humanity to others on 2012-01-31
d:\ drive assigned for home directory use other drive letter like g:\ p:\ etc

---

