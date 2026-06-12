---
title: "server boot problem"
date: 2010-01-04
forum: Server Platforms
---

### Post by redmansk8 on 2010-01-04
Hello everyone, I have loaded server 9.10 on an old IBM server I have. It has a SCSI hard drive it installed fine just when it boots it stops drops into to a shell and states it gave up looking for root. You can wait for a few seconds and then type exit and it will then boot fine. I have read I can go in and enter rootdelay=10 or some amount of time and it will boot like normal. Its not a problem walking over and typing exit when it boots but it would be so much easier to get it to boot normal. Once I got it booted I found the setting which is in /proc/cmdline so I tried to add rootdelay to it by using the command sudo echo "rootdelay=10" >> /proc/cmdline but it said permisson denied. Is there another way to add the rootdelay command?

---

### Post by cdenley on 2010-01-04
You want to set that as a kernel option in grub. The /proc/cmdline file isn't used to set kernel options, but only shows which kernel options were used. I haven't used the new grub yet, so I'm not going to try walking you through it.

---

### Post by redmansk8 on 2010-01-04
Thanks for your info I'll have to do some reading on grub settings.

---

### Post by llawwehttam on 2010-01-04
Grub2 is a bit of a nightmare to change.
Some people I know started booting Grub-legacy then chainloading to grub2 so they could get their old options back as if you use ext4 i believe grub legacy will have problems.

---

### Post by llawwehttam on 2010-01-04
Just found this and thought it might be helpful. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

