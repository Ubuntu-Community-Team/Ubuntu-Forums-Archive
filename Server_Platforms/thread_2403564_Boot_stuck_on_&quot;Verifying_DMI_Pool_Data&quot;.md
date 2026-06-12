---
title: "Boot stuck on &quot;Verifying DMI Pool Data&quot;"
date: 2018-10-13
forum: Server Platforms
---

### Post by honeycombs_big_yahyahyah on 2018-10-13
Hi all,

I just upgraded my kernel via apt-get install, and now my system is stuck on "Verifying DMI Pool Data" when booting.  Any ideas how to debug this?

Other things that have recently changed are that I just replaced a drive in an md array.  However, I was able to reboot with that drive installed, I think, so I kinda doubt that's the issue.

Any help greatly appreciated...

Thanks,
Allie

Ubuntu Server 14.04

---

### Post by howefield on 2018-10-13
Thread moved to the "*Server Platforms*" forum.

---

### Post by honeycombs_big_yahyahyah on 2018-10-13
Seems that I didn’t initialize the new drive properly maybe?  Seems that core.img does exist on sda...  any thoughts on how to fix?

[http://paste.ubuntu.com/p/Qqg5T4dJDg](http://paste.ubuntu.com/p/Qqg5T4dJDg)

---

### Post by honeycombs_big_yahyahyah on 2018-10-18
anyone having a similar issue, i didn't run grub-install on the new drive after installing it, and because it's sda, i guess that was blocking the boot.  I had to boot off a usb, assemble my md array md0, which is where /boot is mounted, and mount md0 to /boot, and *then* run grub-install /dev/sda.  (maybe i had to do grub-install /dev/sda2, which is where my grubbios partition is, as they're GPT formatted...)

---

