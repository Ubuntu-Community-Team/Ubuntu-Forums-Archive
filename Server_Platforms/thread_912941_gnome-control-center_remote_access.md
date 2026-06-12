---
title: "gnome-control-center remote access"
date: 2008-09-07
forum: Server Platforms
---

### Post by tsmets on 2008-09-07
On my Ubuntu server I can use the gnome-control-center remotely but some functions are disabled. I created users but they seem disabled ...

Any idea how I can enable those functionalities so I could activate those users (without) having to physically access the server.

\T,

---

### Post by lazyart on 2008-09-07
perhaps webmin is what you want?

---

### Post by tsmets on 2008-09-08
Yes ....
but I would preferably avoid installing more software... 
I don't remember where but I think I can authorize the remote access of those features 

\T,

---

### Post by rick71 on 2008-09-09
I am using NX Server on my server. I can not edit or create new users or groups remotely. I think this is a Gnome setting. You should be able to create/edit users by remote ssh terminal.

How did you access gnome-control-center remotely?

---

### Post by tsmets on 2008-09-10
X over SSH :)

Here is a transcript of what I do

```

tsmets@ubuntu:~$ !ss
ssh -X  tsmets@192.168.5.201
tsmets@192.168.5.201's password: 
Linux redfern 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Mon Sep  8 22:18:42 2008 from 192.168.2.41

tsmets@redfern:~$ sudo gnome-control-center 
[sudo] password for tsmets: 

```

\T,

---

### Post by rick71 on 2009-02-07
Sorry for the lonf duration...

The problem is indeed an Gnome thing. Gnome will only let you access certain administrative utilities locally. apparently it is a bug that was fixed, and then reappeared. You can use Webmin to administer users.

---

