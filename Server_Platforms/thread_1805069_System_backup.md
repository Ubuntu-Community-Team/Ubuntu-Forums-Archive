---
title: "System backup"
date: 2011-07-15
forum: Server Platforms
---

### Post by TheMatej on 2011-07-15
I took a look through the forum and I didn't really find answer i was looking for, so i decided to post it.
I am running up-to-date Linux Ubuntu Server 10.04.2 LTS which disk will be replaced due to size, speed and age. I don't want to set everithing up again, if I don't have to. So, i thought about copying everything with *dd* command.

Note: In both options */dev/sda* is old drive and */dev/sdb* new one

**Option A:** Run the command from Live CD when the system is off
```
# dd if=/dev/sda of=/dev/sdb bs=4096
```**Option B:** Run the command when the system is running [SIZE=1](I personally don't like system to be up but it would be better if it could be)[/SIZE]
```
# init 1
# dd if=/dev/sda of=/dev/sdb bs=4096
```So, I tryed both options on virtual machin and they worked.

[LIST]
[*]Can i rely on them or is there any other [SIZE=1](better)[/SIZE] option?
[*]Can I use option B insted of option A or is there any difference?
[*]Can someone explain if I have to run it in single user mode and why?
[/LIST]
Sincerely,
Matej (a.k.a. MK)

---

### Post by ian dobson on 2011-07-15
Hi,

I would recommend booting from a liveCD, so that your filesystems aren't mounted when your copying them. Even if you drop into single user mode, some processes are still active in the background (syslog for example) and they could write to the fs. This could case corruption.

Regards
Ian Dobson

---

### Post by TheMatej on 2011-07-15
yeah,

i'm thinking same way, but i didn't know, writing could cause corruption. Thank you.
So, if i understood your answer correct, dropping into single user mode is recommended only for lowering writting on hd?

Thank you,
MK

---

### Post by ian dobson on 2011-07-16
Hi,

Single user mode is just that, only you are logged on. So you can perform major changes/reboot the box without interfering with anyone else.

using dd in single user mode could cause corruption on the drive your writing to, not the one your reading from. Think of it like this, dd starts copying the drive, and copies part of the directory structure, by the time it get to actually copying the files pointed to by the directory structure something has written to the files and they are now larger. But the directory structure dd copied doesn't contain information about the extra data, there's your corruption.

I always just use a boot USB stick with a minimal linux when I need to do major modifications to a server.

Regards
Ian Dobson

---

### Post by TheMatej on 2011-07-16
a'ight, thanks for explanation.

How sexy, i turned server off, booted arch linux, copyed */dev/sda* to */dev/sdb*, deleted *swap* partition */dev/sdb3*, resized */dev/sdb2*, remade *swap*, turned it off, remove master hard drive, changed jumper on new one to master and turned it on... that's it :) - like it

Thanks again,
MK

---

