---
title: "Sun VirtualBox can't even launch Win95 CD... what's going on?"
date: 2008-10-30
forum: Virtualisation
---

### Post by the8thstar on 2008-10-30
Hey guys,

I'm trying to install Win95 as a guest OS on VirtualBox (not OSE). But it can't launch the CD and all I get are the following messages:

1. In the "Details" tab, when I select on the CD/DVD ROM link, I get the following message before I can access the sub-menu:

> Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}


In the VM, I get this (the CD starts spinning in the drive):

> FATAL! No bootable medium found. System halted.

Do you guys know how to sort out the problem?

---

### Post by deeminter on 2008-11-05
The message about the usb is not the reason you may be having problems loading windows 95. As I remember, windows 95 needs a boot floppy disk to get into DOS to allow you to access the Windows 95 CD. To get to the menu to allow you to boot from the floppy boot disk, you must press F12 shortly after selecting the start button for windows 95 in Virtualbox. Once you get to the menu, you will have 3 options, one of which will be for booting from a floppy disk, once in DOS, I beleive you need to select the CD drive which under windows convention will be drive D:. Once at the prompt on "D" drive, run Setup.exe, and the windows 95 installation will begin.

---

### Post by deeminter on 2008-11-05
Another possible reason that you may be seeing the message " No Bootable Media or CD present", might be that the CD is not enabled in the settings for Windows 95 in virtualbox. Before you start the windows 95 guest, you must enable the CD in the settings, then start Windows 95. The last post I made about the requirement of having a boot floppy is still valid. Hopefully this will assist you in getting your virtual windows 95 up and running.

---

### Post by the8thstar on 2008-11-06
> **deeminter said:**
> The message about the usb is not the reason you may be having problems loading windows 95. As I remember, windows 95 needs a boot floppy disk to get into DOS to allow you to access the Windows 95 CD. To get to the menu to allow you to boot from the floppy boot disk, you must press F12 shortly after selecting the start button for windows 95 in Virtualbox. Once you get to the menu, you will have 3 options, one of which will be for booting from a floppy disk, once in DOS, I beleive you need to select the CD drive which under windows convention will be drive D:. Once at the prompt on "D" drive, run Setup.exe, and the windows 95 installation will begin.

You are right. Without the floppy, no install. I just forgot because it's ben such a long time since '95! Thanks for looking into the matter for me!

---

