---
title: "Installing Windows 10 Fresh from USB problems"
date: 2015-12-06
forum: Windows
---

### Post by squeab on 2015-12-06
Hi everyone. So my problem is that I'm trying to boot from USB into a bootable Windows 10 install with no luck. 

I used the terminal on my mac to create a bootable USB with Windows 10 for PC and plugged it into my computer that's running Ubuntu. The boot screen doesn't even show the USB as an option. 

Any ideas? 

I know I didn't jack up anything with the boot USB creation. I'm booting in UEFI (which is what it's supposed to be) with no luck with the USB drive.

Thanks,

squeab

---

### Post by yancek on 2015-12-06
Can you test the usb with windows on another computer to see if it boots to eliminate that as a problem?  Did you set the boot priority to boot from the usb on the computer on which you have Ubuntu?

---

### Post by squeab on 2015-12-06
The only other computer I have is a Mac, but you do have a point. Also, the boot order is good. The problem is that it doesn't even show up on the boot selection.

---

### Post by squeab on 2015-12-06
So I was able to fix the problem. When I created the boot disk in the Mac terminal, it kind of locked it out of being able to be read. Weird. What I did to fix it was use gparted to erase the usb then copy/paste the windows 10 files to the usb. And...magic. It worked.

Reasons I like ubuntu.

---

