---
title: "Dual booting with Truecrypt 6.3a chainloading Grub2"
date: 2010-01-04
forum: Security
---

### Post by mk4umha on 2010-01-04
I'm having problems getting TC to load grub2 1.97b4. When I hit ESC from the TC boot prompt, I get "no bootable partitions found".

I also booted into Ubuntu Live cd, mounted my LVM dm-crypted volume and tried to reinstall grub2 to my nonencrypted /boot under /dev/sda3 and TC still wont boot. Then I set the boot flag on /dev/sda3 and it still won't boot. Has any one encountered this problem using Ubuntu 9.10?

These are the commands I used to install grub2 to my /boot partition. Atleast that's what I think it did.
update-grub
grub-install /dev/sda3
grub-install --recheck /dev/sda3

---

### Post by Jive Turkey on 2010-01-04
I think you might need to unencrypt you boot partition to get things working agian.  Does the latest truecrypt offer a way to use an encrypted one?  If so, cool and good luck!

---

### Post by mk4umha on 2010-01-04
> **Jive Turkey said:**
> I think you might need to unencrypt you boot partition to get things working agian.  Does the latest truecrypt offer a way to use an encrypted one?  If so, cool and good luck!

my /boot isn't encrypted at all.

---

### Post by mk4umha on 2010-01-04
Hmmm, I guess I somehow hosed up my WinXP Encryption. After I set my /boot with the Bootflag under Gparted, I rebooted and typed in my TC password and it took me to grub and not windows XP!

**update**

I fixed it be putting the boot flag back to the encrypted partition where windows XP was and it booted up. So i somehow can't get ubuntu grub2 to boot up when i hit ESC from the TC loader.

---

