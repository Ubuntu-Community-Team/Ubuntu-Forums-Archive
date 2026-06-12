---
title: "Installing Ubuntu 10.04 Server on RAID 1"
date: 2011-03-04
forum: Server Platforms
---

### Post by thehouch on 2011-03-04
I am attempting to run Ubuntu 10.04 Server on RAID 1 and am consistently hitting the same issue when trying to boot the system for the first time (after what seems to be a successful install of the OS). I am creating the RAID 1 using the directions found in the Ubuntu Server Guide. The error I receive when trying to boot the system for the first time is...

```
mount: mounting /dev/disk/by-uuid/f35415ee-4c14-4eb1-995f-f19fbcd760c7 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

Any help in resolving this would be much appreciated. Also, any explanations as to why this happening and what I am doing wrong during the set up process would also be appreciated. Let me know if you need any additional information to help troubleshoot this issue.

---

### Post by thehouch on 2011-03-05
It turns out I had been doing everything correctly but ultimately was provided with bad install media. I ended up downloading a copy directly from ubuntu.com and it was roughly 7MB larger in size than what I had in hand and installed and booted without issue.

Carry on, nothing to see here...

---

### Post by rockycool13 on 2011-05-16
Hi ,
 I also have same problem .
  can u brief ur answer .

---

