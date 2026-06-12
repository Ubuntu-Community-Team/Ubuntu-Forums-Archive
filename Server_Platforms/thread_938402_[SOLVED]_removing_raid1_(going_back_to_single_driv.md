---
title: "[SOLVED] removing raid1 (going back to single drive)"
date: 2008-10-04
forum: Server Platforms
---

### Post by govee on 2008-10-04
I searched and followed all the instructionsI could find but I am still having a problem at boot. Boot fails but gives me a prompt and allows me to press control+D and it boots, but only if I have doth drives installed.

My system has the OS on its own drive as the ide master. The raid is /dev/md0 which has SDb1 and SDc1. I went thru the process of unmounting the md0 and deleting the superblocks. I then modified the fstab to comment out the the mounting of MD0 and mounting the SDA1.

If I remove the SDb or c and reboot the failure happens. What else do I need to do?

thanks,
by the way all data fromthe raid is backed up.I justwant to keep the server running without reloadiing the OS.

---

### Post by govee on 2008-10-05
Nothing I did seemed to help. 
I fixed the flag that identified the data drive as raid 
I used parted to check for errors. 
I tried to change GRUB.....
 Then I noticed that my /dev/sda1 sdb1 keep switching at boot. I would look at fdisk and it would show sda1 as data drive and sdb1 as os drive, but in my fstab my os drive is not listed by /dev/####. It is listed by uuid. my data drive was using /dev/####. I got the uuid for the data drive and used it in the fstab. I rebooted and got a drive error on one of the drives. I ran fsck -y and it fixed it, rebooted and all booted fine. I have rechecked with additional reboots and I now boot with no errors.

---

