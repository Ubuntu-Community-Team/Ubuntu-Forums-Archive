---
title: "When you open my laptop"
date: 2008-07-12
forum: Security
---

### Post by pawnrocket on 2008-07-12
Hi everyone,

I was thinking today that I would like to log (or see existing logs) when my laptop lid is opened. Is there a way in place or a general direction I can research that would make this possible? 

Thanks 

Ubuntu 8.04 2.6.24-19 Toshiba Satellite L355

---

### Post by Tod Merley on 2008-07-13
> **pawnrocket said:**
> Hi everyone,

I was thinking today that I would like to log (or see existing logs) when my laptop lid is opened. Is there a way in place or a general direction I can research that would make this possible? 

Thanks 

Ubuntu 8.04 2.6.24-19 Toshiba Satellite L355

Hi Ponrocket!

My laptop is off for the night, but I do know that many events are logged in /var/log (various files there - such as "messages").  Many may be used when the laptop is opened.

I have run into "suspend.log" mentioned several times as I googled such things as "linux suspend logging".  Perhaps you could do a "sudo updatedb" (which creates a new database of all files on your disks (well most of them anyway - configuration matters)) and then a "locate suspend.log" or simply "locate suspend" to see any related files on your disks.

Good Hunting!

Tod

---

### Post by cinelerrafan on 2008-07-13
Hi Pawnrocket,

on my laptop gnome locks the screen when I close it. When you open it up and type in your password it will log it in /var/log/auth.log

hope this helps,
cinelerrafan

P.S. this of course doesn't log when you open the laptop but don't log in.

---

