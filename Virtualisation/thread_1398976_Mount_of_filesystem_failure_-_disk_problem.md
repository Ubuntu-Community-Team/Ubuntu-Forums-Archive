---
title: "Mount of filesystem failure - disk problem?"
date: 2010-02-05
forum: Virtualisation
---

### Post by andre26 on 2010-02-05
Hi guys,
I'm having a problme with an ubuntu installation under VirtualBox.
Anyhow I posted in General Help coz I think it's not a VirtualBox issue.
Whenever I try to start the Karmic Koala, after the grub prompt, it fails with a "**Mount of filesystem failed**. A manteinance shell will now be started. Control-D will terminate this shell and re-try" error.
It's not the first time it happens to me and I've already tried creating other .vdi images, but after a few weeks (the last time after a few hours!) the problems appears again!
I created first an image on the device mounted as /dev/sda1, divided into three partitions: 1 for the filesystem, 1 for the home and a swap partition.

Now if I run from the shell [FONT=Courier New]
fdisk -l /dev/sda1[/FONT] 
I get:
[FONT=Courier New]Disk /dev/sda1: 10.0 GB , 10001908224 bytes[/FONT]  (which is the size of the FS partition)
[FONT=Courier New]255 heads, 63 sectors/track, 1215 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table[/FONT] 

It seems to me it can't mount the home partition, because of some disk errors. I've also tried to repair eventual NTFS errors within windows but no errors were detected.

What do you think the problem could be?! How could I solve the problem?

Thanks,
Andrea

---

### Post by stlsaint on 2010-02-05
Are you using the latest Karmic iso release?

---

### Post by Kiting Illini on 2010-02-22
I am suddenly having a similar problem. It is difficult to isolate changes as I am just in the process of setting up a dual boot Karmic/Win 7 system on an HP dv6.
 
In the last 24 hours, I have reloaded/reinstalled both the ATI graphics driver and all of the sound drivers. This evening I did a system Update as part of a tutorial. I had just set up a new user, and had selected to log off in order to sign is as the new user. The display wen a little crazed, trying and failing to display the b/w login screen. I powered down, and now when I try to boot, I get:
 
"Mount of root filesystem failed. A manteinance shell will now be started. Control-D will terminate this shell and reboot" or something to that effect.
 
Grub still appears to work, but trying to boot in recovery mode or last known-good configuration both are ineffective. The Win7 side of the house still seems to work fine, and I have no indication of HW failure.
 
I'm thinking the maintenance shell is a good thing, but I'm too new to Linux to know what to do with it. Suggestions? I'd just as soon not have to reinstall from scratch. Any help will be most appreciated.

---

