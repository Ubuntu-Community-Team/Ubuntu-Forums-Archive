---
title: "cups cong file"
date: 2010-02-15
forum: Server Platforms
---

### Post by rdema19403 on 2010-02-15
i have ubuntu 9.10 server when i ssh into it i wanted to know what the command is to get into the  /etc/cups/cupsd.conf file?
I thought it was $ sudo  /etc/cups/cupsd.conf 
but that does not seem to work and after you change the file what is the command to save it?
Thanks

---

### Post by gordintoronto on 2010-02-15
You need to specify a program before the file name, for example, nano.  the command becomes:
sudo nano /etc/cups/cupsd.conf 

In nano, Ctrl-O writes the file, Ctrl-X exits.

---

