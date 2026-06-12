---
title: "Convert installation to read only file system"
date: 2008-09-03
forum: Server Platforms
---

### Post by Moepi on 2008-09-03
Hello,
I have a running Ubuntu Desktop system installed on the local hard drive which should be modified in a way, that the file system is read-only. Well, actually not really read-only, but the changes must not be written to disk. In effect each LiveCD offers exact the mechanism needed.
The systems are booted from the local hard drive, users may change anything on the system but theses changes should be gone as soon as the system is rebooted again.

Does anyone have tips on how to realize such an environment?


Many thanks in advance!

---

### Post by Archmage on 2008-09-03
Maybe I'm totaly stupid, but wouldn't mounting everything (beside the swap-partition) in read only have this effect?

I would do this in the /etc/fstab), but I'm sure that there might be a better way.

BTW: 8.10 sould have a guess-account for this purpose.

---

### Post by cdenley on 2008-09-03
> **Moepi said:**
> Hello,
I have a running Ubuntu Desktop system installed on the local hard drive which should be modified in a way, that the file system is read-only. Well, actually not really read-only, but the changes must not be written to disk. In effect each LiveCD offers exact the mechanism needed.
The systems are booted from the local hard drive, users may change anything on the system but theses changes should be gone as soon as the system is rebooted again.

Does anyone have tips on how to realize such an environment?


Many thanks in advance!

I wouldn't recommend making the whole system read-only. You should be able to install security updates easily. Why not just mount /home with tmpfs, then configure pam to create their home directories automatically. Then you can create some regular home directories for your admin users if you want, and admin users will be able to install updates or new software. Normal users shouldn't be able to modify anything outside their home directory, anyway.

> 
Maybe I'm totaly stupid, but wouldn't mounting everything (beside the swap-partition) in read only have this effect?

I don't think gnome would work properly, along with a bunch of other things.

---

### Post by Moepi on 2008-09-03
It is mandatory that users can achieve root privileges. They should also be able to modify anything they want - but these changes must not be written to disk. This is the point.

---

### Post by cdenley on 2008-09-03
> **Moepi said:**
> It is mandatory that users can achieve root privileges. They should also be able to modify anything they want - but these changes must not be written to disk. This is the point.

I tried this before, then decided my alternative was a better solution for me. However, this time around, I found a very useful thread.
[http://ubuntuforums.org/showthread.php?p=5422268](http://ubuntuforums.org/showthread.php?p=5422268)
It all seems to work on hardy, except...
/etc/initramfs-tools/scripts/modules
...should be...
/etc/initramfs-tools/modules
...for step 2.

---

