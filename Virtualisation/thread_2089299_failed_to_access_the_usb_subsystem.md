---
title: "failed to access the usb subsystem"
date: 2012-11-28
forum: Virtualisation
---

### Post by F35 on 2012-11-28
After reviewing this thread:

[http://ubuntuforums.org/showthread.php?t=1889090&highlight=usb](http://ubuntuforums.org/showthread.php?t=1889090&highlight=usb)


I still can't get virtualbox to recognize the USB's.  I have followed the directions to include my user in the 'vboxusers' group.  Here is the error:




failed to access the usb subsystem


Virtualbox is not currently allowed to access USB devices.  You can change this by adding your user to the "vboxusers" group.



  p, li { white-space: pre-wrap; }     Result Code: 
  NS_ERROR_FAILURE (0x00004005)
   Component: 
  Host
   Interface: 
  IHost {30678943-32df-4830-b413-931b25ac86a0}
   Callee: 
  IMachine {22781af3-1c96-4126-9edf-67a020e0e858}

---

### Post by F35 on 2012-11-28
So, I am running Virtualbox 4.2.4 r81684 on Linux Mint 14 (ie Ubuntu 12.10).  I believe the suggested action to fix the usb issue in prior versions actually works, but I am wondering if anyone else has had success using the same setup I  have.  

Any other thoughts on how to work around / fix this issue.

---

### Post by F35 on 2012-11-28
LinuxMint 14 (64 bit) - (ie ubunut 12.10 64 bit)

---

### Post by F35 on 2012-11-29
Apparently, even thought I could see my user in the vboxusers group, something hadn't updated.  As soon as I re-booted, my usb support on the virtual machine started working.

---

