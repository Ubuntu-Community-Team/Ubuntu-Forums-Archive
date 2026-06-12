---
title: "Trying to set up RAID + Encryption + LVM, but won't ask for pass and won't boot"
date: 2009-02-20
forum: Server Platforms
---

### Post by DinkyDogg on 2009-02-20
Hello,

I'm trying to set up Ubuntu 8.10 Server (amd64) on my machine. I've got a RAID 5 with 3x500gb drives. I've also got a drive that's not part of the array, with /boot.

I'm going through the text-based installer, and setting up each drive as a physical volume for RAID, then setting up the RAID volume as a physical volume for encryption, then setting up the encrypted volume as a physical volume for LVM, then setting up logical volumes for /, /home, and /var.

Everything goes okay in the install, but when I boot after that, it doesn't prompt me for a passphrase. It tells me that my RAID is degraded and is being rebuilt, then dumps me to a shell that says (initrmfs) or something similar.

Why won't it prompt me for the passphrase? What's wrong here? Is there's something I'm doing wrong?

Any ideas?

Thanks in advance.

---

### Post by DinkyDogg on 2009-02-21
Alright, after talking with "ikonia" on the Ubuntu irc channel, it sounds like I'm not the only one to have this problem. It appears that when booting, the ram disk that gets loaded doesn't support the encrypted file systems I set up. There's nothing about dm-crypt or luks or cryptsetup or anything else related in /etc.

So, any hope of this being fixed soon? Do I gotta wait for 9.04? Any other ideas?


Edit: Looks like this bug here - [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/21878](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/21878)

Edit 2: Actually, that bug is 2 years old. ikonia said he and another guy who was having the problem filed a new report yesterday, but I can't find it.

---

