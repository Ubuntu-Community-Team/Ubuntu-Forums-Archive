---
title: "virtualbox hijacks usb printer?"
date: 2011-02-25
forum: Virtualisation
---

### Post by specialmoose on 2011-02-25
I made the switch to Linux about a month or so ago. I'm running Ubuntu 10.10 32bit with the latest virtualbox with Windows XP as the guest OS due to quickbooks 2002 not working with Linux (all versions seem not to work lol). I have a Brother 8460N printer connected via USB to the computer. Whenever I launch virtualbox Windows XP, Windows takes over control of the USB printer. If I try and print while XP has control in Linux, it fails.

Is there anyway to make both virtualbox Windows XP and Ubuntu share the USB printer simultaneously? If not, what can I do to share the printer? My ultimate goal is to have Windows XP virtualized with no internet connection purely to run quickbooks. I need printing in both environments.


edit: I'm running the latest virtualbox off Sun's website, not from the Ubuntu Software Center. That one doesn't have USB support. Windows XP is updated to latest service pack.

---

### Post by Hedgehog1 on 2011-02-26
> **specialmoose said:**
> 
Is there anyway to make both virtualbox Windows XP and Ubuntu share the USB printer simultaneously? If not, what can I do to share the printer? My ultimate goal is to have Windows XP virtualized with no internet connection purely to run quickbooks. I need printing in both environments..

specialmoose,

Your post got me curious, so I tried some variations on this.

As best as I can tell, a USB device is either used by Vbox OR the host OS.

However - you can toggle the printer back and forth without stopping XP in Vbox.

Here is how:

[B]In menu that is part of the Vbox device 'frame', menu to Devices >> USB devices >> Your printer.

Every time you click the printer in the menu, it toggles between the XP OS in Vbox and the Ubuntu Host OS.

While not as perfect as a shared printer would be - this will let you toggle the printer back and forth without shutting down QuickBooks and XP.[/B]

Hope this helps...

:KS

---

### Post by doas777 on 2011-02-26
hedgehog is exactly right. Virtual box filters usb devices based on your selections in the Vbox devices menu. if the device is disabled in Vbox, it will be available to windows, and vice-versa.

when making the change you may need to unplug and replug the device, but it sounds like you want the printer to be connected to the host full time, so you only need to do it on the initial change.

in terms of sharing, here is some info on netsharing your printer so windows can use it to:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
and a video:
[http://www.butterscotch.com/tutorial/How-To-Set-Up-A-Printer-In-Ubuntu](http://www.butterscotch.com/tutorial/How-To-Set-Up-A-Printer-In-Ubuntu)

gl&hf

---

### Post by Hedgehog1 on 2011-02-26
> **doas777 said:**
> hedgehog is exactly right.

Random Chance strikes in my favor!  Yes!!!!

:KS

---

### Post by specialmoose on 2011-03-04
UPDATE:

I checked in the USB settings for the virtual os (WinXP) and saw that it had all my USB devices enabled. So, I disabled my printer so that WinXP couldn't take it. Booted into Windows from virtualbox and sure enough, the printer was disabled. Using that guide that was posted, I turned my printer into a network printer and now I'm printing from XP via the network (host computer with the printer connected to it) and can print from the host os (Ubuntu). Works flawless!

---

