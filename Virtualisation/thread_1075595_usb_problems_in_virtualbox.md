---
title: "usb problems in virtualbox"
date: 2009-02-20
forum: Virtualisation
---

### Post by ltchronic302 on 2009-02-20
I cant get windows xp in vb to recognise my usb camera or my flash drive. My camera is a microsoft vx3000 and ive read that the best way to get that camera to work is install xp in vb and just install the regular windows drivers(which i did) and use it that way but windows wont recognise when i plug it in. The flash drive at least shows  up but when i click it none of my files are in the window only system files of the usb drive

---

### Post by Mercury_Alpha on 2009-02-20
USB is not enabled by default in Vbox. You have to go into the Settings menu, scroll down to "USB" and check a few boxes. The settings menu isn't available when the guest OS is running.

(The Settings menu is found in the window where the guest OSes are listed, not in the window where the guest OS runs.)

---

### Post by ltchronic302 on 2009-02-20
is that the serial port page with port number, port mode ect? I dont know what to enter here.

---

### Post by HotShotDJ on 2009-02-20
> **ltchronic302 said:**
> is that the serial port page with port number, port mode ect? I dont know what to enter here.Open VirtualBox and click on your Virtual Machine then click “Settings” -- In the left panel, click on USB. Check off “Enable USB Controller” and “Enable USB 2.0 (EHCI) Controller". Do this for each VM in which you wish to have USB access.

---

### Post by ltchronic302 on 2009-02-20
i dont see usb just general, hard disks, cdrom, floppy, audio, network, serial ports, and shared folders. If i click serial ports its brings up a box with port 1//2 tabs with port, irq, mode, path, ect

---

### Post by mtopro on 2009-02-20
Are you working with the latest version from their site?  I have version2.1.4 installed on Ubuntu8.10.

When VB is up and running there is also a spot on the window for all hardware settings in the lower right that you can right-click on and enable all sorts of devices.

However you don't use your normal windows driver.  You should use the driver that VB assigns.  If it does not come up with XP, take a look at the name of it and download install that driver.  It may be under a different name than your webcam.

---

### Post by HotShotDJ on 2009-02-21
> **ltchronic302 said:**
> i dont see usbWhat version of VirtualBox do you have installed?  If you don't have the USB entry under "settings" then I suspect that you are using the OSE version.  It does not support USB at all.  See [http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160) to get a version that supports USB.

---

