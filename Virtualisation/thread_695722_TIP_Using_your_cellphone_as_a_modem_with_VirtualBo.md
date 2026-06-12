---
title: "TIP: Using your cellphone as a modem with VirtualBox."
date: 2008-02-13
forum: Virtualisation
---

### Post by RudolfMDLT on 2008-02-13
Hi there,

This tip will quickly cover how to use a working bluetooth connection and VirtualBox to get internet access to your laptop or PC from your cell phone. I have a great need of this and as of yet I still haven't found anything working in Ubuntu or Linux in general for this purpose.

For the moment this is just a tip and I'll write a complete howto for this later if anybody is interested and after I have sorted out internet sharing with a virtual box!

What you need in order for this to work:
A fairly modern cell phone that at least supports GPRS and that can be synced with your computer in Windows.
Colemanvt, has already gone to GREAT lengths to write a detailed HowTo so I won't re-invent the wheel. Please go here to read his HowTo:

[http://ubuntuforums.org/showthread.php?t=690713](http://ubuntuforums.org/showthread.php?t=690713)

Now that you have Virtualbox installed and running with a complete install of Windows XP SP2, or any version of windows that will support your phone and hardware, we can continue.

I recommend downloading your phone's latest management software from the manufactures website, but using the CD supplied with the phone should work fine. Please install your Phone's PC management suite in the Virtual Machine.

Once that is done, shut down the Virtual Machine so that we can edit it's settings. Click on the Virtual Machine in the list and then click on settings. Click on the USB option in the list of settings in the right hand pane. Tick the boxes that read, "Enabled USB controller" and "Enable USB EHCI Controller". This will allow VirtualBox to control your USB devices at USB2 speeds. Click okay to close the dialog.

Make sure that you're phone or bluetooth dongle is plugged into a USB port and power up the virtual machine.

Once Windows has loaded, in the top menu of the VirtualBox click on "Devices", point to USB devices, and click on the USB device that represents your bluetooth dongle or cell phone(if you connected you cellphone via USB cable). Windows now has access to that device and it may start installing drivers immediately. Give it time. :) 

Open your phone's management software and follow the instruction on connecting an pairing with your phone - These applications are mostly idiot friendly and come with pretty good documentation, so this should not be too difficult. The application should also have an option for connecting to the internet or using your phone as a modem. Go ahead and connect to the internet! You should now have internet access within the VirtualBox. :)

Unplug any network cables and disconnect from any wireless networks you where connected to in Ubuntu, to completely make sure that you are indeed browsing off the phone's connections.

I'm still trying to figure out internet connection sharing between a Windows VirtualBox and Linux, as soon as I crack that I'll update this - Any help would be appreciated! :) 

Although it's been a real schlep to install VirtualBox and all the required software - Connecting to the internet while you're on the move is at least now possible, even for a complete Linux novice and it takes me about a minute to boot XP and get online.

Hope some one finds this usefull! :)

Cheers,

Rudolf

---

### Post by K.Mandla on 2008-02-13
Moved to Virtualization.

---

### Post by Skerit on 2008-08-14
Ubuntu is hogging every usb device I connect! I can see them in virtualbox just fine, it just won't touch them because ubuntu is "using" them!

Could anyone help on this one? Some command to "unmount" these kind of usb devices!?

---

