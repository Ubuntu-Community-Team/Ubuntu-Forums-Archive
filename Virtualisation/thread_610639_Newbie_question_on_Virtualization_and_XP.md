---
title: "Newbie question on Virtualization and XP"
date: 2007-11-12
forum: Virtualisation
---

### Post by kennedyjch on 2007-11-12
I've been operating under Ubuntu 7.04 for several months now and the only problem has been those "absolutely essential" applications which only run under Windows and for whatever reason don't work well with Wine or Crossover.

I had been thinking about establishing a dual boot machine and indeed I had partitioned my new computer's hard disks accordingly: Linux system section (10 gb), Linux files section (5 gb), Linux swap  section (500K), XP operating system (14 gb), XP applications (10 gb), XP data (10 gb).  The latter three of these partitions are formatted in NTFS.

However, recently I installed Virtual Box and installed XP home edition as a virtual machine.  How terribly cool!  All of the applications -- those must-have's -- all appear to work properly including: Dragon NaturallySpeaking, Garmin MapSource, Mind Manager and -- office/XL.  

So, my first comment is that if my needs are only to run a desktop and then Windows compatibility applications, then I think the Linux Ubuntu set up running virtual box with Windows XP home edition as a guest seems to be rather perfect.  Indeed it would appear that the only need to dual boot now would be to be able to enjoy computer games that require dedicated use of a high-performance graphics card.  

Question 1: Is it reasonable then that as XP virtualized under Linux handles virtually all my Windows needs (other than 3D gaming), one would configure accordingly and leave dual boot for gaming purposes only?

Question 2: Given the above, is it still necessary to have these pesky NTFS partitions for the virtualized XP under VirtualBox?  Wouldn't it make more sense to transform these NTFS partitions (at least those that are going to be used in the virtualized system) into Linux native partitions and let Linux/virtual box manage the filesystem?

Question 3: Is it true that one can move/copy/backup the virtualized installation by copying the .vdi files? If that is the case, then there should be no problem rearranging the hard disk and just pointing virtualbox to the proper disk images, correct?

Thank you in advance for your comments.

---

### Post by P4man on 2007-11-12
> **kennedyjch said:**
> 
Question 1: Is it reasonable then that as XP virtualized under Linux handles [COLOR="Red"]**virtually**[/COLOR] all my Windows needs (other than 3D gaming), one would configure accordingly and leave dual boot for gaming purposes only?

Nice word play :)

Yes, of course that is reasonable. If you dont need 3D in windows, and you have enough RAM, virtualizing windows is entirely logical. I do exactly what you describe, windows dual boot is only used for gaming.
> 
Question 2: Given the above, is it still necessary to have these pesky NTFS partitions for the virtualized XP under VirtualBox?  Wouldn't it make more sense to transform these NTFS partitions (at least those that are going to be used in the virtualized system) into Linux native partitions and let Linux/virtual box manage the filesystem?

Windows NT doesnt read Ext3, so no, they have to remain NTFS. 

Partitions that do not contain the OS (like data partitions) you might change them to Ext3 and then setup shared folder so your virtual windows can access them through networking, but I found this to be somewhat sluggish (windows networking usually is). Since Ubuntu can read/write NTFS partitions, I wouldnt make it harder than necessary.

> Question 3: Is it true that one can move/copy/backup the virtualized installation by copying the .vdi files? If that is the case, then there should be no problem rearranging the hard disk and just pointing virtualbox to the proper disk images, correct?


Im not sure I'm following you. You currently have the vdi files on an NTFS partition ? In that case, disregard my comment above, and yes, you can perfectly change that to Ext3, and move the vdi file there, and all should be well.

---

### Post by kennedyjch on 2007-11-12
Clarification: As I had configured my box originally to support dual boot, I set up linux and NTFS partitions. Then I discovered virtualbox and I created a .vdi file for XP on the NTFS partition (because I do not understand how to do otherwise.) But since I've noticed that you can create .vdi files on linuz partitions and NT does not appear to have a problem working with them...

As NTFS partitions seem to periodically annoy me with messages to "reboot Windows twice", presumably to check the disk structure integrity, I thought that why not put these files on the Linux partitions (I believe you confirmed you can do this). 

Then the only reason to maintain NTFS partitions would be to:
1) for the dual boot operating system (XP)
2) for an "XP" installed applications folder (i.e., alternative to "program files"). In this way if you have two XP installations, you can "economize" disk space for those apps that need to be in both VirtualBox and dual-boot XP install. (or is this too far out there)?

---

### Post by P4man on 2007-11-12
> **kennedyjch said:**
> 
2) for an "XP" installed applications folder (i.e., alternative to "program files"). In this way if you have two XP installations, you can "economize" disk space for those apps that need to be in both VirtualBox and dual-boot XP install. (or is this too far out there)?

Hmmm.. that should work..  Of course you have to install each app under both "virtual" and "real" windows so the registry settings are there, but yeah, you could save diskspace that way, I don't see why not. 

As for problem with NTFS, that should only happen when you don't shut down windows properly (or you still have it in hibernate mode). Even then you can force a chkdsk and mount the drives without actually booting windows, but I don't know the command by heart (I think ubuntu will tell you when you try to mount it though).

---

### Post by diogenes2 on 2008-06-24
Hello there!
I have been trying to get DRAGON into an XPPRO  partition on Kubuntu8 inside Vbox  without success. 

I THINK I posted to you in another forum but can't find it (BIG system problems due to XP) 
I'm most interested as to which version and your success with Dragon as you are the ONLY person I've found who has done it. 
I've just bought a DVR  to do remote dictation and upload to the system (XP side) a Sony sx57.  Having enough trouble setting it up(!) much less the Vbox.
So congratulations.
If you would care to I'd like to hear your results as to performance etc.

Cheers,
John

---

### Post by kennedyjch on 2009-11-17
I used Dragon Naturally speaking 8 preferred installed in XP Home guest under Virtual Box OSE running on Ubuntu (32 bit) host. 

Now that I have upgraded to 9.10, Dragon no longer works :-(

---

### Post by dy-namo on 2009-11-17
Question? Maybe one of you know how to do this or maybe have a link to some instructions. I have Ubuntu 9.10 and also Vista I can dual boot to either one with no issues, however is it possible to use a vboxOSE to access Vista as a guess and not have to go thru reinstalling Vista (which came factory installed when I purchased it no disk) to use it from Ubuntu ?

---

### Post by P4man on 2009-11-17
> **kennedyjch said:**
> I used Dragon Naturally speaking 8 preferred installed in XP Home guest under Virtual Box OSE running on Ubuntu (32 bit) host. 

Now that I have upgraded to 9.10, Dragon no longer works :-(

Can you give a tiny bit more info? VB still works, but Dragon doesnt start in the VM or what?

---

### Post by P4man on 2009-11-17
> **dy-namo said:**
> Question? Maybe one of you know how to do this or maybe have a link to some instructions. I have Ubuntu 9.10 and also Vista I can dual boot to either one with no issues, however is it possible to use a vboxOSE to access Vista as a guess and not have to go thru reinstalling Vista (which came factory installed when I purchased it no disk) to use it from Ubuntu ?

Bottom line is that is not really possible. You could image the disk and convert it to a vbox vdi drive somehow but windows wouldnt boot as it would be confronted with very different "hardware" (virtual hardware0. Its like taking a harddisk with windows from one machine and inserting in a very different one, it will almost always bluescreen.

---

### Post by kennedyjch on 2009-12-13
> **dy-namo said:**
> Question? Maybe one of you know how to do this or maybe have a link to some instructions. I have Ubuntu 9.10 and also Vista I can dual boot to either one with no issues, however is it possible to use a vboxOSE to access Vista as a guess and not have to go thru reinstalling Vista (which came factory installed when I purchased it no disk) to use it from Ubuntu ?

Unfortunately, unless you are wizard material, you'll have to install Vista under VBOX. Perhaps this question woul dbe better posed on the VirtualBox discussion group?

---

