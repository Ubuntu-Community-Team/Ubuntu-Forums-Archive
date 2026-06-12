---
title: "SFTP Log Monitor"
date: 2006-07-09
forum: Server Platforms
---

### Post by bbzbryce on 2006-07-09
I'm using SFTP to host a few files and would like to be able to quickly tell a few things without having to scroll through thousands of lines of log files.

I patched my openssh with sftplogging so all sftp logs to /var/logs/auth.log.

Does anyone know if there is a program that already does this, or even a simple script that can be modified to tell, current users, current files being transfered, and a various assortment of speeds, like total average speed, file average speed, and current speed which would be like the last 5 seconds.

Also if this hasn't already been done, would monitoring the log be the best way to accomplish this?  Or is there a device that should be monitored to get a more real result? I'm new to how linux logging works.

Thanks.

---

### Post by JustAboutRealJAR on 2007-12-07
I've been looking for something like that too. Anybody have an idea?

---

### Post by bone2006 on 2007-12-30
I've been looking for something as well
whowatch will monitor ssh activity, but not SFTP activity
If you guys have found something, please let me know.

---

