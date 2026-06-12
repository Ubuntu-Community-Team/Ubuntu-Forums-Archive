---
title: "system problem and rts-bpp-dkms"
date: 2013-06-15
forum: System76 Support
---

### Post by shochatd on 2013-06-15
I have a Lemur Ultra running 13.04 and have recently updated the System76 Driver. But I keep getting frequent "System Problem Detected" alerts (usually when taking a kernel update). When I try to "report the problem", I get something about rts-bpp-dkms saying "The problem cannot be reported: This is not an official Ubuntu package. Please remove any third party package and try again." I tried to figure out what this package is about. Something about an SD card reader? My computer doesn't have an SD card slot.
-- David

---

### Post by lee170 on 2013-06-15
I have the same problem on my Lemur Ultra.  I ran sudo apt-get remove rts-bpp-dkms, then did the following to update, upgrade and cleanup, which removed an old kernel and headers.  Hopefully the next software update will run without the rts-bpp-dkms error.


sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove

---

### Post by Arioch on 2013-06-15
Wow, I have been having the same problem with my Lemur. Is this a Sys76 specific issue?

---

### Post by isantop on 2013-06-18
It doesn't necessarily represent a problem; the problem reporting utility, Apport (which is reponsible for those dialogs), isn't being turned off when Ubuntu is released (like it used to). 

The pacakge throwing the dialog is the card reader driver. Really, it silently recovers from the error and assuming you aren't having problems with your card reader, you won't have any issues.

---

