---
title: "Auto copy DVDs/CDs when inserted"
date: 2012-09-16
forum: Server Platforms
---

### Post by ads2996 on 2012-09-16
Hi,

I have a Ubuntu 10.04 server. It runs samba and mediatomb. I would like it to copy CDs/DVDs automatically when inserted. The n place them in a folder for streaming.

Thanks in Advance

---

### Post by kgatan on 2012-09-17
If you want something to happen when you insert a dvd/cd in Linux you need to write an udev rule.

I dont have an example but you can find instructions here, [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)
Look into the section on running programs on specific events.

You can use the program Handbrake to rip the dvds from command line and script.
Google it and you should find out what parameters to use.

---

