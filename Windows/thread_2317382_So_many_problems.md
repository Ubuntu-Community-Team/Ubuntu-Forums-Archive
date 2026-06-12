---
title: "So many problems"
date: 2016-03-16
forum: Windows
---

### Post by tyler98 on 2016-03-16
Ive had quite the day

Ive been trying all day to install Windows. Either as a dual boot with Ubuntu or just by itself. I tried to boot to windows 7 from my USB. When i try to boot it from BIOS, the screen turns black for a second, then shows the boot menu again. Then i thought id just uninstall Ubuntu. booted to Ubuntu from a USB, removed the partition. Nada. same problem from my BIOS boot menu. Installed Ubuntu again. I tried to change my screen size (it was overscanning) and the screen went black. Tried control alt f1. nothing. rebooted. This time i had a mouse with a black screen. Control alt f1 did nothing. now i'm here, on a live USB of Ubuntu, with text barely rendering.

I have an AsRock 970 Extreme4 mobo. Im fairly new to Linux, but know how to run terminal commands. Ive been using it since January.

What do I even do from here?

I know the Windows ISO is fine. Worked in my VM fine

---

### Post by Petre_Cristian_Cre on 2016-03-16
Have you tried to use a cd / dvd instead of USB , maybe your USB port does not working properly anymore because everything you do is on USB that takes you back in BIOS boot menu how you explained , so install from a bootable cd / dvd .
Thinking is not a software problem , 
Hope this helps !

---

### Post by Bucky Ball on 2016-03-16
*Thread moved to **Windows**.*

Best place for help with installing Windows would probably be a Windows forum, but you never know you're luck.

---

### Post by buzzingrobot on 2016-03-16
I agree with the recommendation to burn the Windows install ISO onto a DVD and try that.

Whether or not either OS is installed on the system should not impact how the other's installation image boots.

It's possible that the Win7 image -- since Win7 is rather old -- does not have the drivers needed to support some of the components on that Asrock.

---

### Post by yancek on 2016-03-16
>  I tried to boot to windows 7 from my USB.

Does that mean you have the windows iso on a usb/flash drive?  How did you get it there?  If you just copied it to a usb drive that won't work.  If you did it some other way, explain.

It's possible to boot windows from a usb or flash drive but you would first have to loop mount it to a mount point you have created, then create an ntfs filesystem on the usb/flash drive, then mark that partition as active/bootable, then copy the folders/files from the original loop mount point to the ntfs partition on the usb/flash drive, then install Grub2 to the MBR of the flash pointing to the boot directory on the ntfs partition on the flash drive and manually create a menuentry for windows.  You will also need to get the UUID for that partition which you can do in GParted.

Or you can burn the iso to the DVD.

---

