---
title: "LVM on 2 disks out of 3, possible?"
date: 2009-08-24
forum: Server Platforms
---

### Post by gmalac on 2009-08-24
Hi,
My server has three HDD, sda 300GB with system and home dir, sdb and sdc 500GB each used for data and backup. All drives are formatted ext3
I would like to combine both sdb and sdc into one "data" volume (found other solution for backup, using external usb drive).
Is this possible? if Yes! how?
Thanks for any help
Guy

Server running ubuntu 8.10

---

### Post by Bachstelze on 2009-08-24
It is possible using RAID or LVM (or both), but keep in mind that you will lose all your data in the process.

---

### Post by gmalac on 2009-08-25
Thank you for that and it is OK to lose the data for I have a backup. 
Now how do I do this with LVM please? Is there a command, a program, a script?
Just to point me to a link would already be great.
Thanks
Guy

---

### Post by Bachstelze on 2009-08-25
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

