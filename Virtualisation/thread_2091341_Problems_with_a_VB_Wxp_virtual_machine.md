---
title: "Problems with a VB Wxp virtual machine"
date: 2012-12-04
forum: Virtualisation
---

### Post by rva1945 on 2012-12-04
I have Ubuntu 10.10 running as host OS in both the laptop and a desktop PC.

In the laptop, VB manages a W7, the Wxp virtual machine started to reboot once and again after asking me to check the disk, no way to make it boot. I deleted the VM from inside VB with the Delete All Files option.

In the desktop PC, VB is managing a Wxp virtual machine. I copied its folder to the laptop to VirtualBox VMs folder.

Then I created a Wxp virtual machine using the "existing hard disk" and selected the vmdk file. When I started it, the same problem showed up: the Wxp reboots once and again. Of course it works fine in its source desktop PC.

Seems as if VB is still seeing the old Wxp virtual machine.

?

---

### Post by jaimerosario on 2012-12-17
You need to use "Export Appliance" from the File menu in Virtual Box, rather than copying the folder of the vm. Then, in your other computer, use "Import Appliance".

---

