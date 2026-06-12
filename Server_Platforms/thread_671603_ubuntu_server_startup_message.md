---
title: "ubuntu server startup message"
date: 2008-01-18
forum: Server Platforms
---

### Post by bone2006 on 2008-01-18
The startup message each time I ssh into the server is starting to annoy me, is there a way to edit the script?

***********************************
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

***********************************

---

### Post by Vinno on 2008-01-18
Yeah. 

its mod of the day i think or issue

/etc/motd
/etc/issue
/etc/issue.net

Edit one of those. Just look inside for the right one.

---

### Post by Dr Small on 2008-01-19
The message that gets displayed at login, is /etc/issue
The message that you see after your login (above the prompt) is the motd.

Dr Small

---

### Post by bone2006 on 2008-01-19
/etc/motd did the job
Thanks guys

---

### Post by mlbarnes on 2008-03-05
I am having a problem when I edit the MOTD in the Ubuntu Server version 7.10 that every time I reboot it gets reset to the default. Is there a way to change that?

---

### Post by Ballena on 2008-03-14
I had the same problem with the custom messaged gor reset after system restart. Apparently the /etc/motd is a link to /var/run/motd. Maybe you should edit this file instead? Or delete te link in /etc/ and make a real file.

---

