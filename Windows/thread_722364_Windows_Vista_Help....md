---
title: "Windows Vista Help..."
date: 2008-03-12
forum: Windows
---

### Post by MrSoze on 2008-03-12
I got a new computer not long ago and it came with Windows Vista.  I made a mistake when I was trying to run a dual os with Ubuntu and now I have lost my Windows Vista.  Ubuntu is alright but I still need Windows for a lot of school projects.  I know its supposed to have a hidden partition for restoring but it is gone too.  My computer is from Acer and I have been in contact with their tech support for about a month now,  They sent recovery CD's that wouldn't work. from what I've read its because I even cleared the hidden partition for restoring windows.  After a few calls and emails telling them the CD's do not work their answer is try using the system restore CDs.  They say they never send any of the Windows Vista disks. 

So what I am trying to find is someone who has purchased Windows Vista Business and has the disk.  I am looking for someone who would be willing to send a copy of it to me.  I will pay for the cost of the disk and the shipping.  I have my product key so I'm not asking for anyone to provide anything like that.  All I would need is the disk to load it back on and I will use my information to activate and register it.  I am getting tired of dealing with Acer and would like to get my computer back to the way it was.  So if you are willing to help or know another direction I can take please email me at [email]needvista@yahoo.com[/email].  I set up the account just for this.  I will then email you my address and go from there.  If you are still reading by this point thanks for your time and any help you can provide.

---

### Post by LaRoza on 2008-03-12
Well, if you really did wipe Vista, the system restore cd's should work.

(Try booting from them, the first one if there are more than one)

If they have trouble, use GParted (or the Ubuntu disk) to wipe the drive of all formatting. The pre-existing ext3 partition may confuse the Restore Disks.

---

### Post by MrSoze on 2008-03-12
alright thanks i'll try using the gparted or ubuntu disk because i've tried the disks over and over and they don't work so maybe that'll help.

---

### Post by LaRoza on 2008-03-12
> **MrSoze said:**
> alright thanks i'll try using the gparted or ubuntu disk because i've tried the disks over and over and they don't work so maybe that'll help.

They should work, I have used such disks (but from a different company) and it was able to restore fine. Takes a while, and is a pain though.

---

### Post by MrSoze on 2008-03-15
so i think i'm getting closer.  i used the ubuntu disk made a partition that windows would recognize.  this helped with the recovery disks that i have.  i was able to go through like i should and didn't get an error.  but once i click OK to reboot, it reboots the system and just loads ubuntu like always.  so once i did it again i pressed esc to bring up the menu and all it shows it ubuntu and ubuntu safe mode.  so i dont know it seemed to work but i feel like i'm still no closer to having windows back

---

### Post by Daveski on 2008-03-15
Can you see windows files on the windows partition (while you are in Ubuntu)?

If so, then you just need to sort out GRUB to include an option for Windows:

add this to the bottom of /boot/grub/menu.lst:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by MrSoze on 2008-03-16
heres what i have when i do sudo fdisk:
Device     Boot    Start     End	   Blocks  	  Id	      System
/dev/sda1      *     1	       2431	19526976       b	W95 FAT32
/dev/sda2         14220   14593     3004155         5          Extended
/dev/sda3          6513     14219    61906477+    7	    HPFS/NTFS
/dev/sda4          2432     6512      32780632+	 83	       Linux
/dev/sda5        14220	14593	    3004123+ 	82	Linux Swap/Solaris 

and before i did the recovery i only had it showing linux under the system.

---

