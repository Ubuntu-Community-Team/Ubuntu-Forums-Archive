---
title: "Virtualbox problems suddenly"
date: 2012-12-29
forum: Virtualisation
---

### Post by keevill on 2012-12-29
VBox 4.2.4 on an Ubuntu 12.04 Host with a Win 7 Guest installed, 


Using programs under the Windows guest OS, Until recently, I have been able to successfully manage my Iphone 4S ( JBroken ).
I have been using CopyTrans or Ifunbox or even Itunes.

Latest ver of Guest Additions are installed and I have connected my iphone via USB and enabled it but right clicking on the USB tab at the bottom of the screen or by selecting devices from the menu at the top.

I have made a usb filter so that the iphone connects whenever connected.

Recently After enabling it , the guest 'sees' the iphone correctly as an USB phone device and also an external USB HDD which I attached.
However, none of the Iphone management programs including itunes can see the iphone. 
That is CopyTrans, Ifunbox & Itunes.
I can test the USB external hard disk by copying files to and from it.
I've tried rebooting the machine, the iphone and also using a different cable and rear USB port but the problem remains.
Strange cos it was working perfectly for some time. I did peform a kernel update on Ubuntu recently so I figured I had to re-install Vbox so I downloaded and installed the latest ver 4.2.6 and also the latest GA.
Still no joy.
Host can see the usb device iphone but no software can connect to it.

I tried my ipod which works fine .

I tried my wife's iphone 4S and that won't work either.
Could it be a power issue with the usb ports ???

I confirm that The phone is seen in the Guest OS and I can use Win Explorer to travel the phone but the 3 progs I mention above which I want to use to put material onto the phone, do not see the device.

I posted in the Vbox forums but so far have had no solution so I try here before I move over to another virtualware software solution.
-keevill-

---

### Post by Ms. Daisy on 2012-12-29
When you reinstalled virtualbox, did you also reinstall the new version of guest additions inside the Win 7 guest?

---

### Post by howefield on 2012-12-29
Thread moved to the "*Virtualisation*" forum.

---

### Post by Sealbhach on 2012-12-29
Perhaps you could reinstall the iphone management software. If Windows 7 can see your iphone and your ipod works, then it may well be a software problem rather than a vbox problem.

.

---

### Post by keevill on 2012-12-29
> **Sealbhach said:**
> Perhaps you could reinstall the iphone management software. If Windows 7 can see your iphone and your ipod works, then it may well be a software problem rather than a vbox problem.

.
I have re-installed the GA from the freshly downloaded package.
There are 3 different software packages including the minimum access software package ( copytrans which is an exe file  ) and checked for updates .
I only tried with Itunes to see if it worked. I have no wish to use it. I want to use copytrans or Ifunbox within the win guest, neither of which can 'see' the device.
-keevill-

---

### Post by gmgdnj on 2013-02-18
> **keevill said:**
> I have re-installed the GA from the freshly downloaded package.
There are 3 different software packages including the minimum access software package ( copytrans which is an exe file  ) and checked for updates .
I only tried with Itunes to see if it worked. I have no wish to use it. I want to use copytrans or Ifunbox within the win guest, neither of which can 'see' the device.
-keevill-

Are you still trying to rectify this problem or have you solved it yet?  I want to use ifunbox as well but have yet to install. Have you tried removing all that u upgraded and reinstalled what was working?  Also, please advise as to what versions of all that u were using. Thanks

---

