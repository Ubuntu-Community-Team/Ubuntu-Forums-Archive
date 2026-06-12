---
title: "Virtual Box not reading -32 bit Backtrack 5 .iso"
date: 2013-06-18
forum: Virtualisation
---

### Post by shibumi333 on 2013-06-18
I've been trying to create a VM using Virtualbox. I want to create a backtrack 5 VM but it will not read the -32 bit .iso. I've even downloaded and tried the -64 bit and it reads it just fine, but obviously does not work since I have a -32 bit machine. This is the message that is given to me .

Failed to open the CD/DVD image /home/shade/Applications/BackTrack/BT5-GNOME-32.iso.

Could not get the storage format of the medium '/home/shade/Applications/BackTrack/BT5-GNOME-32.iso' (VERR_NOT_SUPPORTED).

Result Code: VBOX_E_IPRT_ERROR (0x80BB0005)
Component: Medium
Interface: IMedium {29989373-b111-4654-8493-2e1176cba890}
Callee: IVirtualBox {3b2f08eb-b810-4715-bee0-bb06b9880ad2}
Callee RC: VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)

The specs I have under settings ->general tab are 

Type:Linux.
 Version: Other Linux.

---

### Post by 2F4U on 2013-06-19
Did you verify that the downloaded iso file is not corrupt?

---

