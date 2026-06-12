---
title: "windows xp pro / ubuntu"
date: 2013-11-23
forum: Windows
---

### Post by squakie on 2013-11-23
I have a post in the forums for questions about the linux side, but could use some help on the windows side.

My DVD/RW drive broke down (opens, insert disk, tries extremely briefly [1 or 2 seconds] to spin up, then dies), at a bad time.

I have 2 Raspberry Pi media centers and thought I was done scanning everything so just completely reinstalled ubuntu and got rid of my Windows XP partition.  Now I have found I messed up the scanning of a few VHS tapes, and the adapters I have (I've tried 3) just don't work in ubuntu (they're usb based and apparently no linux drivers), so I have to create another small XP install so I can rescan those tapes.

So, no functioning optical media drive, and I need to install XP.  I know all about installing Ubuntu from USB flash, but don't have a clue about Windows.  I can have access to a Windows laptop to try to build such a flash (I own and have my XP Pro install disk) on it, but I can't install any additional software (got the laptop going for my sister, and she's real leary (as she should be I guess) of having me do anything to it now.

So - is there a way to create a Windows XP installation USB flash using the Windows XP Pro disk but no extra programs?

Thank you for your time.

---

### Post by QIII on 2013-11-23
There used to be something called Win2Flash, but I'm not sure if it worked with XP.

---

### Post by squakie on 2013-11-23
Thanks!  I'll some research on that after I get up on Saturday.

---

### Post by bashiergui on 2013-11-27
You might consider creating a VM for XP. Then if it ever comes up again you don't have to muck with partition tables.

It would be wrong to buy a USB cd/dvd drive, use it to install XP, then return it and get your money back. So don't do that ;)

---

### Post by shelvacu on 2013-11-27
if you copy, byte-for-byte from the disk to thumb, it should work as if it was a disk IIRC. The "dd" command is good for this. Assuming your disk is /dev/disk0 and the thumb is /dev/sdc (use lsblk to be sure), do "dd if=/dev/disk0 of=/dev/sdc". It will take a bit, and it will overwrite everything on the flash drive. Make sure to use /dev/sdc and **not** /dev/sdc1. Also, I would also reccomend the VM way, I believe most types of VM software allow usb pass-through, such that the drivers can be in the VM and it should still work.

---

### Post by electrohandyman501 on 2013-11-27
If the optical drive is bad, you will want it anyway some day in the linux os, so why not go ahead and replace it and be done with it.
I also agree that VM is the way to go, so long as you have a NON-oem version install disk of XP pro. If your disk is Dell oem, you will have to modify your vmsetup file to imitate a Dell bios to the guest system. BTDT.....

Just a thought......

---

