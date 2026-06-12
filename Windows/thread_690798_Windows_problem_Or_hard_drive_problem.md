---
title: "Windows problem? Or hard drive problem?"
date: 2008-02-07
forum: Windows
---

### Post by sdrawkcab on 2008-02-07
I've got a computer in the house that is very out of date. 128 MB of RAM, 35 GB hard drive, USB 1.0, you know; the works. I think there's some mold or something in there too. These things aren't completely irrelevant though.

The problem is that it apparently (not my computer) just restarted one day and then when powered back on, would go into a loop of restarting without getting into the OS. It would try to get there and even show the Windows XP loading screen, but it inevitably would restart. 

I immediately did the easiest thing and externally plugged it into my Ubuntu computer and scanned it with a couple virus scanners. I didn't find anything except a possible virus called "terminator.exe", which is apparently part of all HP computers and while sounding malicious isn't anything to worry about. I deleted it anyway, don't worry, I did my research and it's not needed. Nothing changed.

Next I figured that the install was possibly corrupt. They don't have the original XP disc for it (I'm guessing the computer just came with the OEM on it) so I took mine and did the only legal (I think) thing I could do. I tried deleting and reinstalling the boot.ini file first. I had absolutely no luck with this as whenever I tried:

```
ATTRIB -H C:BOOT.INI
```

Or

```
ATTRIB -R C:BOOT.INI
```

It would tell me that the files weren't accessible. 

Then I thought maybe the hard drive might have some corruptness to it. I ran CHKDSK, found some errors and the proceeded to run CHKDSK C: /r. This worked. I just had to do a FIXMBR I think to get it running. 

HOORAY! 

Nope. 

I booted to safe mode first and no problems. So I booted normally and no problems at first. I walked away to go find some windows specific virus scanners and when I came back, "Operating System Not Found" was displayed. 

I did all of the steps I took before again and was going to see if I could install the virus scanning stuff in safe mode, but when I got back, everything was dead once again. 

I don't know if anybody here has had these specific problems or not. It would be great if I could get some guidelines or diagnostic ideas I suppose. I'm starting to wonder if maybe it's just a bad drive and has nothing to do with the windows install considering how filthy everything is.

I'm terribly sorry for the length of this, I didn't want to leave anything out...sorry.

---

### Post by obdata on 2008-02-07
It could be the hard drive is corrupted or something, but it is very likely a hard drive that is about ready to go. :(  We had that happen several times already.

---

### Post by sdrawkcab on 2008-02-07
Thanks for the reply. That's what I'm starting to think. The computer is probably due anyway. I didn't scan for adware or spyware however. I'm not sure if there are anyways to do that. Does Knoppix or something have anyway to do that?

---

### Post by dca on 2008-02-08
When CHKDSK /F /R was run did the end result provide a listing of any bad sectors that were fixed or marked unusable?  It's not uncommon for the boot sector itself having a corrupt/bad sector causing the HDD to fail or be worthless at that point.  There's also boot sector virus' but I haven't seen too many of those.

---

### Post by lespaul_rentals on 2008-02-08
Sounds like a corrupt Windows install.  I've had similar problems.  Yes, hard drive failure is possible, but I think you might try installing a command-line distro just to check.

---

### Post by DrMega on 2008-02-08
I've known this happen to so many people all with XP SP2. I suspect something in the service pack causes corruption in the registry. I would reinstall Windows (if I really wanted Windows on there that is).

---

### Post by sdrawkcab on 2008-02-08
> **dca said:**
> When CHKDSK /F /R was run did the end result provide a listing of any bad sectors that were fixed or marked unusable?  It's not uncommon for the boot sector itself having a corrupt/bad sector causing the HDD to fail or be worthless at that point.  There's also boot sector virus' but I haven't seen too many of those.

It didn't list any sort of specific errors or sectors. It showed me "allocated memory" and such, but it didn't tell me anything specific other than "One or more problems have been fixed".  

> **DrMega said:**
> I've known this happen to so many people all with XP SP2. I suspect something in the service pack causes corruption in the registry. I would reinstall Windows (if I really wanted Windows on there that is).

Yes, you'd be right if you assumed I had SP2. But when you say that the registry is corrupt, couldn't that be fixed with a system restore?



I was told by someone else to go look at the C:/windows/minidump directory for any files. I have one [HERE](http://www.box.net/shared/owkxgn5gkc) if anyone knows what to do with it.

Also, I was told to press F8 before the windows logo showed and say to "disable restart on boot failure".  I did this and the next time I booted it inevitably failed but decided to run a CHKDSK by itself. It showed me this just a minute ago:

```

Deleting index entry [24] in index $I30 of file 355

Deleting index entry _24_~1 in index $I30 of file 355

Deleting index entry RP1963 in index $I30 of file 9325

Deleting index entry Basic Home Hardware.wps in index $I30 of file 47339

Deleting index entry BASICR~1.WPS in index $I30 of file 47339

```

Thanks for the help guys.

EDIT: I just system restored to September to be safe. Turned off, and then wouldn't boot. Operating System Not Found. I'll FIXMBR and see what happens.

---

### Post by Bungo Pony on 2008-02-08
If it's randomly rebooting, it's either a hardware problem  (not the hard drive) or a goofy Windows problem. I'd toss a different hard drive in there with a different OS, boot up, and leave it on for a bit.

It might also be a flakey IDE cable. Try changing that too (or swapping with the CD drive).

---

### Post by dca on 2008-02-08
For posterity I would suggest you replace HDD...

---

### Post by sdrawkcab on 2008-02-08
I pressed F8 before it could show the windows logo or anything. I set it so that it would show me any errors when it tried to restart. I got this:

```

KERNEL_DATA_INPAGE_ERROR

you should boot to safe mode, reboot, press F8 yadda yadda yadda...



*** STOP: 0x0000007A (0xC0201754,0xC0000185,0x805D5B25,0x0456D860)

Beginning dump of physical memory

```

Yep, I googled it. Points to a SCSI error. which is strange since it's not a SCSI drive or anything. I switched the ribbon it was connected to, to see if that was the problem. Nah. So, either it's the drive, the controller for the drive on the motherboard, or just a completely ruined windows install. Either way here there's nothing I can do about it. 

Anyone got some way to scan for hardware errors? It'd be nice to know the exact problem here. I guess I could install Ubuntu on there or something and see if that runs alright for a long while to determine if it was windows. If it didn't work though I still wouldn't know if it was the drive or the board. I'd put my money on the drive though.

Now...taking bets on when "that clicking noise" will start to surface. :)

---

### Post by SunnyRabbiera on 2008-02-09
My personal advice is see if you can get a system rescue disk or something, or download simply mepis or knoppix as I know they have a badblocks check on the disk

---

### Post by smoker on 2008-02-09
use the links below to download 'drive fitness test' and 'memtest' either to bootable floppies or cd's, and test out your hard drive and memory.

i would also check your power supply though if haven't a tester swap it out for a known working power supply if possible.

[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)
[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)
best of luck

---

### Post by andrewjoy on 2008-02-17
This hard drive sounds as tho its on the way out to me.

You could try a 

```
fixboot
```
and
```
fixmbr
```

form the recovery console this will remake your mater boot record so if you have any other dos/linux installs on there they will break if they use lilo.

---

