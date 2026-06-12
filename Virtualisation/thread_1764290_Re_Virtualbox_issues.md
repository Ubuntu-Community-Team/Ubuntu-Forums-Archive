---
title: "Re: Virtualbox issues"
date: 2011-05-21
forum: Virtualisation
---

### Post by dykesy61 on 2011-05-21
can't work out how to start a thread so I am posting here...I have successfully installed virtualbox with 11.04 but cannot get 11.04 to recognise USB devices.  I can get them to open the folder and then they disappear into thin air.  They don't appear in Places, and I would really like to be able to transfer stuff onto my virtual machine.

any help please?
and do relocate me if I have done this wrong.

cheers

Dykesy61, a long term, but shallow, ubuntu user!

---

### Post by howefield on 2011-05-21
Thread moved to "*Virtualization*"

Have you installed the extension pack ?

---

### Post by tgm4883 on 2011-05-21
> **dykesy61 said:**
> can't work out how to start a thread so I am posting here...I have successfully installed virtualbox with 11.04 but cannot get 11.04 to recognise USB devices.  I can get them to open the folder and then they disappear into thin air.  They don't appear in Places, and I would really like to be able to transfer stuff onto my virtual machine.

any help please?
and do relocate me if I have done this wrong.

cheers

Dykesy61, a long term, but shallow, ubuntu user!

What version of Virtualbox? Open source or closed source version? Did you install the VirtualBox Extensions for USB?

---

### Post by dykesy61 on 2011-05-21
I;m running 4.0.8 under windows 7 and I installed the USB 2 support package - vbox additions.
I am also using the guest software for ubuntu.

---

### Post by SecretCode on 2011-05-21
Did you install the VirtualBox **Extensions **for USB, **in Windows**? This is a different thing from the Guest Additions which you install in the guest (and isn't required for USB support).

---

### Post by dykesy61 on 2011-05-24
yes...I have...it opens the first time (a usb storage device) and then when I try to copy from it, selecting the destination, it disappears again.  it then seems to appear outside of virtualbox, ie on my main windows 7 64 bit home version, and is there waiting to see what I want to do with the usb storage device!

---

### Post by dykesy61 on 2011-05-24
Clicking on Devices in the virtuak machine when it was running, I also looked at USB devices, and it said:

Failed to attach UNKNOWN DEVICE to virtual machine UBUNTU 11.04


Result Code: 
E_INVALIDARG (0x80070057)
Component: 
HostUSBDevice
Interface: 
IHostUSBDevice {173b4b44-d268-4334-a00d-b6521c9a740a}
Callee: 
IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}

---

