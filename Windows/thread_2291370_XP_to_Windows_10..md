---
title: "XP to Windows 10."
date: 2015-08-19
forum: Windows
---

### Post by pyrophorus2 on 2015-08-19
I have 2 HDs, my bigger one is Ubuntu 15.04, I really don't want that touched at all.

My 2nd HD has a Blue-screened version on XP. I have download the Windows 10 iso onto that drive.
I would like to install 10, on that smaller drive, I'm not worried about anything on that drive either.

My thought was to unplug my Ubuntu drive and then install 10 on the active drive, but I'm not sure
if that will mess anything up.

Good idea, or do you have better ones?

---

### Post by yancek on 2015-08-20
I'm not sure if I'm reading your post correctly.  You seem to be saying that you have a windows 10 iso on a partition on the hard drive of the xp system and want to install windows 10 to that same partition??  Don't see that working.  Have you tried putting the iso on a DVD and booting from that?  You can boot windows 10 installer from Grub in Ubuntu and use that to install to an internal drive.  More specifics on your intentions would help.

---

### Post by CharlesA on 2015-08-20
I hope you have a license for Windows 10, since you can't get a free upgrade from windows XP to 10.

In any case, you'd need to create a bootable USB or burn the ISO to a dvd to do the install. Having the drive with Ubuntu on it unplugged would be a good idea, just to be safe.

---

### Post by buzzingrobot on 2015-08-20
If you unplug the Ubuntu drive, the Windows installer won't see it, so it will install on the only visible drive per normal. Then, it's a matter of reconnecting the Ubuntu drive and configuring the bootloader to show options for Windows and Ubuntu.

As Charles says, the free upgrade to 10 is not available for XP, only for 7 and 8.1. Microsoft sells 10 install images online, and that site includes step-by-step procedures to download the ISO, burn it, and launch the install.

---

### Post by pyrophorus2 on 2015-08-21
The XP is broken, its blue screened, not working and I don't care about it.
Imagine its like its a new HD.

I'll burn the DVD, and then unplug the Ubuntu drive, and then deal with the bootloader afterwards.
I'll come back with that question another time.

---

### Post by chemist931 on 2015-09-12
Its actually not that hard to mess with the installer.  If you only have two HDD's and you know both of their sizes, you can just select "Something Else" and select the right drive.  But, a computer that came installed with WXP will probably not run W10 too well.

---

### Post by QIII on 2015-09-12
Unless you have a Microsoft key for Windows 10, the installer ISO won't work.  If you have a currently installed version of an eligible product, you can upgrade to Windows 10.  That upgrade is contingent on the key for your current installation being valid.

I have personally communicated with Micosoft about this.  Their instructions:  

Do one of the following --

1.  ***Buy*** a Windows 10 key and use the installation ISO.

2.  Use the upgrade tool while running a ***currently installed and eligible version with a valid key.***

Windows XP is not eligible for the upgrade, so the upgrade tool will not work.  If you don't have a key for the Windows 10 installer, you will not be able to activate it.

---

