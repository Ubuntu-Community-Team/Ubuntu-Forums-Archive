---
title: "Simple file backup"
date: 2013-05-24
forum: Server Platforms
---

### Post by JohanDees on 2013-05-24
Hi guru's:  How can I do an simple automatic (cron) backup on my server (ubuntu server) to a usb for just a certain bunch of files ? 
 Preferably with automount of the stick, and autostart after reboot ? 
I like to add, that it should run daily, and overwrite the old file on the usb stick.

---

### Post by CharlesA on 2013-05-24
Rsync would work for that. You would just have to specify which files you want to copy.

---

### Post by JohanDees on 2013-05-25
Ill take a look in Rsync. Thanks

---

