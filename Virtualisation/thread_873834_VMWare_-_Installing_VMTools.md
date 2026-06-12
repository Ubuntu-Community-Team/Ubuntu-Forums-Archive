---
title: "VMWare - Installing VMTools"
date: 2008-07-29
forum: Virtualisation
---

### Post by lyric0n on 2008-07-29
Hi,

I am running Ubuntu w/ VMWare 1.06 and have multiple Ubuntu Server VM's...I would like to install VMware Tools, but when I select the option nothing happens and the install doesn't go through.

Does anyone know what I should do to make this happen?

Thanks,
Chris

---

### Post by fjgaude on 2008-07-29
What are the VMs: Windows, Linux, Unix?

---

### Post by lyric0n on 2008-07-29
The VM's at Ubuntu Server 8.04.

---

### Post by fjgaude on 2008-07-29
Could be there are not tools for 8.04 server... anyone know?

---

### Post by KatBuntu on 2008-07-30
You have to mount the VMware tools CD image, by selecting "Install VMware Tools" from the VMware server menu. It will automatically disconect any CD device you have working, and the VMware tools image CD will be set on the virtual CD device.
You have to mount it and copy the binaries to your root or /usr directory, and simply run them.

---

