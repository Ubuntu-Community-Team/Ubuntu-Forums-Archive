---
title: "file system check fail"
date: 2010-04-27
forum: Server Platforms
---

### Post by piyhawat on 2010-04-27
when I run ubuntu server 

--------------------------------------------------------------------------------------------------------
mountall start/starting
fsck from util-linux-ng- 2.16
swapon:/dev/mapper/SDserver-swap_1:swapon failed : Device or resource busy
mountall : swapon /dev/mapper/SDserver-swap_1[10198] terminated with status 255
mountall : problem activating swap : /dev/mapper/SDserver-swap_1
/dev/sda5/ : Superblock last mount time (Fri Apr 23 12:13:29 2010, now = Fri Dec 7 22:25:25 2001) is in the future
/dev/sda5/ : UNEXPECTED INCONSISTENCY ; RUN fsck MANUALLY
(i.e., without  -a or -p options)
mountall : fsck/boot[10197]terminated with status 4
mountall : Filesystem has errors : /boot 
init : mountall main process (10196) terminated with status 2
File system check failed
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@SDserver:`
-------------------------------------------------------------------------------------------------------

what does it mean. And how I will solv it .

---

### Post by Bachstelze on 2010-04-27
Boot from a Live CD and run a fsck manually, like

```
fsck /Dev/sda5
```

---

### Post by Phulerock on 2010-04-27
I thinks you need to boot to revocery mod or use livecd to check your hdd. When the OS loaded, some partition and files are protected by OS.

do with Bachstelze's suggestion.

---

### Post by piyhawat on 2010-04-28
> **Bachstelze said:**
> Boot from a Live CD and run a fsck manually, like

```
fsck /Dev/sda5
```


I did that but problem not solved --"

---

### Post by Drenriza on 2010-04-28
boot from a live cd.
open a terminal.
 
run
```
fsck -fa /dev/"device"
```
then run
```
badblocks -n /dev/"device"
```
 
substitude the word "device" with your device name.
for example
```
fsck -fa /dev/sda1
```

---

### Post by viralmeme on 2010-04-28
> **piyhawat said:**
> when I run ubuntu server .. File system check failed .. what does it mean. And how I will solv it .
It means that the system didn't shutdown properly the last time and the file system is in an inconsistant state. To protect files it will only reboot in a readonly mode. You need to do the fsck thing as described.

---

