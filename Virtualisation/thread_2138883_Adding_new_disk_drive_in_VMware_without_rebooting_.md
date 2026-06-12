---
title: "Adding new disk drive in VMware without rebooting server"
date: 2013-04-25
forum: Virtualisation
---

### Post by KernelXitron on 2013-04-25
I'm running Ubuntu Server 12.10 under VMware.

I need to add a disk, which I've created in VMware and which has been assigned to the server.  'fdisk -l' does not detect the added hardware, nor does 'hwinfo'.

If I reboot, the new drive shows up.

Is there a way to detect the new dev without having to reboot the server?

Thank you!

Kernel Xitron

---

### Post by jocke92 on 2013-05-01
To have the ability to do that in a Windows machine I know that vmware tools is required. Have you got that installed?

---

