---
title: "Upgrades from 6.10 to 7.10 to 8.04.2 issues (uuid/hda/sda)"
date: 2009-04-20
forum: Server Platforms
---

### Post by helfire on 2009-04-20
Hi all,

First my latest upgrade from 7.10 to 8.04.2 resulted in my swap partition not being mounted. this was due to /etc/fstab referring to it as /dev/hda2 though it is now identified as /dev/sda2. (i updated /etc/fstab accordingly)

In my /etc/fstab / and boot are still referred to hda1 and hda3. (though these devices dont exist in /dev/, so i'm surprised the server booted)

I also do not have the hal package installed and am hesitant to install it because I do not know how it'll handle updating my /etc/fstab

How should I go about updating my fstab to use uuid's? /dev/sda2's uuid is not listed in /dev/disk/by-uuid/ (but sda1 and sda3's are)

I do not have physical access to this server and reboot support costs and arm and a leg. Any help is appreciated :)

Thanks,

---

