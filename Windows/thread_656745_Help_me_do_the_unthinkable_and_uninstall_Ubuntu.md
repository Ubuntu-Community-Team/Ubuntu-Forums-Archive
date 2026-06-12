---
title: "Help me do the unthinkable and uninstall Ubuntu"
date: 2008-01-02
forum: Windows
---

### Post by PaddyMcNasty on 2008-01-02
I have been dual booting XP and Ubuntu for a while (XP for gaming) and have just spent all my money upgrading my PC for Vista and bought a laptop. My intention is to have my desktop for gaming and therefor running Windows and my laptop for everything else and running Ubuntu. 

Only problem is I don't know how to get rid of the Ubuntu partition on my desktop. I don't want to wipe my hard drive completely.

Could someone take me through how to do it? I'm not an idiot but I'm not a computer genius either so no words over 3 syllables please!

Cheers
Patrick

---

### Post by overdrank on 2008-01-02
> **PaddyMcNasty said:**
> I have been dual booting XP and Ubuntu for a while (XP for gaming) and have just spent all my money upgrading my PC for Vista and bought a laptop. My intention is to have my desktop for gaming and therefor running Windows and my laptop for everything else and running Ubuntu. 

Only problem is I don't know how to get rid of the Ubuntu partition on my desktop. I don't want to wipe my hard drive completely.

Could someone take me through how to do it? I'm not an idiot but I'm not a computer genius either so no words over 3 syllables please!

Cheers
Patrick

HI and to remove Ubuntu this link will help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by marx2k on 2008-01-02
> **PaddyMcNasty said:**
> I have been dual booting XP and Ubuntu for a while (XP for gaming) and have just spent all my money upgrading my PC for Vista and bought a laptop. My intention is to have my desktop for gaming and therefor running Windows and my laptop for everything else and running Ubuntu. 

Only problem is I don't know how to get rid of the Ubuntu partition on my desktop. I don't want to wipe my hard drive completely.

Could someone take me through how to do it? I'm not an idiot but I'm not a computer genius either so no words over 3 syllables please!

Cheers
Patrick

Just format the partition Ubuntu was sitting on. The only problem I see you having is GRUB sticking around in the boot sector but I think this should help you:

[http://www.linuxquestions.org/questions/linux-newbie-8/unistalling-ubuntu-532170/?highlight=removing+grub#post2645130](http://www.linuxquestions.org/questions/linux-newbie-8/unistalling-ubuntu-532170/?highlight=removing+grub#post2645130)

---

### Post by jken146 on 2008-01-02
Boot into the Live CD.  Use gparted to delete your Ubuntu partition.  Then format it in NTFS and use it as Windows storage.

Copy any important personal files on this partition somewhere else before you do this -- they will be erased.

---

### Post by PaddyMcNasty on 2008-01-02
Thanks for your quick replies. But I have just discovered a new problem. I just rebooted to get into Ubuntu and backup my files, but it seems when I upgraded to Vista, I lost GRUB. Eek! Anyone know another way to get into it?

---

### Post by jken146 on 2008-01-02
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by marx2k on 2008-01-02
Well you can boot the liveCD and mount the Ubuntu drive when youre in the live CD (or try to get Vista to read ext3)

---

### Post by PaddyMcNasty on 2008-01-02
Wow, you guys are fast! Ok I'll try to find my Ubuntu CD and let you know how I get on. But I'm in Scotland and it's 4am here and I'm going to collapse if I don't go to bed now so will post back tomorrow.

Thanks again

---

### Post by Dr. C on 2008-01-02
There are two steps for this 

1) Remove GRUB from the Master Boot Record (MBR)

2) Format the GNU / Linux partitions

Note if one just does 2 without first doing step 1 when rebooting one gets a GRUB error and a black screen. If this happens proceed to step 1.

Step: 1

The most logical place to look for information on how to do get rid of GNU / Linux is:
[http://www.microsoft.com]("http://www.microsoft.com")
A search on that site for "remove Linux" will provide the following: 

The old fashioned way using a MS-DOS floppy: Boot from an MS-DOS floppy that has the FDISK command. The type: ```
 fdisk /mbr
```This will get rid of GRUB and Windows XP should then boot normally. 
[http://support.microsoft.com/kb/171611]("http://support.microsoft.com/kb/171611")

This is the method I used when I was trying and messing up Ubuntu Breezy 2 years ago. By the way I used an old working 286 to produce the floppy to do this unthinkable deed. To create the floppy on the 286 I used: ```
format a: /s
``` If one does not have a working 286 running MS-DOS (or some other way of creating MS-DOS system disks) then [http://www.bootdisk.com]("http://www.bootdisk.com") is a great source for boot disks. 

The more modern way:
Booting into the Windows XP recovery console and use the FIXMBR command
[http://support.microsoft.com/kb/314503]("http://support.microsoft.com/kb/314503")

Step: 2

The GNU / Linux partitions can then  be formated using the disk administrator tools in Windows XP.

---

### Post by chips24 on 2008-01-02
pop in youre windows disk, delete the partition, go to the command promt and type

"bootrec /fixboot"
"bootrec /fixmbr"

or else you will get an ERROR 22 on youre GRUB loader

---

