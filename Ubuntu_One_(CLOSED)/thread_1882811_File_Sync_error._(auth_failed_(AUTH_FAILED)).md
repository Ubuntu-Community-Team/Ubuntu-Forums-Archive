---
title: "File Sync error. (auth failed (AUTH_FAILED))"
date: 2011-11-18
forum: Ubuntu One (CLOSED)
---

### Post by baosheng on 2011-11-18
My Ubuntu One worked fine all the time until today. I saw the error "File Sync error. (auth failed (AUTH_FAILED))" on Ubuntu One Control Panel on my Ubuntu box. I googled around and tried all I can find. But they didn't work. I also have tried to remove the device from Ubuntu One web interface. It didn't work either. 

[IMG]http://p.twimg.com/Aegi4e7CMAE-GV9.png:large[/IMG]

Does anyone know how to fix this problem?

---

### Post by LonelyStar on 2011-11-21
In my case it helped to set the time on the ubuntu computer correctly.

---

### Post by duanedesign on 2011-11-24
Hi,
Could you please check this file ~/.cache/ubuntuone/log/syncdaemon-exceptions.log to see if it contains anything. You can easily check it with this command:

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log

```
You can post the output, if their is any. It may contain file names. if that makes you uncomfortable you can private message it to me.

Thanks,
Duane

---

### Post by baosheng on 2011-11-24
Sorry Duane, since I didn't get the reply back earlier, I have deleted the home directory of the username that had problem with Ubuntu One. So, i don't have that log file any more. 

> **duanedesign said:**
> Hi,
Could you please check this file ~/.cache/ubuntuone/log/syncdaemon-exceptions.log to see if it contains anything. You can easily check it with this command:

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log

```
You can post the output, if their is any. It may contain file names. if that makes you uncomfortable you can private message it to me.

Thanks,
Duane

---

### Post by darkspook on 2012-03-22
correcting the time works for me. thanks :D

---

