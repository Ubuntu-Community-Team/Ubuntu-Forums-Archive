---
title: "Printing remotely to virtualbox xp guest install - Karmic"
date: 2010-01-17
forum: Virtualisation
---

### Post by MrMister007 on 2010-01-17
Hi all, 

I'm running a desktop karmic system connected directly to a canon printer. I have looked everywhere for a working imageclass mf5770 driver but it seems that canon has given up linux support for these models.](*,) 
I have been able to print, though, from my virtualbox xp pro  guest install, and now I need a way to connect this OS to my existing home network so my other computers can print remotely. 

Any help would be greatly appreciated!

Thanks in advance

---

### Post by AlexandreP on 2010-01-18
Configure your VM's network interface to work as a bridged connection (instead of a connection through NAT). Then, you will be able to see your VM in your network exactly like any other computer of your LAN. You will then be able to access your printer through Samba/Windows Printer Sharing.

---

### Post by MrMister007 on 2010-01-18
Thanks for the tip. I configured one adapter as bridged and the second as host-only so I could both print locally and remotely. 
However, I find that in order to print, I have to manually give usb access to the VM through the devices menu. Is there any way to auto enable this?

Thanks again.

---

### Post by AlexandreP on 2010-01-19
If you want Windows to directly manage your printer, then yes, you have to give USB access to your USB device (your printer) to your VM. If you don't, your VM can't directly access your printer.

I never tried, but I think you can specify one or more actually-connected-to-your-PC USB devices to be automatically plugged into your VM in your VM's preferences, when your VM is turned off. (You can't change its preferences when it's on.) Just search a bit in the preferences.

---

