---
title: "Enable USB 2.0 VMWARE Player 3.1"
date: 2010-07-15
forum: Virtualisation
---

### Post by jack frost on 2010-07-15
Is there a way to allow USB 2.0 support in VMware Player 3.1.  I am using Ubuntu 10.4 host and windows 7 64 bit virtual machine. Everything works fine except usb 2.0. Sorry if this has already been asked. thanks.

---

### Post by C.S.Cameron on 2010-07-15
Try the version from Oracle, not the OSE version from the repositories.

---

### Post by fjgaude on 2010-07-15
> **jack frost said:**
> Is there a way to allow USB 2.0 support in VMware Player 3.1.  I am using Ubuntu 10.4 host and windows 7 64 bit virtual machine. Everything works fine except usb 2.0. Sorry if this has already been asked. thanks.

Does USB 1.n work? You are activating the Removable Devices?

---

### Post by jack frost on 2010-07-15
> **fjgaude said:**
> Does USB 1.n work? You are activating the Removable Devices?
 
USB1 works fine.  I active the removable devices. I was just wondering if I could get USB 2.0 to work for faster speed.  You know that windows msg you get. (this device could perform faster)

---

### Post by jack frost on 2010-07-15
> **C.S.Cameron said:**
> Try the version from Oracle, not the OSE version from the repositories.
 
I will try virtualbox again. I used to use it then went to vm player with version 3.1.

---

### Post by fjgaude on 2010-07-16
Okay, I notice with the options provided with Player 3.1 that USB2 is greyed out, it using for that an early version of Workstation 5.n. So try VBox, non-open version.

---

### Post by jack frost on 2010-07-16
> **fjgaude said:**
> Okay, I notice with the options provided with Player 3.1 that USB2 is greyed out, it using for that an early version of Workstation 5.n. So try VBox, non-open version.

I googled around and found this and used gedit to add :

To enable USB 2.0 support in VMware Player, add the following lines  to your .vmx file:

Code:
 scsi0.present = "TRUE"
scsi0.pciSlotNumber = "18"
ehci.present  = "TRUE"
ehci.pciSlotNumber = "19"

It works.. you may find that two or three of these lines are already there.  Just look for the file in your folder where the vm is saved and there should be only one file with a .vmx extension.  

_for me_

scsi0.present = "TRUE"  - already there
scsi0.pciSlotNumber = "18"   - had to add
ehci.present  = "TRUE"   - this line was there ; but said false, changed to TRUE
ehci.pciSlotNumber = "19"  -this lines was there; but had a value of 160, changed to19

I would save the orig file some place before you make changes.. The first time I did it. I just added all four and the virtual machine would not start; but it did tell me in the error message that the lines already existed, so it made it easy to find which ones to add etc. They are also not all in the same place of the file. 


 I hooked up the archos5 right after and the usb could perform faster message did not come up.

Also in the virtual machine settings. Enable high speed support is not greyed out. I was able to check box it.

---

### Post by fjgaude on 2010-07-16
Wow, thanks for your efforts... glad they worked for you, but not for me... must have something to do with me not having what you have... through, I don't actually use any USB 2.0 devices, only printers under 1.0.

---

### Post by fjgaude on 2010-07-16
> **fjgaude said:**
> Wow, thanks for your efforts... glad they worked for you, but not for me... must have something to do with me not having what you have... through, I don't actually use any USB 2.0 devices, only printers under 1.0.

Okay, it does work if you make sure this line in the .vmx file is:

virtualHW.version = "6"

Mine was "4"... I didn't try "7", but it will likely work, as Player 3.1 is a lot like Workstation 7.0 and beyond.

Thanks again for helping the group out.

---

### Post by dcstar on 2010-07-22
> **fjgaude said:**
> Okay, it does work if you make sure this line in the .vmx file is:

virtualHW.version = "6"

Mine was "4"... I didn't try "7", but it will likely work, as Player 3.1 is a lot like Workstation 7.0 and beyond.


When I changed from VMware Server 1.10 to VMware Player 3.1 I found that my old VMs needed the HW version changed to enable all the advanced features available in new VMs created by Player 3.1.

Once the simple edit was done all of these features were available in my existing VMs.

---

### Post by jack frost on 2010-07-22
> **dcstar said:**
> When I changed from VMware Server 1.10 to VMware Player 3.1 I found that my old VMs needed the HW version changed to enable all the advanced features available in new VMs created by Player 3.1.

Once the simple edit was done all of these features were available in my existing VMs.

that is good to know. Yeah, 3.1 is like vmworkstation 6.5-7.0, when you open up the vm player and click on one of the vm's it has that verbiage listed under description to the right.

pic attached

---

