---
title: "ubuntu server"
date: 2009-08-18
forum: Server Platforms
---

### Post by GreenDance on 2009-08-18
i'm just wondering, really i don't need to keep a monitor plugged into my server do i?, i can manage my server remotely from SSH or something like that?

thanks

---

### Post by Cheesemill on 2009-08-18
Correct. None of my Ubuntu servers have a keyboard or monitor.

---

### Post by wojox on 2009-08-18
Same here. Headless.
Make sure you have openssh-server installed. If you didn't choose it when installing.
```
sudo apt-get install openssh-server
```
```
sudo apt-get install openssh-client
```

---

### Post by GreenDance on 2009-08-18
many thanks :)

---

### Post by volkswagner on 2009-08-18
check your BIOS allow boot without keyboard and mouse.  Some older systems may need a keyboard attached to eliminate boot alarm.

---

### Post by Iowan on 2009-08-18
I found a patch to get around that, but I doubt it works for all machines.
(hmmm, must be on the machine at work...)

---

