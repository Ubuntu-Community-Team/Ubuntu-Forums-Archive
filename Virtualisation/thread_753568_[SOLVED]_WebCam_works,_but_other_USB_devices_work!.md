---
title: "[SOLVED] WebCam works, but other USB devices work!!!"
date: 2008-04-12
forum: Virtualisation
---

### Post by jeffsa12 on 2008-04-12
I downloaded a deb package, " virtualbox_1.5.6-28266_Ubuntu_gutsy_i386.deb",  of VirtualBox 1.5.6 for Ubuntu 7.10 from:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilte](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilte)

I'm running Ubuntu 7.10, and installedl WinXP Pro Corp edition in a virtual PC.. 
I installed the guest editions with no problems, got USB filters set up, USB working, but only for my cheapo Logitech webcam.

I need Win for my old Samsung digital cam and Yahoo webcam IM.  I have tried Gyach I,  E and Kopete as replacements for Yahoo.....unsuccessfully....cam image freezing, application freezing, etc. 

My Samsung digital cam plugs directly into a USB port. With Windows, it needed no driver installation, and it seemed to functioned as an external drive. I thought it would be no problem with Linux until I spent days trying everything I could find to get it working.....even tried Wine with the Windows drivers from the CD....no luck.

Getting to my problem with VBox, as I said, my USB webcam works, but nothing else. No USB printer, digital camera, USB thumb drives.

I've spent most of the day trying all the fixes I could find with no luck. Why would one USB device work but not all? I get the following pop up warning in my VBoxs /  Windows when I connect my camera, printer, etc. 

Failed to attach USB device

Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I have found and tried a lot of fixes.....with no luck.

 I initially installed VBox from the repositories before I figured out the two different versions....with and without USB support. Could something from the first install, that Synaptic may have left after uninstall be causing my problems?

Thanks for any help!!!

---

### Post by jeffsa12 on 2008-04-13
I have everything working now through trial and error......

Unchecked the" Enable USB EHCI Controller" in VBox which supports USB2.0......kinda sucks to only have usb 1.0, but beats no USB support. 

Put the following into my fstab file:

none /proc/bus/usb usbfs devgid=121,devmode=664 0 0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0
none /proc/bus/usb usbfs devgid=1003,devmode=664 0 0

121  is vboxusers
1001 is vbox
1002 is usbusers 
1003 is usbfs

I think I actually only need 1-2 of these groups, but I'm not sure
which ones.....and which ones I could delete but at least it's working!!!

Anyone willing to help me get this cleaned up
and explain the security or other issues with this mess?


Reinstalled WinXP along with a  larger dynamic V HD.

I have all my USB stuff working... HP USB printer, 3 different USB thumb drives,  Samgsung digital cam, Logitech webcam,  and Yahoo IM with webcam support.

---

