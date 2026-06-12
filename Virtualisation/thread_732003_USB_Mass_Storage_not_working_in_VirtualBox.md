---
title: "USB Mass Storage not working in VirtualBox"
date: 2008-03-22
forum: Virtualisation
---

### Post by fifth_rune on 2008-03-22
I am running latest version of VBox in Feisty (yeah I should update).  Anyway, after some random point in time a few weeks ago USB Flash drives and Hard drives no longer work in my WinXP Media Center Edition Guest.  Other stuff like my printer still does.  Also, XP picks up the device (i.e. it says 'safely remove USB Mass storage device') but I can't actually access it from anywhere.  Any help?

---

### Post by fifth_rune on 2008-03-23
Bump.  Please help.

---

### Post by Hero of Time on 2008-03-23
Do you have access to the USB devices directly in your Ubuntu? I don't have Ubuntu running atm, but I do recall that there is a howto here somewhere that describes the exact steps to take in order to get USB working in your VM.

---

### Post by fifth_rune on 2008-03-23
No, I get full access no problems in Ubuntu.

---

### Post by Hero of Time on 2008-03-24
So did I, but somehow I needed the group usbfs that has full rights on the usb devices and after that, it worked like a charm. You might want to check the search function here.

---

### Post by fifth_rune on 2008-03-24
I do have access from /etc/fstab for that group and anyway that doesn't explain why my USB printer works but not memory devices.

---

### Post by fifth_rune on 2008-03-27
Still need help so bump.

---

### Post by Hero of Time on 2008-03-27
Ok, a few things that you can try. First, make sure that the storage device is UNmounted on the Host (sudo umount /dev/sdb*). Then add the device in the Guest. That should make it work.

If it doesn't, check the device manager in the Guest. I read, and also had myself, that usb storage devices might not be installed properly in Windows Guests. I noticed that with 3 different usb sticks, the usb 1.1 didn't install properly. This was on XP host though, might be that the host didn't pass it through properly (it is MS we're talking about :P).

---

### Post by ikari87 on 2009-04-17
> **Hero of Time said:**
> I read, and also had myself, that usb storage devices might not be installed properly in Windows Guests. That's EXACTLY my problem. One PQI 8GB pendrive works, other, Sandisk Cruzer Contour 8GB does not. External WD MyBook doesn't work as well.
Both of the not working devices show in the device manager that "mass storage device" has a problem. I can't get around it, any help?

(Actually I'm having this in a virtual XP under OpenSUSE 11.1, with all the usb stuff configured (usbfs mounted and rights granted) - it works for other devices. The problem seems driver-specific. Of course I have the newest Virtual Machine Additions and all possible updates installed as well)

---

