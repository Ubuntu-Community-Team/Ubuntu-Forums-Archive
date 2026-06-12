---
title: "Mounted, but yet Invisible &amp; Only Root Can Unmount.. ? i"
date: 2011-01-31
forum: Ubuntu Studio
---

### Post by Wejdan on 2011-01-31
Hi,

I have this partiotion "dev/sda6" (format ext4) that I kept aside to keep my documents visible for both, Ubuntu Studio & windows
But, since it's in Ext4 format, it's not visible on windows. It's actually not visible in ubuntu too even though it's mounted in "home" folder

I've seen couple of posts here and there, tried the following:

1) Gave myself all the permissions available in "users and accounts"

2) unmount using "Disk Utility", I received the following:
> umount: only root can unmount
UUID=7ea5fe16-63d0-47e2-8aa0-f4a28dd1f41d from /home3) Format, Delete the partition:  I got:
> /dev/sda6 is mounted4) Unmount the partition using Terminal"  [PHP]sudo umount /dev/sda6[/PHP], [PHP]sudo umount /dev/sda6 /home[/PHP]I got:
[PHP]umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
[/PHP]5) ran this command (I don't really know what it's supposed to do)
[PHP]sudo chmod -R 777/home/dev/sda6[/PHP]and I got:
[PHP]chmod: missing operand after `777/home/dev/sda6'
Try `chmod --help' for more information.
[/PHP]

p.s. what doesn't mean that I have to be root?
I'm the only user "account" using the computer?

thanks,..

---

### Post by Morbius1 on 2011-01-31
> It's actually not visible in ubuntu too even though it's mounted in "home" folderPlease post the output of the followinfg commands so we can see how it's mounted:
```
cat /etc/fstab
```BTW,
> sudo umount /dev/sda6 The syntax for a umount is: **sudo umount *path-to-mountpoint***

What you are doing is trying to umount a device. You can't umount a device only a mount point.

---

### Post by Wejdan on 2011-01-31
thnx.. 
I ruined it all, logged into windows, deleted the partition,
and then Ubuntu-Studio couldn't start my home folder! 
so, I reinstalled ..

but thx again for trying to help

---

