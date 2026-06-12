---
title: "Possible that Ubuntu might be able to use CD/DVD drive if Windows won't?"
date: 2019-01-15
forum: Windows
---

### Post by JeffreyDB on 2019-01-15
My laptop is currently running Windows 10. I haven't used my CD/DVD drive in awhile & when I tried to a little while back it wouldn't recognize that there was even a disk of any kind in the drive. I tried different CDs & DVDs but it acts like the tray is empty. Nothing appears to be physically wrong with the drive & I can hear it whirling when I close the tray with a disk in it.

It seems quite possible to me that when Windows did one of its automatic updates it messed up the drivers or interface or whatever. I went to the manufacturer's site to see if there were any new drivers, but it indicates that it just uses generic Windows drivers.

I'm wondering if it is possible that Ununtu might still be able to access the drive. Secondary question, if so, would it be possible that it could do so if I was running Ubuntu in a virtualization mode, such as through [VirtualBox]("https://www.virtualbox.org/"), or if in that setup Ubuntu or Virtual Box are just using Windows drivers anyway and if there is some flaw in their setup then Ubuntu wouldn't work either in a virtual setting.

Any help, thoughts or recommendations would be most appreciated.

---

### Post by yancek on 2019-01-15
Did the CD/DVD drive ever work with windows?
What's on the CD/DVD?  Data, blank discs?
Simple enough to test Ubuntu.  Either download and write it to a usb and boot with the Try option or install VirtualBox and boot the Ubuntu iso there.

---

### Post by wildmanne39 on 2019-01-15
*Thread moved to **Windows for a more appropriate fit**.*

If you install Ubuntu in virtualbox it will be able to use your CD/DVD drive if your drive is working but I suspect it is not. You will have to install guest extensions for Ubuntu to be able to access the drive from inside virtualbox.

>  Simple enough to test Ubuntu. Either download and write it to a usb and boot with the Try option or install VirtualBox and boot the Ubuntu iso there. 
+1 to the above.

---

### Post by JeffreyDB on 2019-01-15
> **yancek said:**
> Did the CD/DVD drive ever work with windows?

Yes. My laptop is about 4 or 5 years old & was working fine, though I didn't use the drive all that much, just occasionally. I probably hadn't used it in a year or more.

> What's on the CD/DVD?  Data, blank discs?

No, I tried commercial CDs. Different ones by different companies. Also tried a couple of DVDs from the library, but no go.

> Simple enough to test Ubuntu.  Either download and write it to a usb and boot with the Try option or install VirtualBox and boot the Ubuntu iso there.

OK, thanks. The only usb stick I can find is a little less that 500 MB, but it looks like the lubuntu distro is over 1 GB & I figured that would be a pretty small one. I thought there used to be "Live CDs", which I assumed were smaller, but don't see them online.

VirtualBox seemed to be a way to get around that, but I wasn't sure how it worked. If it only used Windows to access the hardware then I figured it wouldn't work even if a dual boot type situation might.

---

### Post by JeffreyDB on 2019-01-15
> **wildmanne39 said:**
> [I]Thread moved to **Windows for a more appropriate fit**.

[/I]Thanks for cleaning that up for me. I wasn't quite sure where to post it.

> If you install Ubuntu in virtualbox it will be able to use your CD/DVD drive if your drive is working but I suspect it is not.

OK, unfortunately that may be true I guess. One reason I suspected that it might be a driver issue or something was that there was a Windows update a day or two before that. I tried Windows support chat & the person did a remote system restore to the earlier version and seemed confident that that would fix it. I was wondering if the same thing had happened to a lot of people. But alas, it didn't fix it & I got alerts a day or 2 later that Windows was going to upgrade again, which it did. Since I hadn't used it in awhile, though, it could have possibly been an earlier update, perhaps even from a year or two earlier.

Of course, if it's just a worn out drive it's a non-issue.

> You will have to install guest extensions for Ubuntu to be able to access the drive from inside virtualbox.

Cool, I'll have to check that out. Thanks for the help.

Even if it doesn't work for this drive, it might actually work for a printer or a couple of scanners that became paperweights when I upgraded Windows. That does seem to be an advantage of Ubuntu/Linux over Windows. You can pretty much keep what you have if it's working well, or go back relatively easily.

Thanks again to both of you for the help.

---

