---
title: "Would not show contents of USB drive even it is mounted (not encrypted)"
date: 2018-06-10
forum: Ubuntu/Debian BASED
---

### Post by nk59 on 2018-06-10
I want to share one USB stick between few computers and/or users. Once formatted as ext4 drive it will be functional on another computer with the same user name (the same as computer on which it was formatted) and will mount but with message "The folder contents could not be displayed" for another user. This happens on Ubuntu 16.04 (Robolinux v.9.2) and Debian Jessie 8.10 also, the same story with couple of other USB sticks formatted in the same way. Attempt to change permissions with command:  sudo chown 777 /media/sdb1        (or sdb, disk name, user name?) show that no such file. Just stuck with it, please help.  Nick

---

### Post by ajgreeny on 2018-06-10
Once formatted as ext4, but what is it now?

Is it now NTFS and either improperly removed from Windows meaning it is still in use as far as Linux is concerned, or do you use it in Windows where fast-start is enabled meaning that even when you shutdown Windows the USB is still in a mounted condition?

---

### Post by yancek on 2018-06-10
The chown command you posted is incorrect unless you actually have a user named "777".  You would need something like:  sudo chown username /media/sdb1 and of course, woould have had to create the directory sdb1 under /media for the mount point.  To change permissions, you would use the chmod command.

Are the flash drives you refer to still ext4 filesystems?

---

### Post by coffeecat on 2018-06-10
> **nk59 said:**
> (Robolinux v.9.2) and Debian Jessie 8.10

*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by Impavidus on 2018-06-10
Username is irrelevant, the contents can be displayed if the user ID has the right permissions. On Ubuntu the first user has user ID 1000, the next has 1001 etc, but other Linuxes may do this differently. As for chown or chmod, you have to use the correct mountpoint, which may be something like /media/username/partitionlabel, but again different Linuxes may do this differently.

---

### Post by nk59 on 2018-06-10
Thank you every one who replayed.  USB disk still ext4 and it was connected to Linux PC only. No windows involved. I tried chown on live DVD running OS (Robolinux 9.2.2):     sudo chown live /media/live/partition label       It worked and I was able to copy files to the USB drive. On another Linux (Deb) computer it will mount and show contents but will not allow to copy files with error message: ... Error opening file 'media/user name/partition label/file name': Permission denied.  Running code:       sudo chown user name /media/user name/partition label       granted permissions and I copied files to the disk successfully. Switching back to Live, OS mounted drive and showed contents in window but did not allow to copy files again. Apparently in   chown --help   there is a description of command to change permissions to owner and/or group. Unfortunately luck of knowledge of Linux did not allow to figure out proper code to grant permissions to any user on any of Linux computers.  Any help guys?    Thank you in advance,  Nick

---

### Post by yancek on 2018-06-11
I'm not sure I understand what you did from the comments in your last post.  If you run the chown or chmod commands from a Live system, you should have the changes while still booted.  Once you reboot the Live system, any previous changes made (chown/chmod) will not be maintained and you need to do the commands again.  Any type of change made on a 'Live' system will be lost on reboot.

---

