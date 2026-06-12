---
title: "VMWare on Windows and EXT4"
date: 2011-06-07
forum: Virtualisation
---

### Post by Oxwivi on 2011-06-07
Can VMWare or any other virtualization engine on Windows detect EXT4 partition and boot the operating system on it?

---

### Post by sean.dybob on 2011-06-07
Is the Ext4 partition on a hardrive or inside a already existing filesystem?

---

### Post by Oxwivi on 2011-06-07
How can it be inside another filesystem? I had installed an OS directly on a USB (not live, but a regular install), and it would be cool if I could run it while on Windows.

---

### Post by sean.dybob on 2011-06-07
it is posible to run an OS from an USB device inside virtualbox.

there is a command to attach virtualbox to such device.
al you have to do is the following:

```
vboxmanage internalcommands createrawvmdk -rawdisk /dev/<device> -filename <filename>
```this wil create a vmdk file that points to the device, make sure you have acces right to the raw device.

---

### Post by Oxwivi on 2011-06-08
Umm, that looks a command for VirtualBox in a Linux environment. I want VirtualBox/VMWare in Windows to access a USB and run the Linux-based OS in an EXT4 partition.

---

### Post by sean.dybob on 2011-06-08
The commands on windows are the same except the way drives are shown.
On linux raw drives are exposed as for example /dev/sda on windows it's \\.\PhysicalDrive0.

for more info execute: ```
vboxmanage internalcommands createrawvmdk
``` and ir wil print information related to the command.

---

### Post by Oxwivi on 2011-06-08
Do I do that on Windows? Because if I do that it says:```
[B]'vboxmanage' is not recognized as an internal or external command,
operable program or batch file.
```[/B]

---

### Post by sean.dybob on 2011-06-08
vboxmanage is found inside the virtualbox installation directory, should be inside C:\Program Files\Oracle\VirtualBox\ directory.

---

