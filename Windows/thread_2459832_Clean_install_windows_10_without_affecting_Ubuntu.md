---
title: "Clean install windows 10 without affecting Ubuntu"
date: 2021-03-27
forum: Windows
---

### Post by abinav-shankar on 2021-03-27
Hi,

I have Windows 10 and Ubuntu 20.10 installed on two separate hard disks. There are problems with my Windows 10 and refreshing or resetting solves the problem only temporarily (The issues come back after two or three restarts or logins). I am planning to clean install Windows 10 from USB. I have all my personal files in ubuntu. Will clean installing W10 affect my Ubuntu files? Is it safe to proceed without any additional setups?

Thanks.

---

### Post by mikewhatever on 2021-03-27
It is easy to make a mistake while installing an OS, for example, format or delete a wrong partition, overwrite files, etc. To be on the safe side, it is always advised to keep a backup of all important files on a separate storage device.

Now, a clean install of W10 should not affect Ubuntu files, if you do everything right. Are you sure of yourself?

---

### Post by yancek on 2021-03-27
Do you have backups?  Have you done this before?  Are your current installs of windows 10 and Ubuntu both UEFI or both Legacy?  If you have Ubuntu and windows on separate drives, likely it would be best to disconnect the Ubuntu drive while installing windows 10.  Remember to install both in the same mode, both UEFI or both Legacy.

---

### Post by oldfred on 2021-03-27
If UEFI, Ubuntu may have boot files in ESP on Windows drive?

If BIOS, Windows does not see Linux partitions. In some cases if default BIOS boot drive is Ubuntu drive, Windows will put its 100MB boot partition on the Linux drive, destroying first 100MB of drive.

And you even though separate drives, you need to install in same boot mode, both need to be UEFI or both BIOS. How you boot install media, UEFI or BIOS for both Windows & Ubuntu is how it installs or repairs. Always be in correct boot mode.

Best to have good backups, and both Ubuntu live installer in case you need repairs & Windows installer or repair/recovery disk for repairs in future also.

I like to document system with either Boot-Repair's summary report or terminal based bootinfoscript. Also helps then to know how system is booting and what is installed where:
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

