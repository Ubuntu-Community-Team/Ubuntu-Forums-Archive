---
title: "Issues With Clonzilla and VBox"
date: 2011-07-07
forum: Virtualisation
---

### Post by Joe- on 2011-07-07
I recently used Clonzilla to clone my WinXP laptop to an external HD. That worked fine but I now want to restore that Clone in a VBox on a Win7 computer. The issue is that VBox doesn't recognise the HD. I've added what i think is the HD to the USB devices although it does have a strange name. And when I try and click Devices>USB while the VBox machine is running is says it failed to attach the unknown USB device.

Any help would be really helpful.

Cheers Joe

---

### Post by lmarmisa on 2011-07-07
Try to access to the backup folder selecting the Samba protocol in the Clonezilla menu. Share the folder of the HD on Windows 7 and select the Bridged Adapter mode in the network configuration of your virtual machine. If you follow this recommendations, you will restore your backup to a virtual disk.

But I seriously doubt that you will be able to run your recovered system because the hardware of your virtual machine is quite different from the original system.

---

