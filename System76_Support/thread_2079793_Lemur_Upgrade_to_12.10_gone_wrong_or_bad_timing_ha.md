---
title: "Lemur Upgrade to 12.10 gone wrong or bad timing hardware failure"
date: 2012-11-02
forum: System76 Support
---

### Post by DNAtsol1 on 2012-11-02
I downloaded and did an inplace upgrade from 12.04 to 12.10 last night. It all seemed to go fine but when I restarted the system it went immediately into memtest and started spitting memory errors during the random number test (@ ~44% memtest completion). The errors were still screaming by after I left it run overnight (8 hours later)

I'm try to determine if this is upgrade related or an unfortunate hardware failure coincidence. 

Also, regardless of the cause, I would like to get a functioning system back. What info would you need to help me troubleshoot?

I'm running a 64-bit system on a Lemur laptop(model:lemu2) with 8GB RAM (I think - I haven't checked in a while) 

Thanks
DNAtsol

---

### Post by isantop on 2012-11-02
> **DNAtsol1 said:**
> I downloaded and did an inplace upgrade from 12.04 to 12.10 last night. It all seemed to go fine but when I restarted the system it went immediately into memtest and started spitting memory errors during the random number test (@ ~44% memtest completion). The errors were still screaming by after I left it run overnight (8 hours later)

I'm try to determine if this is upgrade related or an unfortunate hardware failure coincidence. 

Also, regardless of the cause, I would like to get a functioning system back. What info would you need to help me troubleshoot?

I'm running a 64-bit system on a Lemur laptop(model:lemu2) with 8GB RAM (I think - I haven't checked in a while) 

Thanks
DNAtsol
Go into the Grub menu (by holding shift immediately after the System76 Splash screen), then make sure to choose a non-MemTest option. See if it will go into Ubuntu.

If MemTest it spitting errors, then it's likely failed RAM (Software can't cause RAM prblems), so i would open a ticket on our website: [https://www.system76.com/my-account](https://www.system76.com/my-account)

---

### Post by DNAtsol1 on 2012-11-02
> **isantop said:**
> Go into the Grub menu (by holding shift immediately after the System76 Splash screen), then make sure to choose a non-MemTest option. See if it will go into Ubuntu.

If MemTest it spitting errors, then it's likely failed RAM (Software can't cause RAM prblems), so i would open a ticket on our website: [https://www.system76.com/my-account](https://www.system76.com/my-account)

Thanks. Just to complicate things, I did s you suggested and while trying to boot to GRUB  the screen flashed 3 "error: file not found" before bringing up the GRUB list. There were only 2 options, both memtest. 1 for memtest and 1 for memtest with console)

So, it might still be an updating software error (- corrupted grub?). If memtest is the only option it can't really boot to the new or previous Ubuntu) but I tend to agree that it's likely a HW failure. However, before I open a ticket I would like to be sure. 

So, can I edit GRUB or point to an externally located GRUB (say on a USB) and try to boot from there? 

Thanks
DNAtsol

---

### Post by isantop on 2012-11-02
> **DNAtsol1 said:**
> Thanks. Just to complicate things, I did s you suggested and while trying to boot to GRUB  the screen flashed 3 "error: file not found" before bringing up the GRUB list. There were only 2 options, both memtest. 1 for memtest and 1 for memtest with console)

So, it might still be an updating software error (- corrupted grub?). If memtest is the only option it can't really boot to the new or previous Ubuntu) but I tend to agree that it's likely a HW failure. However, before I open a ticket I would like to be sure. 

So, can I edit GRUB or point to an externally located GRUB (say on a USB) and try to boot from there? 

Thanks
DNAtsol

Okay. What I'm guessing happened is that the RAM failed at some point durig the upgrade, then that caused the upgrade to fail. Go ahead and open a ticket on our website, and we'll take care of it there.

---

### Post by LeeS87 on 2012-11-06
My pang9 has the same problem, memtest had errors at 44%, even after putting in replacement ram and moving it to the second slot.  I think it must be a software issue, one that unfortunately causes me kernel panics.

---

### Post by DNAtsol1 on 2012-11-07
> **LeeS87 said:**
> My pang9 has the same problem, memtest had errors at 44%, even after putting in replacement ram and moving it to the second slot.  I think it must be a software issue, one that unfortunately causes me kernel panics.
were you able to resolve the issue?? I just had system76 ship RAM replacement and if that is not the issue then I'll be looking for a next step.

---

### Post by LeeS87 on 2012-11-13
It appears that the ramtest errors have something to do with the test, since after replacing the ram, I reinstalled Ubuntu, and while the test still has the same results, Ubuntu has not had a kernel panic since.  So, maybe memtest86 no longer works properly.

---

### Post by isantop on 2012-11-13
> **LeeS87 said:**
> It appears that the ramtest errors have something to do with the test, since after replacing the ram, I reinstalled Ubuntu, and while the test still has the same results, Ubuntu has not had a kernel panic since.  So, maybe memtest86 no longer works properly.

Are you using the version included in Ubuntu, or the one downloaded form [memtest.org](memtest.org)? I've always found the one included with the Ubuntu installation to be a bit buggy on modern hardware, and need to use the later version from the Memtest Website.

---

### Post by LeeS87 on 2012-11-18
I was using the one in Ubuntu, and while I couldn't figure out how to download the other one to usb, I did discover that there is an Ubuntu specific memtest bug that would make it fail around 44% on Sandy Bridge (I'm guessing the bug also exists on Ivy Bridge).  This still doesn't explain why I get specific crashes, the most likely crash being when the computer is left on for a long period of time.

---

### Post by Pbethe on 2012-11-18
OK, so the Memtest off of the 12.10 is bad.  I have gotten similar errors from the one I got from the lubuntu disk, version 4.20, I think.  Is the version off the web site good?

---

### Post by isantop on 2012-11-19
> **Pbethe said:**
> OK, so the Memtest off of the 12.10 is bad.  I have gotten similar errors from the one I got from the lubuntu disk, version 4.20, I think.  Is the version off the web site good?

Yes, though you'll want to write it to a CD, as it's difficult to put it on a USB drive.

---

### Post by DNAtsol1 on 2012-11-26
> **isantop said:**
> Go into the Grub menu (by holding shift immediately after the System76 Splash screen), then make sure to choose a non-MemTest option. See if it will go into Ubuntu.

If MemTest it spitting errors, then it's likely failed RAM (Software can't cause RAM prblems), so i would open a ticket on our website: [https://www.system76.com/my-account](https://www.system76.com/my-account)

OK, I received my memory a little while ago and finally have time to install and try to recover my machine. 

1) how the *bleep* do I get at the memoryon a Lemur Ultrathin? I've taken out all the external screws, the battery, the HDD but something is still catching and preventing me from disassembling the thing (it seems to be caught somewhere near the middle of the mother board or toward the back).

2) assuming I successfully swap the memory how to I start the process of getting the OS upgrade completed if I don't have a Kernel to select in GRUB? I'm hoping I don't lose my home dir since I (stupidly) didn't finish backing up some data so I'm not real keen on doing a fresh install. 

Thanks

---

### Post by DNAtsol1 on 2012-11-26
quick update: figured out how to replace RAM (Damn you easy to remove keyboard!) 

Currently running memtest 4.2 that I assume, based on this discussion, comes from ubuntu. I do not have a cdrom on my machine so..... suggestions?

---

### Post by isantop on 2012-11-27
> **DNAtsol1 said:**
> quick update: figured out how to replace RAM (Damn you easy to remove keyboard!) 

Currently running memtest 4.2 that I assume, based on this discussion, comes from ubuntu. I do not have a cdrom on my machine so..... suggestions?

I would borrow a USB CD drive. It's really the best way to ensure that you have a solid, good copy running.

---

### Post by DNAtsol1 on 2012-11-28
> **isantop said:**
> I would borrow a USB CD drive. It's really the best way to ensure that you have a solid, good copy running.

memtest complete.... so is there a procedure I can go through to complete the upgrade and keep my /home dir? I do not see any kernel in the grub. only memtests.

If I do a fresh install of 12.10 is there some way to prevent an overwrite of /home 

Can I run a live version, access the HDD /home data get if off and bring it back later? 

finally, if I were to setup a /home partition (assuming I have to a fresh install) how much space would you recommend for the rest of the system on the HDD. 

Here's hoping

---

### Post by DNAtsol1 on 2012-11-29
> **DNAtsol1 said:**
> memtest complete.... so is there a procedure I can go through to complete the upgrade and keep my /home dir? I do not see any kernel in the grub. only memtests.

If I do a fresh install of 12.10 is there some way to prevent an overwrite of /home 

Can I run a live version, access the HDD /home data get if off and bring it back later? 

finally, if I were to setup a /home partition (assuming I have to a fresh install) how much space would you recommend for the rest of the system on the HDD. 

Here's hoping

To, perhaps, aid in more specific aid, I downloaded 12.10 and am running it as a livedisc. When I go to install, I get the notice that 12.10 is already installed. I have the option to install it again (along side the original) but the reinstall option is de-highlighted. On several other different threads I've read the following possible solutions:

1: select other (manual) and install on the same / partition without formatting and the original /home will be untouched but have to recreate my original user account names and passwords

2: use bootrepair to attempt to correct the grub not having the option of booting into 12.10

Which approach woud you suggest I choose if my primary concern is keeping and accessing my original /home directory.

Thanks
DNAtsol

---

### Post by DNAtsol1 on 2012-11-29
Fixed.

I decided to try the grub repair first since the initial install info displayed by the livedisc suggested the 12.10 upgrade appeared successful. 

I followed the instructions from the url below, selected the recommended options and things appear to be correct. Account info remains, nothing to reinstall or initialize. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

