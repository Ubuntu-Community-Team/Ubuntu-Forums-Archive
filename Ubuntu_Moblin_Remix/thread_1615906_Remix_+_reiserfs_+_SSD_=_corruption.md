---
title: "Remix + reiserfs + SSD = corruption"
date: 2010-11-07
forum: Ubuntu Moblin Remix
---

### Post by hr2600hz on 2010-11-07
Hi!
 

 I'm experiencing a problem with remix and reiserfs.
 I've installed Remix 10.04 on my Acer Aspire One ZG5 (16GB SSD) and made two
partitions (sda1 - reiserfs, sda2 - swap). It worked well until system update. After
update and system restart SSD went corrupted and no boot, kernel panic, and so on.
Have try to mount with sysrescue distro and nothing, disk is fully corrupted.
 

 Ok, after reinstall and putting ext4fs everything was working ok.
 

 So, time passed and now I've decided to install 10.10 just to see new UI.
 

 Have formated sda1 again with reiserfs (i just like this fs), and the problem is still
here, reiserfs gets corrupted after system update.
 

 With 9.04 I didn't experience problems with reiserfs so I don't think my SSD is  broken.

---

