---
title: "Reinstall Vista"
date: 2007-02-12
forum: Windows
---

### Post by Ziox on 2007-02-12
So here's my situation.  I have just received my new HP Pavillion dv6000t laptop with Windows Vista Preinstalled.  I checked out the new (and bloated) OS, and I found it to be esthetically pleasing.  However, I'm longing to install Ubuntu and Windows XP.  In addition, I wish to remove all of the bloatware HP had preinstalled onto the system. 
 
So my question: Can I reinstall a clean version of Vista without the Software that came with it? And can I use the OEM provided serial number (production key) to reinstall Vista ON THE SAME HARDWARE?
 
Thanks in advance!
Ziox

---

### Post by kevinf311 on 2007-02-12
It depends on whether or not your computer came with an install disk or a restore disk.

If you have the restore disk, it is unlikely that you will be able to install without still having the HP programs.

If the computer came with a real Vista installation disk then you should be home free. I believe that the same Vista installation can be done on a computer as many times as necessary providing that the hardware does not change.

Be sure to turn off bitlocker if you have it before installing Ubuntu.

---

### Post by Ziox on 2007-02-12
Could you explain bitlocker a bit more?
 
Also, could I install using my OEM Production Key?

---

### Post by kevinf311 on 2007-02-13
Here's the [wikipedia article]("http://en.wikipedia.org/wiki/BitLocker") on it. From what I've heard, there may be an issue with booting from live CDs if bitlocker is active.

In theory, it's a good system and should keep people from being able to break into your data should they gain access to your computer (assuming it starts in the off position). You can probably have bitlocker enabled whenever, just not when you want to boot from the Live CD to install Ubuntu.

I'm not sure what CD is shipped with the OEM computer that you bought. Whatever was sent should allow you to reinstall the OS upon borkage onto the same hardware. What isn't certain is whether or not the CD has the HP programs bundled with it. If it is an HP Restore Disk, then it is likely that you will restore your computer to the state it was in upon the first boot. If the CD is a Full Windows Vista "whatever" Edition disk, then upon reinstalling you will have a clean vanilla Vista installation. That is the main variable: whether the disk is from HP or Microsoft.

---

### Post by Ziox on 2007-02-13
Thank you, that was  extremely helpful.  I'm glad that I don't have Vista Ultimate Installed (just Home Premium).  I've tried to shrink the size of my current Vista partition.  Unfortunately, the Gnome Partition Editor that accompanies Ubuntu 6.06 LiveCD was unable to shrink the size.  Do you know why it is like that?

---

### Post by BoyOfDestiny on 2007-02-13
> **Ziox said:**
> Thank you, that was  extremely helpful.  I'm glad that I don't have Vista Ultimate Installed (just Home Premium).  I've tried to shrink the size of my current Vista partition.  Unfortunately, the Gnome Partition Editor that accompanies Ubuntu 6.06 LiveCD was unable to shrink the size.  Do you know why it is like that?

Just a guess, but did you defrag that filesystem first? If the data is spread around... 
Well, time for some crude ascii art
* being data, _ free space

This can't be resized
[***___*___*___*_________*]

This can be resized
[*******__________________]

Sorry if that's not the issue though. :)

---

### Post by Ziox on 2007-02-13
You are right.  I did some research and found that the deframentation tool Vista includes only defrag files smaller than 64MB on a NTFS (why? I don't know).  So now I'm going to do a full defrag.  
 
Thanks for all the help. Everyone.

---

### Post by smoker on 2007-02-13
just a thought, doesn't vista run on a different file system, winfs, or nfs? i would check this and see if gparted can handle this type of file system if so!

---

### Post by Ziox on 2007-02-13
> **smoker said:**
> just a thought, doesn't vista run on a different file system, winfs, or nfs? i would check this and see if gparted can handle this type of file system if so!
 
Initially, MS planned to release Vista with a new file system - WIN FS.  However, due to numerous programming challenges (among others), the new file system is to be released with Windows Longhorn Server Edition. (Thankfully)

---

### Post by smoker on 2007-02-13
thanks, Ziox, for clearing that up, cheers

---

### Post by Ptero-4 on 2007-02-14
Ziox. Do you have a PC (Apple or System76 branded x86 computer) around? If you have one try to netboot your HP $PC from that PC, partition the HD and lock it (to prevent the HP $PC from nuking the ubuntu partition), then you can boot the HP $PC normally and install Ubuntu off the LiveCD.

---

