---
title: "no installer data could be found WoW dell"
date: 2011-06-28
forum: Wine
---

### Post by PrimeRadiant on 2011-06-28
**no installer data could be found WoW** 			 			 			 		   		 		 		Hi I am running a Dell inspiron 570 with the following specifications:

CPU: AMD Athlon II X2/X3/X4
Memory: 8 GB of RAM
Graphics Card: ATI Radeon HD 4200
Driver Packaging Version: 8.84.6-110324a-116088c-ATI
2D Driver Version: 8.84.60
Catalyst Control Center Version: 2.13
RandR Version: !.3

Wine 1.3+

The wine version was the most recent recommended in these forums.

Anyway I get the following message: "No installer data could be found" when I execute WOW.exe from the command line.

I read a post from another user and there may be hidden files. Then I  checked the howto:" WoW with Wine" again and saw that some files may be  hidden and the following would uhide them:

**Note** that on some WoW DVD's the  installer executable is hidden  and you need to re-mount the disc with  the 'unhide' option. To do this  type in a terminal:
  
sudo umount /dev/cdrom
sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

However when I ran the second command I got the following

william@PrimeRadiant:~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Can anyone help give me the proper command to unhide these files on WoW.  And I have another question. Once I unhide the files, can I simply copy  them to a directory on my computer and install WoW from there? Thanks.  Any help is appreciated.

---

### Post by war28 on 2011-06-28
Have you tried installing WoW on a Window$ partition and then copying to your Ubuntu partition?

That's what I did. I asked to install it on a friend's computer and just copied the files. Then I just did wine wow.exe and runs perfectly.

---

### Post by PrimeRadiant on 2011-06-28
Hi. Well no my hard drive is occupied entirely by ubuntu. I don't have Windows.

---

### Post by cwwilson721 on 2011-06-28
Easiest way (and the way I do it when installing from DVD)is to:
[LIST]
[*]Do the "unhide" mount
[*]Copy all the files from there to a folder on my computer
[*]Go to winecfg, and "mount" the folder as a drive in wine
[*]Right click the installer, and away I go
[/LIST]

I've done this for years, but since Cata came out, now I just download the full client from WoW/Blizzard. While it is 9GB, it's still smaller than the patches to get from the DVD to (as of today) 4.2

---

### Post by PrimeRadiant on 2011-06-28
When I try to do the 'unhide' I get the error message shown in my earlier post.

BTW I have copied the only visible file on the Wow disks (I have two) 'Installer.exe' to my home folder. But of course my problem is that I'm having problems unhiding the (presumably) other files on the disk.

---

### Post by cwwilson721 on 2011-06-28
Don't follow the instructions to the letter. 

Why? Because where your system mounts the DVD might not (Actually, IS NOT) where the instructions say.

I use a SATA DVD burner, and my DVD device is /dev/sdc, so I [code]umount /dev/sdc[\code] 

Find where your device is, and unmount it. Then substitute your device number for whatever the instructions say

---

### Post by cwwilson721 on 2011-06-28
Don't follow the instructions to the letter. 

Why? Because where your system mounts the DVD might not (Actually, IS NOT) where the instructions say.

I use a SATA DVD burner, and my DVD device is /dev/sr0, so I ```
sudo umount /dev/sr0
``` 

Find where your device is, and unmount it. Then substitute your device number for whatever the instructions say.

Example to mount:
```
sudo mount -t iso9660 -o ro,unhide /dev/sr0 /media/WoW/
```

** Sorry for the double post. Clicked wrong button and never knew...sigh... ***

---

