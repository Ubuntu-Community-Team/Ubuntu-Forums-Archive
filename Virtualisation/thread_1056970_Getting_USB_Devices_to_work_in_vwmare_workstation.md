---
title: "Getting USB Devices to work in vwmare workstation"
date: 2009-02-01
forum: Virtualisation
---

### Post by tekkenhead on 2009-02-01
1.	First off I am using ubuntu 8.04 with vmware workstation version 6.5.1 and installed image winxp pro.
2.	You have to mount a usb drive first. So usb_storage shows up under the usbcore module when you use the command lsmod. 
3.	Next umount the drive. Switch to su user and then from the command line issue the following commands. lsmod. In the output you should see a line with usbcore with usb_storage and ehci_hcd next to it. 
4.	You have to remove these two modules with these commands, rmmod usb_storage and rmmod ehci_hcd. After you issue the last command the drive might remount  after a few secs so you have umount again.
5.	Now fire up your vmware workstation and with the usb drive still installed. I change the setting so vmware doesn’t automatically detect usb devices which is under VM menu, Setting submenu. 
6.	You should now be able to connect the usb device with no problems!
7.	You can also disconnect and reconnect with the usb device. The only problem I ran into you might get a popup telling you the (device appears to be claimed by another driver for usb_storage on the host operating system) just acknowledge it and it will appear fine under windows.
8.	Also after you powerdown the vmware image, ubuntu will automatically mount the usb drive.

I hope this helps someone.

---

