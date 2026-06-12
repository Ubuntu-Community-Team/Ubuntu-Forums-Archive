---
title: "vsftpd upload to trigger an bash script to zip file"
date: 2006-01-13
forum: Server Platforms
---

### Post by lionel_son on 2006-01-13
Hello,

I was wondering if there is a way to automatically zip uploaded file on a VSFTPD server. I haven't found a option to run a dedicated bash script or is there a way it can be done in apache when downloading the file via the web (on the fly)?

I would like to avoid running a crontab every minute just for that purpose...

thanks a lot for your help

lionel

---

### Post by Mr_Grieves on 2006-01-13
I've messed around with Apache and Vsftp abit but never laid eyes on a inbuilt functionality that does that. Sounds like a job for some external software or.. a script via cron.

---

### Post by shinepuppy on 2008-03-21
Greetings,
I require the same event-driven functionality. My search led me to pure-ftpd which has a pure-uploadscript feature that allows you to execute an external script after a successful upload:
[http://blog.derjohn.de/space/start/2006-11-14/1](http://blog.derjohn.de/space/start/2006-11-14/1)

Hopefully this will help others as well.

---

