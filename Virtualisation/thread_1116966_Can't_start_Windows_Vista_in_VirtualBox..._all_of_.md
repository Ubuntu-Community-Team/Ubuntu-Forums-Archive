---
title: "Can't start Windows Vista in VirtualBox... all of a sudden!"
date: 2009-04-05
forum: Virtualisation
---

### Post by the8thstar on 2009-04-05
I wanted to start Windows Vista today in its VM and I got the follwing message:

> PIIX3 cannot attach drive to the Secondary Master (VERR_FILE_NOT_FOUND).
Unknown error creating VM (VERR_FILE_NOT_FOUND).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


I don't recall fiddling with files related to VirtualBox or the VM or the kernel. So I'm at a loss as where to start looking for an answer and a fix. Your help will be appreciated!

---

### Post by Perryg on 2009-04-05
> **the8thstar said:**
> I wanted to start Windows Vista today in its VM and I got the follwing message:



I don't recall fiddling with files related to VirtualBox or the VM or the kernel. So I'm at a loss as where to start looking for an answer and a fix. Your help will be appreciated!

I know this sounds stupid but check it out anyway.

Did you by chance have a cd in the drive and mount it?  Live cd, guest additions, or something like that.

If so you can either put the cd back in and boot or look at the vbox  .xml file to see what the problem might be.  It is looking for a secondary drive of some kind.

---

### Post by the8thstar on 2009-04-05
Excellent hint **Perryg**! I unmounted the CD-ROM drive and was able to get back into Vista.

Thanks for your answer!

---

### Post by Perryg on 2009-04-05
> **the8thstar said:**
> Excellent hint **Perryg**! I unmounted the CD-ROM drive and was able to get back into Vista.

Thanks for your answer!

You are welcome.

---

