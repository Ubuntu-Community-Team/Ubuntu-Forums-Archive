---
title: "Help! Can anyone tell me how to setup a file server for my local network?"
date: 2010-08-15
forum: Server Platforms
---

### Post by dongk on 2010-08-15
Hello,

I'm trying to setup a NAS for my network, the only problem is that I  can't figure out how to do it.  On my network I have about 3 computers  however only I only use 2 of them so I thought that maybe I could use  the third computer in such a way that I could access it 24/7 from the  internet as a server for all of my files (school papers, music etc  etc...). The only problem is that I don't know where to get started.  Both of the computers I'm currently using are Windows and the one that  I,hopefully, can turn into a server is running on Ubuntu. So, any advice  or tutorials that someone can point me towards?

Thanks in advance

---

### Post by cj.surrusco on 2010-08-15
I would recommend setting up a FTP server using vsftpd. There is a basic tutorial to get it set up [here]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html").

---

### Post by wojox on 2010-08-15
Have you looked here [Network File System (NFS)]("https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html")

---

### Post by Iowan on 2010-08-16
It's been awhile since I tried it - but have you considered something like [FreeNAS]("http://sourceforge.net/projects/freenas/")?

The [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") is another good place for ideas.

---

### Post by beetlejuice321 on 2010-08-17
dongk.  

**Try EBox Server (Based on Ubuntu)**
[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

Its installs a pre-configured Ubuntu server that is completely managed both at the server and remotely using only a web-browser. You can setup shared folders (directories) and access restrictions (based on Samba).  You can also configure any other options you want commonly used with Linux such such as SSH, DHCP, DNS, FTP, etc.  

It is aimed at a small businesses but should work well for your needs and allow you to have additional features as well.

---

