---
title: "I hate my brother! Please help. Forgotten password."
date: 2008-03-22
forum: Security Discussions
---

### Post by Starcrazee on 2008-03-22
Hi,
My stupid little brother has "accidentally" changed the password on my computer and forgotten what he changed it to. :mad:

Is there **any** way that I can log on without using a password?
If not I am going to kill him.

---

### Post by mikewhatever on 2008-03-22
There is a way to reset the forgotten password, look here [https://help.ubuntu.com/community/LostPassword?highlight=%28password%29](https://help.ubuntu.com/community/LostPassword?highlight=%28password%29).

---

### Post by Dr Small on 2008-03-22
Log into recovery mode from GRUB and then type:
```
passwd *user*
```

Dr Small

---

### Post by netlogic on 2008-03-24
1. if he hasn't password protected his grub, just add "single" to the kernel line. you will logon with a single user mode and change the password.

2. no bios password, boot off a live and chroot and change password.

3. bios password on a workstation, remove the cell battery inside or reset the bios by using a jumper switch, so the bios goes back to default and boot to CD-ROM.

---

