---
title: "Problem dual booting windows 10 and ubuntu"
date: 2015-09-27
forum: Windows
---

### Post by gullpet on 2015-09-27
I'm trying to dual boot windows 10 and ubuntu, but when i select the ubuntu partition of the hdd, it says me "reboot and select proper boot device", can someone help me? (fast boot and secure boot are disabled)

---

### Post by yancek on 2015-09-27
Windows 10 will normally use UEFI to boot.  Did you install Ubuntu in UEFI mode?  If you can boot the Ubuntu installation medium you used, go to the site below and download and run the boot repair script.  Make sure you select "Create BootInfo Summary" and do not try to make repairs.  It will output a file with detailed information and you can post that here for help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gfe on 2015-09-27
I don't know if I'm having the same problem as the OP, but Windows keeps on wiping out my dual boot. I've tried EasyBSD, and it creates a Linux option that doesn't work. To get into Ubuntu, I have to cancel out of the Windows startup and use the startup options in BIOS (I think that's what it is). I think it's possible that EasyBSD doesn't recognize my ext4 (?) filing system, but I'm not sure. I don't claim to understand how bootup works.

I'd be happy launching Ubuntu from the Windows startup menu. I'd also be happy launching everything from GRUB as long as I an still retain the Windows options such as system recovery and that Windows 10 doesn't constantly overwrite it.

Anyway, here's the link to my boot repair file:[ http://paste.ubuntu.com/12592007/]("http://paste.ubuntu.com/12592007/")

Thanks for any help you can provide!

---

### Post by gullpet on 2015-09-27
[http://paste.ubuntu.com/12592358/](http://paste.ubuntu.com/12592358/)
this is mine. (i know my hdd is a little bit messy, maybe because i tried different ways to fix this but i'm not an expert)

---

### Post by yancek on 2015-09-27
You have the appropriate EFI boot files for both windows and Ubuntu on sda2 which is the EFI partition.  You also have Grub boot code in the master boot record of that same drive which almost always causes problems.  I'm sure that is at least part of the problem.  I don't use EFI myself but if you want to search the forums, there are numerous similar posts here.  You could wait for someone with more familiarity with UEFI to post a possible solution.

---

### Post by jerrylamos on 2015-09-29
Wily 15.10 Ubuntu running on usb SSD, Win 10 on internal hard drive.

On Lenovo M58p desktop, a couple ubuntu Wily and an ubuntu 14.04.3 LTS are on a usb SSD hard drive.
Boot, F12 select the usb.

On HP Stream 13 laptop Win 10 on the internal hard drive.
Bios turn Security off and enable Legacy 
Boot Win 10 on 2nd screen select Power then shift-Restart
Then select usb to boot from.
Sometimes if I'm quick, power on and push F9 gets me the boot choices.

Now Microsoft Win 10 is not happy with any other operating system, so sometimes I have to use ubuntu forum forum techniques and also try Win 10 "troubleshooting" icon..

USB drives are getting pretty cheap, for example on Amazon a 64GB usb3 ran $22, 64GB usb2 is $21.  I put 3 ubuntu's, a 2G swap, and a 30G archive on one of these.

I don't mess with the internal drive which has Win 10 and will stay with the pc when I replace it in maybe 3 years or so average.  I'm into factory refurb pc's or laptops (and phones) from Amazon.  A year or so after a new model is out there are bargains.

Every once in a while boot Win 10 to update and remind myself why I like ubuntu instead.  The new Win 10 Edge browser is a mess example organizing bookmarks is hopeless.

Oh, Face Time on iPad is great to Australia where my son lives....we're in New Hampshire USA.

---

