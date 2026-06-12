---
title: "Can't enumerate USB devices"
date: 2022-10-26
forum: Virtualisation
---

### Post by oygle on 2022-10-26
I have VirtualBox Version 7.0.2 r154219 (Qt5.15.3) installed, and Windows 8.1 running okay in the VM. Everytime I go into VirtualBox, I get the message

> Can't enumerate USB devices , which indicates why I cannot access USB devices in Windows 8.1. The USB setup is as follows:

usb 2.0 interface -  USB hub with keyboard and other devices
usb 3.0 interface -  USB stick 

The setting in VirtualBox is at 3.0 , so it should work okay.   The hub works in Windows 8.1 , because I can use the keyboard. Most posts I searched through with this type of error, the instructions were to ensure the VirtualBox setting was to USB 3.0 , which it is.

---

### Post by oygle on 2022-10-26
I added myself to the vboxusers group, rebooted, and now no message, however still cannot access the USB in the guest (Win 8.1).  It may be worthwhile to go through the set of instructions at [https://askubuntu.com/questions/1178183/virtualbox-cant-find-usb-devices/1379515#1379515](https://askubuntu.com/questions/1178183/virtualbox-cant-find-usb-devices/1379515#1379515)

---

### Post by ajgreeny on 2022-10-26
Do you have the Guest-Additions installed in your guest and assuming you do, are they exactly the same version as the Vbox application itself?
Also I note you have installed Vbox 7.0.2 which I tried but then went back to version 6.1 which I believe is more reliable and very stable.

---

### Post by oygle on 2022-10-26
> **ajgreeny said:**
> Do you have the Guest-Additions installed in your guest and assuming you do, are they exactly the same version as the Vbox application itself?

It took quite a lot of time to even burn the ISO for Guest Additions. I worked out that for some reason VirtualBox made any loading/mounting of CD's or DVD's impossible. Noting would read at all, media that has been previously buirnt and read okay. So a reboot and then I have the CD/DVD back again.  Then finally, installed the Guest Additions in the guest (Win 8.1).

I assumed I had to also install the Guest Additions in the host/Kubuntu, so following the instructions at [https://www.pragmaticlinux.com/2022/04/install-the-virtualbox-guest-additions-in-ubuntu-22-04/](https://www.pragmaticlinux.com/2022/04/install-the-virtualbox-guest-additions-in-ubuntu-22-04/) , tried that but it failed ..

> modprobe vboxguest failed

I hope I now haven't messed up anything else to do with kernels and booting.

> **ajgreeny said:**
> Also I note you have installed Vbox 7.0.2 which I tried but then went back to version 6.1 which I believe is more reliable and very stable.

I've now spent so much time with this version, I don't want to be repeating all that. Meaning a Win 8.1 install and updates takes a long time. The VM is already 17 Gb.

At least in the Guest/Win8.1 under file explorer I can now finally see a file under Network - >  \\VBOXSVR\SharedFiles , so that is something.

---

### Post by ajgreeny on 2022-10-27
You do not "burn the .iso for Guest additions"; normally it is not even an iso file but simply a package that is downloaded direct from Vbox, then you simply double click it in the file manager wherever you downloaded it and it installs in the Vbox application itself.

I do not know how it is all done if you use the Vbox version from Mint's own repositories as I have never used them for Vbox.

---

### Post by oygle on 2022-10-27
> **ajgreeny said:**
> You do not "burn the .iso for Guest additions"; normally it is not even an iso file but simply a package that is downloaded direct from Vbox, then you simply double click it in the file manager wherever you downloaded it and it installs in the Vbox application itself.

From the Guest/Windows I could **NOT** access either a USB or file sharing, so I was left with _only one option_, to burn the Guest Additions ISO, which was at /usr/share/virtualbox/VBoxGuestAdditions.iso

Then the Guest was able to install it, as it could 'see' the CD/DVD player. After that file sharing worked.

---

### Post by ajgreeny on 2022-10-27
Ah!
A Windows guest about which I know almost nothing so I'll have to leave it there.
I havent used Windows since XP days, and I moved away from even that in 2005 and too much has changed since then.

---

### Post by oygle on 2022-10-27
> **ajgreeny said:**
> I havent used Windows since XP days, and I moved away from even that in 2005 and too much has changed since then.

I'm trying to leave it completely  just needing the Win 8.1 to convert some old files.

---

