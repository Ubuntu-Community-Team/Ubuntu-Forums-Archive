---
title: "Very basic ad hoc ftp server?..."
date: 2005-10-23
forum: Server Platforms
---

### Post by raggamuffin on 2005-10-23
I have two computers that share an internet connection through a router that I often transfer files between...both are now Kubuntu 5.10...

until a couple days ago, one of them was running XP, but I got fed up with windows, period, and installed Kubuntu on it too...

before the OS switch, I would run [ftpdmin](http://www.sentex.net/~mwandel/ftpdmin/) on the windows box, and connect to 192.168.1.100 in gFTP in order to transfer files between them...

now that both boxes are linux, I can't seem to find an decent equivilent/replacement program for ftpdmin...

could somebody give me info/suggestions on setting up a very basic and simple ftp connection between the two computers in order to transfer some files from one to the other?...

thanks in advance...

---

### Post by Beggar on 2005-10-23
Honestly, I dont think you want to run an FTP server, since you already have gftp installed I would recommend an ssh server as its most likely more secure. You can even use gftp to connect to it using the 'ssh2' connection option.  As for an ssh server, I would recommend openssh-server, a simple *sudo apt-get install openssh-server*, and your all set. Oh, and congratulations on getting rid of Windows, we are all very proud.

---

### Post by raggamuffin on 2005-10-23
[QUOTE=Beggar]...[/QUOTE]

Great...exactly what I needed to know...thanks a lot...

---

