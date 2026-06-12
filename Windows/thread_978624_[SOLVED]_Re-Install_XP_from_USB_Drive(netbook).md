---
title: "[SOLVED] Re-Install XP from USB Drive(netbook)"
date: 2008-11-11
forum: Windows
---

### Post by notwen on 2008-11-11
I recently purchased a Dell Inspiron Mini 9 that came pre-installed w/ WinXP.  Needless to say I wiped the SSD and installed Ubuntu Hardy.  Now that I've verified that everything works the way I want it to I would like to go back and make my netbook a dual-boot system.  Problem seems to be that installing XP from a USB drive is easier said than done.  =]

I've installed many a Linux distro from USB drives using Unetbootin and didn't think there would be any issue whilst installing Windows using the same method.  Unetbootin doesn't mention any ability to install WinXP(or any other variant) from USB.  Using Unetbootin and an iso of my Dell restore CD only bring sup the Unetbootin menu and loops the 10sec countdown.

After countless Googles I've only came across a method of using any form of DOS to install and I was curious if anyone knew of any other ways to go about this or suggested a guide to perform this task?  The one I'll be using if no other suggestions turn out to be as simple is located [here]("http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html").  There are a lot of guides/how-tos out on the web, most are 2-3 years old and all seem to involve the same apps.

In the end, I'm wanting to dual-boot WinXP and Ubuntu on my 16GB SSD.  Thanks for any info you can toss my way. =]

---

### Post by smoker on 2008-11-11
hi, just curious, why do dell give you a restore cd when the computer has no cd drive, do they expect you to have one, or buy one?

i use a similar adapter to this to reinstall on machines without a built-in cd drive, though it has to be bootable via usb, if interested, you may find similar locally, and probably less in cost:
[http://www.amazon.co.uk/MY-Link-3-5-2-5-IDE-CABLE/dp/B000LU2A5W/ref=sr_1_2/276-6064772-4578156?ie=UTF8&s=electronics&qid=1226422915&sr=8-2](http://www.amazon.co.uk/MY-Link-3-5-2-5-IDE-CABLE/dp/B000LU2A5W/ref=sr_1_2/276-6064772-4578156?ie=UTF8&s=electronics&qid=1226422915&sr=8-2)

just a suggestion

---

### Post by notwen on 2008-11-11
I was hoping to not have to purchase any new hardware that would likely only get used on this netbook.  I have multiple USB drives and would like to avoid at all costs(even if small) getting anything new.  I'm pretty sure that installing WinXP off of a USB Thumb Drive is possible, but I'm just looking for alternative methods than the one provided in my link.  

Is this adapter you linked to simply an alternative way of hooking up a internal IDE drive to my netbook via USB?

---

### Post by smoker on 2008-11-11
> **notwen said:**
> Is this adapter you linked to simply an alternative way of hooking up a internal IDE drive to my netbook via USB?

yes, it connects an ide drive or an internal optical drive to a usb port, basically saves you buying a dedicated external usb cd drive which can be pricey. i suppose it may only be worth buying if you have an old optical drive lying around though!

---

### Post by notwen on 2008-11-13
Well the guide above does indeed work, but you'll need to remember that the FAT16 file system cannot recognize volumes over 2GB.  So if you do try this method use only 2GB or smaller flash drives.  I also used Daemon Tools to mount the iso of my restore cd onto a virtual cd drive and had no issues.  =]

---

