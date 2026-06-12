---
title: "ftp server dies on start up"
date: 2006-10-07
forum: Server Platforms
---

### Post by water on 2006-10-07
I've installed an ftp server following this guide : [https://help.ubuntu.com/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/ubuntu/serverguide/C/ftp-server.html) and everything worked perfectly for a short while (30 - 60 minuttes).

Then suddenly it just died, and if try tp start it with > sudo /etc/init.d/vsftpd start it reports back with OK but seems to die imediatly.

the log ( /var/log/vsftpd.log ) only show entries from the short period ther server was running : 

> Fri Oct  6 15:37:55 2006 [pid 4448] CONNECT: Client "10.10.10.185"
Fri Oct  6 15:39:13 2006 [pid 4463] CONNECT: Client "10.10.10.185"
Fri Oct  6 15:39:17 2006 [pid 4465] CONNECT: Client "10.10.10.185"
Fri Oct  6 15:40:58 2006 [pid 4493] CONNECT: Client "10.10.10.185"
Fri Oct  6 15:40:58 2006 [pid 4492] [slimserver] OK LOGIN: Client "10.10.10.185"

I've tried reinstalling but that does solve the issue.

Any suggestions?

:water

---

