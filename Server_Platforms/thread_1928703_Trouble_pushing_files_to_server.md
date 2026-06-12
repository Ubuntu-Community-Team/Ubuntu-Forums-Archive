---
title: "Trouble pushing files to server"
date: 2012-02-20
forum: Server Platforms
---

### Post by Tactical Fart on 2012-02-20
I've recently run into a problem when I try to push a file to my headless server. I don't know exactly what is going on but the server seems to 'okay' the transfer, but nothing will get pushed. (This applies to ftp, sftp, and samba). My other machine works just fine though (only tried sftp). The weird part is that I can ssh into it just fine, as well as run apt-get update, install, etc. It can fetch files, but not if it was solicited. I can also order it to copy files.

It was originally on ubuntu 10.x (forgot which one) because an upgrade to 11.x makes the screen appear weird. I tried to install 11.10 on top of what I had, but it didn't help anything and the problem(s) persists. When I tried to re-up the conf files for some of my deamons, I was able to push a conf with a length of 677 but not one with 5383. 

Note: iptables was used in the first install, but was not yet implemented in the second. The terminal that I use to control the two machine is the same. 

Any ideas?

---

### Post by jonobr on 2012-02-21
Hello

Normally when I read people can login via FTP but not push or pull data,
that is usually an indication that port 21 is open but port 20 is closed, given in your case that sftp in your case has the same problem, Im not so sure here, but no harm checking


I would run

```
sudo tcpdump -i any port 20
```
in a terminal

login with ftp and then see if the data session kicks off from the above tcpdump.

BTW- interesting name

---

