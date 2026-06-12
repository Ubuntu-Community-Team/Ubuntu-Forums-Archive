---
title: "Windows 2000 + STOP error 1E == Dead Windows."
date: 2007-06-21
forum: Windows
---

### Post by StarsAndBars14 on 2007-06-21
I have a problem.  Windows 2000 (SP4 with updates) is giving me a BSOD whenever I try to log in, and crashes me even in Safe Mode.  The stop error that it gives is:

KMODE_EXCEPTION_NOT_HANDLED 0x0000001E(0xC0000005,0x8044745B,0x00000001,0x22804B27)
8047445B base at 80400000, DateStamp 3ee6c002 - ntoskrnl.exe

This started only yesterday, and neither using the Recovery Console nor the ERD have helped.  I had to reinstall all problem files over the old installation to even get to the point where viewing bluescreen information was possible - before that the system would auto reboot at "Applying security policy." -  I haven't installed anything like system services or new hardware, and there's nothing to cause a hardware conflict.  I doubt there's a virus on the partition since I have my ISP's security kit running on startup and it as well as Windows worked fine a week ago.

What the heck is going on here?  I think Windows is borked.

(PS I've looked everywhere I can on the net and none of the places I can find are any help.)

---

### Post by Yoooder on 2007-06-21
That's tricky...  just looking at some of that error info makes it sound kind of like either the kernel is trying to determine the timestamp of something that's royally puking, or perhaps the kernel's timestamp is out of whack--but that's just sheer speculation.

Can you confirm that the machine will run another OS ok, even just a LiveCD?  Maybe run memtest86 off the LiveCD just to rule out the possibility of bad RAM.

Aside from that, I would think a full scan of the hard drive for bad blocks would be a good thing to run.  If that turns up clean then maybe try to get access to the filesystem through ntfs-3g and backup your Docs & Settings then try re-installing Win2k back on top of the pooched install.  

Just make sure not to format the drive during the install (so the new copy will lay over top of the old one).  It can have ugly results, but should (1) help indicate if the problem is with hardware or the OS, and (2) provide you the chance to backup everything so that you can reformat and do a clean install of everything

---

### Post by StarsAndBars14 on 2007-06-21
Just so we're on the same page, the machine isn't broken.  I'm running Gentoo from it right now without problems.  Memtest doesn't indicate the RAM is failing.

I think I'll just install 7.04 instead and be done with 2000.

---

### Post by dca on 2007-06-21
I doubt this will help:
 
[http://support.microsoft.com/kb/124550/EN-US/](http://support.microsoft.com/kb/124550/EN-US/)
 
or this:
 
[http://www.webservertalk.com/message1064378.html](http://www.webservertalk.com/message1064378.html)

---

### Post by smoker on 2007-06-21
> This started only yesterday, and neither using the Recovery Console nor the ERD have helped. ]

did you try a chkdsk /f /r while in the recovery console. if you can't do that in w2000 recovery console, i would slave the drive to another windows machine if you can, and do the full chkdsk.

best of luck

---

