---
title: "is it possible to  transfer files from a virtual os to system os"
date: 2009-04-11
forum: Virtualisation
---

### Post by fuser312 on 2009-04-11
i am running ubuntu 8.10 on my system and installed scientific linux using virtual box. now my question is can i transfer files from my ubuntu to scientific linux and vice versa.

---

### Post by jocampo on 2009-04-11
HI

I am not an expert but let me help you anyway (it seems people are lazy today, no one has helped me either on my own thread) ...

Well, usually you can configure some settings for the network devices (at software level, in the VIrtualBox console, for example) and you can select NAT. That will allow you to put both machines on same network. If both can see each other, you can use ftp, ssh or similar protocols, to move data back and forth.

---

### Post by bodhi.zazen on 2009-04-11
There are many many ways to do this. You can use a shared flash drive or any number of networking protocols including Samba, ssh (scp), NFS, http, ftp.

Virtualbox also comes with shared folders.

---

### Post by HermanAB on 2009-04-12
Howdy,

Install ssh-server on the host and then use nautilus (or konqueror) with sftp://user@1.2.3.4 over port 22/TCP.  You don't need to configure anything to get this to work - runs out of the box.

NFS is only slightly more work to get going.  You need to configure one line in /etc/exports on the host and one line in /etc/fstab on the guest.

---

### Post by meka4996 on 2009-05-07
try this
[http://ubuntuforums.org/showthread.php?p=7236471#post7236471](http://ubuntuforums.org/showthread.php?p=7236471#post7236471)

---

### Post by axel206 on 2009-05-09
Check this guide. You have to install virtualbox additions and enable shared folders.

[How to install Linux on Windows using VirtualBox](http://www.my-guides.net/en/content/view/112/26/)

---

