---
title: "Updating grub conf receiving error"
date: 2010-06-29
forum: Server Platforms
---

### Post by tnine on 2010-06-29
Hi all,
  I have 4 drives in my workstation.  I've created a raid 5 array on drives sdb-sdd.  sda was still Windows, which was randomly blitzing my grub configuration.  I've swapped my sda drive and my sdd drive.  As a result, my sda drive is not a raid drive, and my sdd drive is now windows 7.  I'm attempting to update my grub configuration, and it craps out every time with this error.


toddnine@greenlantern:/boot/grub$ sudo update-grub2 
Generating grub.cfg ...
/usr/sbin/grub-probe: error: unknown filesystem.


Any ideas why I'm getting this?  I'm on the latest 10.04 64 bit server with all the latest updates.

---

### Post by stlsaint on 2010-06-29
Not really sure in this situation but i think you still have grub reading a 5 raid setup but you removed the sdd drive. have you reconfigured your raid setup to show this swap?

---

### Post by tnine on 2010-06-30
Hey stlsaint,
  Yes, I had removed and re-added the drive to the raid array.  However, it had not finished rebuilding the array when I ran the command.  Now that the array rebuild is finished, the command worked fine.

Thanks for the help!

---

