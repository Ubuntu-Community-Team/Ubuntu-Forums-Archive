---
title: "Using USB &#38899;ound &#20013;n Vmware and host"
date: 2008-08-13
forum: Virtualisation
---

### Post by falkaholic on 2008-08-13
&#21566;'m running x86 with VMWare Workstation 6.


&#21566; am using a USB (Griffin iMic) &#38899;ound &#20013;n/out device. &#20013;n order to get &#38899;ound &#20013;n my VMs, &#21566; have to attach it to a VM, which excludes &#38899;ound &#20035;rom the host and &#20182;ther VMs.

It seems VMware should just &#20351;se the hosts &#38899;ound &#25454;et up but doesn't. Is there a config tweak or something &#21566; &#21487;an &#28858;o?

thanks

---

### Post by fjgaude on 2008-08-13
Do you have a driver that came with the USB sound? If so and you are in Windows, load the driver and then go to VM, Removable Devices, USB Devices and see if the USB is listed.

---

### Post by falkaholic on 2008-08-13
Hi,

I've made it that far. The problem is that onces I attached the USB to a VM, its only on that VM. Not even my host can play sound. Once I stop the VMs and even quit VMware; I dont get sound until I unplug and replug the USB device.

---

### Post by fjgaude on 2008-08-13
Sorry, I've not run into this situation before... maybe others have.

Good luck!

---

