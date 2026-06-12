---
title: "Dual-boot system restore problems"
date: 2014-11-08
forum: Windows
---

### Post by mittleiderja on 2014-11-08
So this is more of a Windows question, but I think it's because I have a dual-boot with Ubuntu that I'm having this problem...

I decided to try a new 3rd party Windows 8.1 theme, which has apparently screwed up my computer. Knowing there was a chance of this, I did create a restore point for Windows right before making this change, just in case. Now when I boot into Windows, I just get a black screen. Booting with the Windows install USB I have, I can get to repair installation menu, but nothing works.

Trying to use System Restore from within the install media, it just tells me I need to specify which installation to repair (I'm assuming it thinks the USB is it's own install or something, because I only have one instance of Windows on this machine), and to restart and choose at start up. Restarting just takes me to the grub to choose Ubuntu or Windows. Other options to repair the installation are blocked by saying the hard drive is locked and to unlock it (?).


I need to be able to get to the pre-boot options for my installed Windows, but I think this is blocked by the grub that allows me to choose between Ubuntu and Windows at startup. As soon as I hit windows it loads to a black screen with just the mouse pointer, and I can't do anything else. 

Any ideas on how to reset to the restore point I just made? Do I need to configure something in Ubuntu to allow windows to boot normally?

---

### Post by yancek on 2014-11-08
> Trying to use System Restore from within the install media, it just tells me I need to specify which installation to repair

What are the options?  Did you try any of them?  What happened if you did?

> I need to be able to get to the pre-boot options for my installed  Windows, but I think this is blocked by the grub that allows me to  choose between Ubuntu and Windows at startup. As soon as I hit windows  it loads to a black screen with just the mouse pointer, and I can't do  anything else. 

Once you select windows from the Grub boot menu, you are in windows and neither Grub nor Ubuntu are involved.  Looks like you need to try to use the repair options with your windows medium to repair the windows bootloader.  Are you using GPT/UEFI or MBR to boot?

---

### Post by Bucky Ball on 2014-11-08
*Thread moved to **Windows**.*

---

### Post by mittleiderja on 2014-11-10
Sorry for the late response. It turned out that the Windows recovery partition was actually on the other hdd on the computer, so from the BIOS I booted that hdd, and recovery worked perfectly... So, solved! haha

---

