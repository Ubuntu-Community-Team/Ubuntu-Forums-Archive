---
title: "VMware, Vista, Ubuntu and external harddrives"
date: 2008-03-04
forum: Virtualisation
---

### Post by SyrusMX on 2008-03-04
I've installed Ubuntu 7.1 on this desktop before, and it saw my external WD MyBook just fine. I found that I didn't want just Ubuntu, so I reinstalled Vista and snagged a copy of VMWare Workstation 6 ACE and installed Ubuntu. But while in Ubuntu I cannot find my external drive. It's not in /media and fdisk -l only shows the linux partition. Is there a way I can access, read, write etc to my external in Unbuntu via VMWare?

---

### Post by fjgaude on 2008-03-04
Is the external drive NTFS? You can access it through Samba and Windoes file manager.

Setup shares in both Ubuntu and Windows. Can you do this?

---

### Post by SyrusMX on 2008-03-04
It's a Fat32 drive, and windows sees it fine, but Ubuntu in VMWare doesn't. I know Ubuntu will see it, as I had just straight Ubuntu installed before and it saw it fine, but through VMWare it's not recongizing the drive.

---

### Post by fjgaude on 2008-03-04
It seems to be you have to setup shares, both in Windows and in Ubuntu, to permit Windows to actually see the drive. 

You have to use the Windows Explorer to see the drive on the network. Declare the drive in Ubuntu as a Share, and then Explorer can see it on the network.

You will not see the drive like it is a Windows drive, like you see the C: onto which vmware is installed. Is the drive a USB type?

There maybe other ways but this is the way I use.

Let us know how you are doing.

---

### Post by SyrusMX on 2008-03-06
Windows already sees the drive, Ubuntu does not. Windows is the base OS, VMWare is installed under windows, and is running an Ubuntu VM. The drive is USB.

---

### Post by fjgaude on 2008-03-06
I don't know how you setup Ubuntu as a guest. You might add this line to its /etc/fstab file and then reboot:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

This might go it. You do know that the USB devices are in the VM/Removal Devices menu of the guest?

---

