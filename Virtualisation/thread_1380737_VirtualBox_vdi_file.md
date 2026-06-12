---
title: "VirtualBox vdi file"
date: 2010-01-14
forum: Virtualisation
---

### Post by DBQ on 2010-01-14
Hi everybody. I have a question. In VirtualBox when you create a new virtual machine, in the snapshots directory of that virtual machine it creates a vdi disk.  Why? What is the function of it?  Thank you for the info.

---

### Post by SecretCode on 2010-01-14
It doesn't for me. vdi files only appear in the Snapshots directory when you actual ask it to create a snapshot.

The thing that does appear in that dir is a .sav file if you close the vm and save its state (ie don't power it off). This file contains the virtual RAM (and I presume things like CPU registers).

---

### Post by DBQ on 2010-01-14
The thing is I did not ask it to create snapshots. I just create a new VM, and the vdi file is placed in the directory.

---

### Post by DBQ on 2010-01-14
I completely removed the VirtualBox and then reinstalled it. Now it seems to work.

---

