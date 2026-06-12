---
title: "Can't see usb devices in vmware"
date: 2010-03-04
forum: Virtualisation
---

### Post by luke0927 on 2010-03-04
Hello, I'm a vm newbie and have tried ubuntu 9.04/10 and mepis 8.0 I can not get any of them to see a usb device once its plugged into the host machine not sure if its a linux thing or vmware?  vmware says the usb controller is present.  any thoughts on my regular box it will auto mount my usb stick?  here is a lsusb output.

mepis1:~# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mepis1:~#


any thoughts?


EDIT guess I should play around a little more before posting if your usb is already plugged in when the VMware starts you have to manually add it but if you have the VM up then plug in the USB it will see it.

---

### Post by dcstar on 2010-03-05
> **luke0927 said:**
> Hello, I'm a vm newbie and have tried ubuntu 9.04/10 and mepis 8.0 I can not get any of them to see a usb device once its plugged into the host machine not sure if its a linux thing or vmware?  vmware says the usb controller is present.  any thoughts on my regular box it will auto mount my usb stick?  here is a lsusb output.

mepis1:~# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mepis1:~#


any thoughts?


EDIT guess I should play around a little more before posting if your usb is already plugged in when the VMware starts you have to manually add it but if you have the VM up then plug in the USB it will see it.

Please refer to the threads at the top of this forum.

---

### Post by Exca on 2010-03-10
> **luke0927 said:**
>  
EDIT guess I should play around a little more before posting if your usb is already plugged in when the VMware starts you have to manually add it but if you have the VM up then plug in the USB it will see it.
 
Hello luke0927,
 
Did you solved this issue ?
 
If you're using VMWare server, dont forget to add as usb port to your config.
[IMG]http://sychlora.dvrdns.org/images/vmw_hardware.png[/IMG]
 
When the virtual machine is started, go to your vmware infrastructure web client (in my case, vmware infrastructure software on windows don't allow user to connect a host USB).
Clic on your VM, and you'll see near the start/stop buttons, a usb button (this button only appears when the VM is up).
[IMG]http://sychlora.dvrdns.org/images/vmw_usbplug.png[/IMG]
 
VMWare seems to update automatically the USB devices list you can connect to your VM.
 
Good luck, and sorry if I'm out of the subject ;)

---

