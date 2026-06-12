---
title: "How do I issue server commands from a desktop"
date: 2009-03-28
forum: Server Platforms
---

### Post by itsols on 2009-03-28
Hello everyone, I've installed the Ubuntu 8.04 Server on a PC. In order to save room/desk space and power consumption, I'd like to to use it without a screen and other peripherals.

I also have a dual-boot laptop (Ubuntu desktop 7.10 and Windows XP) on the network.

I want to know if it is possible to issue ALL of the server commands using my LAPTOP. I mean all commands like listing files, copying, ftp, software setup, hardware setup, etc.

An example of listing files with either find or ls would be and ideal start.

Thank you very much for your time.

---

### Post by m3bik on 2009-03-28
I use [PuTTY]("http://www.putty.org/") on my laptop to connect to my server through SSH.

You can issue all your commands this way.

---

### Post by MrWES on 2009-03-28
> **itsols said:**
> Hello everyone, I've installed the Ubuntu 8.04 Server on a PC. In order to save room/desk space and power consumption, I'd like to to use it without a screen and other peripherals.

I also have a dual-boot laptop (Ubuntu desktop 7.10 and Windows XP) on the network.

I want to know if it is possible to issue ALL of the server commands using my LAPTOP. I mean all commands like listing files, copying, ftp, software setup, hardware setup, etc.

An example of listing files with either find or ls would be and ideal start.


Thank you very much for your time.

You can use ssh to remotely login to your server. Here is a good HOWTO on setting that up.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4")

Bill

---

### Post by MrWES on 2009-03-28
> **m3bik said:**
> I use [PuTTY]("http://www.putty.org/") on my laptop to connect to my server through SSH.

You can issue all your commands this way.

PuTTY works well if you want to connect from your Windows machine. You can also use WinSCP to transfer/manage files.

Bill

---

### Post by MrWES on 2009-03-28
OT: I love Lion Stout from Sri Lanka!

---

### Post by itsols on 2009-03-28
Hello everyone!

This is one of the fastest responses I got.

Thank you VERY MUCH for this info.

PS: You guys are welcome to Sri Lanka and I'd love to show you around from the beaches to the mountains 3000 ft above sea-level. But I can't help with the LION thing - lol...

Thanks again.

---

### Post by hyper_ch on 2009-03-28
if you want to transfer file get [http://www.winscp.com](http://www.winscp.com) --> just enter your username,password and the ip of your server and it connects over a secured line to it in a 2-pane ftp window. Very simple.

---

