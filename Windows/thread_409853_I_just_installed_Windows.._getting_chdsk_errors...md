---
title: "I just installed Windows.. getting chdsk errors.."
date: 2007-04-15
forum: Windows
---

### Post by billdotson on 2007-04-15
I just installed Windows.  Right after I installed it and I had not installed anything even drivers I ran chkdsk.  Everything was fine.  Then I installed all of my games and apps and configured them and then booted into Ubuntu and made backup .img's of the Windows partition (while it was unmounted) with ntfsclone and also dd.  After that was done I booted back into Windows and ran chkdsk and I got the following:


Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Bill>chkdsk
The type of the file system is NTFS.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index verification completed.
CHKDSK is recovering lost files.
CHKDSK is verifying security descriptors (stage 3 of 3)...
Security descriptor verification completed.
CHKDSK discovered free space marked as allocated in the
master file table (MFT) bitmap.
CHKDSK discovered free space marked as allocated in the volume bitmap.
Windows found problems with the file system.
Run CHKDSK with the /F (fix) option to correct these.

 105474725 KB total disk space.
  45236368 KB in 55946 files.
     19848 KB in 3994 indexes.
         0 KB in bad sectors.
    130161 KB in use by the system.
     65536 KB occupied by the log file.
  60088348 KB available on disk.

      4096 bytes in each allocation unit.
  26368681 total allocation units on disk.
  15022087 allocation units available on disk.

C:\Documents and Settings\Bill>


The other day when I had installed Windows I installed all my stuff and then booted into Ubuntu, made a backup iage w/ dd and then restored that image to the partition Windows was on.  I booted into it and ran chkdsk and I got the EXACT same chkdsk message.  So then I decided to reinstall Windows.  This is that install that I re-did.. and it is doing the exact same thing.

Actually when I had just installed Windows the last time (this install) before I install ANYTHING I booted into Ubuntu and made a backup image w/ ntfsclone.  Then I restored that image and booted into Windows to see if it worked correctly.  I ran chkdsk and there were no errors.

I don't notice anything going wrong except for that chkdsk message.  This seems very odd..

This is very frustrating.. if anyone knows any way to help me I would greatly appreciate it.

Thanks.


I did google for that message and here is what Microsoft technet has to say:   [http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/w2000Msgs/2442.mspx?mfr=true](http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/w2000Msgs/2442.mspx?mfr=true)

is this even an issue at all?  Should I just keep going as planned?

I have also been looking at this : [http://groups.google.com/group/microsoft.public.windowsxp.basics/browse_thread/thread/c82ac10c0e2556cb/821bb178c8253927?lnk=st&q=chkdsk-+free+space+as+allocated&rnum=1&hl=en#821bb178c8253927]("http://groups.google.com/group/microsoft.public.windowsxp.basics/browse_thread/thread/c82ac10c0e2556cb/821bb178c8253927?lnk=st&q=chkdsk-+free+space+as+allocated&rnum=1&hl=en#821bb178c8253927")

---

### Post by M$LOL on 2007-04-15
By any chance did you select "Quick Format" instead of "Format with NTFS filesystem"?

---

### Post by billdotson on 2007-04-15
no I did not choose quick format.  I have booted into the recovery console with the install disc and have run chkdsk /r.

chkdsk /r scanned and said 
"CHKDSK found and fixed one or more errors on the volume"

then I booted into Windows and I ran chkdsk and it was fine.

Then I did a few things like disabled some startup services and ran chkdsk again and it was back. 

So then I booted into recovery console again and it did the same thing.

---

### Post by billdotson on 2007-04-15
maybe when I restored using ntfsclone it did something funny??  Odd that it did this before.. I doubt dd would have done the same thing when I restored.. :\

---

### Post by M$LOL on 2007-04-15
Hmm, I'm not sure. Is it inconvenient for you to reinstall again? Could be just something that went wrong during installation the first time.

---

### Post by billdotson on 2007-04-15
well it has done this on TWO installs.  I reinstalled to fix it and at first it worked but after I got all my programs installed and stuff it started doing it again.

From that Microsoft technet link it seems to say it isn't that much of an issue, but I can never be too careful

---

### Post by billdotson on 2007-04-17
can someone please keep checking this.  I get the MFT mis-allocation error after I install all of my programs.  Right after Windows XP installs the error is not present, but as soon as I get all my programs installed I get the error.  If I go to My Computer> C: and right click on it and go to check for errors then I tick both boxes and when it says the drive can't be locked I say ok.  Then I tell it that it is ok for it to schedule it to check on bootup.  It runs and says it corrected one or more errors but when I boot into Windows it is still there.  I have also tried booting into the recovery console and running chkdsk /r and I have also tried scheduling chkdsk /f /r to run at bootup.  

All those options say they fix filesystem errors but when I boot into Windows the MFT misallocation error is still there.  Can anyone help?

---

### Post by slayerboy on 2007-04-17
have you actually tried testing your hard drive for errors?  CHKDSK usually only checks file system errors.

Given that you have reinstalled a couple of times, it could be a couple of things.

1.  Physical problem with your hard drive.  Using something like Ultimate Boot CD ( [http://www.ultimatebootcd.com](http://www.ultimatebootcd.com) ) and one of the programs on there to test your hard drive, you should be able to pretty much rule out a physical problem with your hard drive.  Usually it will also tell you if there might be a problem with the IDE cable plugged into the hard drive.  You can easily solve this by either reseating the cable or replacing the cable, if indeed you have an IDE hard drive.

2.  Problem with the hard drive partition table.  If this is the case, and you are dual booting, pretty much the only way to fix this is by wiping everything out and reinstalling Windows and then Ubuntu.  You can wipe out the partition table several ways, but I usually use the Ultimate Boot CD and use a program that writes zeros to the drive at least once.  I had an issue with a bad partition table and it took 3 passes of zeros to get the partition table info wiped (took about a day and a half for the 3 passes of zeros to complete).

If after you've tried all of these things and you are still having issues, then you have a ghost haunting your computer.  LOL!

Seriously, these 2 steps should cure most of any issues you have if it's a hard drive problem, which is sounds like.  As a very last resort, it might just be that the hard drive is in very early stages of dying and the tests that you did could not detect any problems yet.

Good luck and let us know how it worked for you!

---

### Post by billdotson on 2007-04-17
I made my partitions w/ gparted and and left the first 108GiB unallocated on that drive.. you know for Windows install CD to format w/ NTFS (full format).  When Windows is clean.. i.e. nothing installed at all even drivers I don't get those errors, but after I install all of my programs I get the error.  What should I use to wipe my hard drive and repartition?  I have a SATA2 drive.  Also, I ran chkdsk /r at the recovery console to check for bad blocks.. there were not any.  Is this good enough or do I need to use another tool to check the hard drive?

---

