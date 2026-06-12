---
title: "Ubuntu 15.10 and Windows 10 pro -- how to make them work together"
date: 2015-08-06
forum: Windows
---

### Post by cigtoxdoc on 2015-08-06
One of my "research" PCs is dual boot Win 7 64 Pro and Ubuntu-Gnome 15.10 64 bit.  BIOS is set to UEFI + Legacy.  Win 7 constantly wants to update itself to Win 10, but all updates fail.  I gather from reading other posts that I am trying to do something bad.  I don't have much on the Ubuntu partition that is not standard applications software and not much data (backed up).  The Win 7 side has some purchased software on it so I would rather not mess with the Win 7 side.

Has anyone else faced this problem and solved it?  If so, how?

Thank you,

John

---

### Post by yancek on 2015-08-06
The problems you are referring to seems to be a failure of windows 7 to update to windows 10.  Might be better off using a windows forum or the microsoft site.  Having Ubuntu or any Linux on a separate partition would not have anything to do with this.

---

### Post by QIII on 2015-08-06
Windows 7 will keep giving you that little button on the task bar and the polite suggestion that you update because that is what Microsoft wants you to do.  If that update is failing, there is something wrong with Windows or you are possible not following the process correctly.  It is not hard to misunderstand Microsoft's instructions from time to time.

It has nothing to do with Ubuntu.

---

### Post by Bucky Ball on 2015-08-07
> **QIII said:**
> It has nothing to do with Ubuntu.

If you are running a dual-boot and this is happening in Windows, agreed.

*Thread moved to **(Windows)**.*

PS: If you do need to post regarding 15.10 issues in the future it should go in the ***[Ubuntu Development Version]("http://ubuntuforums.org/forumdisplay.php?f=427")*** area as it is not released for another two months and is considered to be in development. Good luck. :)

---

### Post by Frogs Hair on 2015-08-09
Hardware compatibility is not an indication that the computer is ready to upgrade. The vendor/MS partner has to provide driver and OEM software updates before the upgrade will succeed and work properly. From what I've seen on various forums and due to my own upgrade experience on one of my computers this may take longer than MS anticipated.

---

### Post by cigtoxdoc on 2015-08-09
Thank you to all for your replies.  PC is homebuild based on MSI motherboard and Intel i7-4770K processor.  After much troubleshooting, problems seem to be due to corrupt files in the Win 7 installation that cannot be repaired with normal tools and I need to use an in-place reinstall. 

John

---

### Post by Frogs Hair on 2015-08-09
15.04 and Win 10 are working great on the home build desktop. I ran a factory reset on the laptop due to Win 10 driver and power manager problems. After reset the Win 10 app activated again post update and I wont initiate the upgrade as before with MS media creation/upgrade tool. When and if the upgrade appears in the update manager I'll go from there. Good Luck !  ;)

---

### Post by jerrylamos on 2015-08-22
I run ubuntu from usb SSD hard drive works fine thanks.  Usb cases run $10 or $20 from Tiger or Amazon, SSD's I look for a bargain on either website.

Win 10 upgraded from Win 7 is run from internal hard drive.

In past I've dual booted Win 7 and (several) ubuntu's on the internal hard drive.  Sooner or later grub screws things up.

Only rub is after booting Win 10, boot sequence usually boot sequence usb first gets screwed up so I do F1 or F12 or whatever to get ubuntu going again.

No big deal, I'm usually running ubuntu except to update Win 10 for a bazillion security updates, and one application which only works with Word 2010 on Windows.

So I've got Win 10 on the desktop and laptop, and can pass them on to whoever when I upgrade.

Ubuntu runs fine from usb and doesn't even mind switching between pc's, just have to adjust display settings.

---

