---
title: "Win 2000 missing boot record on HD, can’t load Win2000"
date: 2007-08-13
forum: Windows
---

### Post by Sudan on 2007-08-13
n.b.: Resolved 
Hi,
I’ve been reading these forums to get myself up to speed to switch from Win to Ubuntu.  There seems to be a lot of knowledge here.  I hope I can get some help with this harddrive problem.  

All of the sudden my Win 2000 Pro machine is giving me an error of missing boot record when I boot Win2000.  I don’t care too much about fixing this NTFS formatted hard drive to make it bootable.  What I would like is to get data files off it.  So my thought for an easy fix to get the files, is just to install this hard drive as the secondary HD in another machine running (uggh) Vista (don’t scream, please LOL).


Is there any reason not to install the faulty harddrive into the new Vista machine?  I assume that a boot record isn’t required on a slave drive.  Any warnings, suggestions?  Thanks.

P.S. Hope I put this post in the right forum, I’m new.

---

### Post by jimrz on 2007-08-13
> **Sudan said:**
> Hi,
I&#8217;ve been reading these forums to get myself up to speed to switch from Win to Ubuntu.  There seems to be a lot of knowledge here.  I hope I can get some help with this harddrive problem.  

All of the sudden my Win 2000 Pro machine is giving me an error of missing boot record when I boot Win2000.  I don&#8217;t care too much about fixing this NTFS formatted hard drive to make it bootable.  What I would like is to get data files off it.  So my thought for an easy fix to get the files, is just to install this hard drive as the secondary HD in another machine running (uggh) Vista (don&#8217;t scream, please LOL).


Is there any reason not to install the faulty harddrive into the new Vista machine?  I assume that a boot record isn&#8217;t required on a slave drive.  Any warnings, suggestions?  Thanks.

P.S. Hope I put this post in the right forum, I&#8217;m new.

that should work, or you could try booting a "live" cd (maybe knoppix, as it will mount the drive for you automatically) then  copy the data to an external drive and use it to move it wherever you need.

---

### Post by Sudan on 2007-08-13
> **jimrz said:**
> that should work, or you could try booting a "live" cd (maybe knoppix, as it will mount the drive for you automatically) then  copy the data to an external drive and use it to move it wherever you need.
Thanks for reply. I searched and found this interesting post

[http://ubuntuforums.org/showthread.php?t=339788&highlight=live+cd+knoppix]("http://ubuntuforums.org/showthread.php?t=339788&highlight=live+cd+knoppix")

Thanks for idea.  But this Win2000Pro machine that has the faulty HD in it, is an old hardware and I can't use external USB HDs on it.  (I've tried before.)  Does the Knoppix Live CD somehow allow me to "see" my Vista machine on my LAN?  

And where do I download a Knoppix Live CD?
Thanks.

---

### Post by goumples on 2007-08-14
if the boot record is corrupted, then pop in a dos boot disc from [www.bootdisk.com](www.bootdisk.com) (use msdos 6.22 imo) and type fdisk/mbr at the command prompt.. it should reset the default boot record.

---

### Post by angryfirelord on 2007-08-18
If you plan on dual-booting Ubuntu at all, Ubuntu will detect Windows 2000 and add it to GRUB for you.

---

### Post by Sudan on 2007-08-18
> **angryfirelord said:**
> If you plan on dual-booting Ubuntu at all, Ubuntu will detect Windows 2000 and add it to GRUB for you.

Hi, 
By this do you mean install Ubuntu on the harddrive while the HD is in its current state of not being able t load Windows 2000?

Or do you mean to use a live CD and boot that up and have it read the HD?

By the way, I did try running Windows 2000 "repair console" from setup boot disks.  I tried FIXMBR and FIXBOOT neither fixed the HD so that I could load W2k normally.

I downloaded Knoppix live CD, ver 5.1.1 and will try that.  Is ver 5.1.1 a good Knoppix version?  I am a complete wirgin on all Llinux stuff.

Thanks

---

### Post by angryfirelord on 2007-08-18
I meant installing to the HDD. You could shrink Windows 2000 make room for Ubuntu. GRUB doesn't work with Windows.

However, if you can get to Recovery Mode with your Windows CD, I think the command to fix your MBDR is fixmbr.

---

### Post by smoker on 2007-08-19
> All of the sudden my Win 2000 Pro machine is giving me an error of missing boot record when I boot Win2000. I don&#8217;t care too much about fixing this NTFS formatted hard drive to make it bootable. What I would like is to get data files off it. So my thought for an easy fix to get the files, is just to install this hard drive as the secondary HD in another machine running (uggh) Vista (don&#8217;t scream, please LOL).

this is by far the easiest way to get the data off the drive, just remember to set the drive jumper to slave instead of master.

once you have your data off, try a disk check, (if same as xp) right click the drive in 'my computer', select 'properties', and 'disk tools', then 'check this drive', and put a tick in the two boxes that appear in the dialogue box.

best of luck

once that is done, replace the drive, putting jumper back to master, and try to boot. if it still will not boot, as your data is now backed up, you can try a repair or a reinstall of 2000 if you require.

---

