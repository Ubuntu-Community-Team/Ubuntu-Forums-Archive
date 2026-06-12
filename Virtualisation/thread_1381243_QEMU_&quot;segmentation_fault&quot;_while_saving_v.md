---
title: "QEMU &quot;segmentation fault&quot; while saving virtual machine state."
date: 2010-01-14
forum: Virtualisation
---

### Post by jacek100 on 2010-01-14
Hi. Im using Qemu on Ubuntu 9.10. I did following:

qemu-img create -f qcow2 disc 10G

qemu -hda disc -cdrom /dev/cdrom -m 512

Then i installed quest OS (Windows XP). I shut down VM and booted again, without cdrom:

qemu -hda disc -m 512

After windows booted and I logged in, I did ctrl+alt+2 
and i entered following command in qemu monitor: 
savevm john

Then Qemu quits automaticallly, and it says "Segmentation fault" in hosts command line. I was trying to load that snapshot by typing:
qemu -hda disc -m 512 -loadvm john

This command should start qemu and load saved vm state with all running apps right? In my case it only started qemu and booted windows.

I tried also in qemu monitor:
loadvm john
but it says "Could not find snapshot 'john' on device 'ide0-hd0'. 
Typing "info snapshots" in qemu monitor doesnt show any avaible snapshot. Please help. Thanks in advance. Sorry for poor english language.

Here is a screenshot of qemu monitor and hosts command line:

---

