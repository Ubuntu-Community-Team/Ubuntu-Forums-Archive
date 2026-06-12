---
title: "vsftpd - how to check the current transfer ?"
date: 2010-05-05
forum: Server Platforms
---

### Post by marllowe on 2010-05-05
Hi,

Is there any way to check current transfer in vsftpd ?
I've found this:

```
watch ps -C vsftpd -o user,pid,stime,cmd
```but it show me only this:
USER       PID STIME CMD
ftp      10732 May05 vsftpd: XXXX.XXXX.XXXX.XXXX/ftp: RETR something.iso

[COLOR=#000000]Second question[/COLOR] is:
Is there any applet for gnome which change colour when somebody login to server ?

Regards,
Artur

---

### Post by MSPdwalt on 2011-04-20
Artur, have you had any luck with this?

---

