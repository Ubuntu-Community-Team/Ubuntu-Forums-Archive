---
title: "Windows XP won't start, Ubuntu 8.10, xVM VirtualBox 2.0.4"
date: 2008-11-23
forum: Virtualisation
---

### Post by turezky on 2008-11-23
I have this issue that is bugging me lately.
As many over here, I'm still bound to XP. And I use VirtualBox to run Windows XP.
I created an XP guest back in VirtualBox 1.5.x or 1.6.x version of VirtualBox and while running Gutsy.
Since then I updated to Heron and VirtualBox 2.0.4... And everything was working fine, even USB after some tricks...
However, after I updated to Intrepid, the problems started. I was using the same old hard disk with 1 year old Windows on it, which ran perfectly previously with the same settings, but now I get this screen, and the Windows keeps rebooting...
Anyone has the same issue, or at least do you know what this screen could mean?

---

### Post by bodhi.zazen on 2008-11-23
That is a windows error. Did you run the disk check as instructed ?

---

### Post by turezky on 2008-11-23
I tried running programs from Hiren's Boot CD, but none worked (freezed during CD-Rom driver load)... I don't any other means of running **checkdisk** on Windows...

---

### Post by turezky on 2008-11-24
Sorry, but, anybody?
I'm really stuck with this... :(

---

### Post by piine on 2008-12-06
> **turezky said:**
> Sorry, but, anybody?
I'm really stuck with this... :(

You should be able to boot from the XP disk and run chkdsk from the repair console. I've never ran it from virtualbox, however, I'm guessing it should run.

---

### Post by adamsj991 on 2008-12-07
Yeah, I am having the exact same problem.
I installed XP through VirtualBox, and I thought maybe that was the problem.
I get the exact same screen when I try and boot XP like normal.
Also, when I go past the Ubuntu thing to choose what OS to boot, into the Windows XP option, I have two options. A blank line, and the Windows XP Professional option.  When I try and boot into the blank line, it gives me a "missing corrupt file: hal.dll".  When I try and boot into the Windows XP professional, it gives me the blue screen shown in the first post.
Now, when I start Windows through VirtualBox, I can start the blank line, but when I try and boot the Windows XP option, it gives me that same hal.dll error.
So, I know how to fix the hal.dll error.  So, I tried to do that (you must use the Recovery Console on the disk).  But, I was pleasantly informed by my Windows disk that there was no hard disks on the machine.  Right.
  
Also, in Ubuntu, when I use GParted to look at my partitions, it says that the Windows partition cannot be read...again, right.

Help anybody?

---

### Post by elp99jcm on 2008-12-14
Two things to try, is the IDE controller set correctly 

Machine->Settings->Advanced->IDE Controller Type

Older ones used PIIX3 and new VMs by default have PIIX4 set.

Also, are the permissions set correct for the VDI file you are using?

~/.VirtualBox/VDI/MY_MACHINE.VDI should have user rw permissions.

These are two common problems I have encountered which cause a BSOD during boot.

---

### Post by HermanAB on 2008-12-14
"missing corrupt file: hal.dll" means that there is something wrong in the Windows c:\boot.ini file and it points to the wrong disk partition, thus rendering Windows unable to boot.

For example:

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

The 3 in the erroneous lines, above, points to the 3rd partition on the first physical hard disk.  Since this user only had 2 partitions, this value was incorrect.  Changing the value to 2, in both lines, allowed the user to complete Windows XP's setup.

The corrected BOOT.INI looked like this:

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect


Some sleuthing required...

Cheers,

Herman

---

### Post by SL666 on 2009-03-02
> **elp99jcm said:**
> Two things to try, is the IDE controller set correctly 

Machine->Settings->Advanced->IDE Controller Type

Older ones used PIIX3 and new VMs by default have PIIX4 set.





This fixed my exact issue THANKS!

---

### Post by AlanPorter on 2009-03-08
Thanks for the help.  Same problem, same solution (PIIX3).

Alan

---

