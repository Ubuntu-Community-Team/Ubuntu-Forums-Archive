---
title: "PXE Benchmark environment"
date: 2011-09-15
forum: Server Platforms
---

### Post by Paul dH on 2011-09-15
Hi there,
 
I've created a syslinux PXE environment within our Windows WDS server and already have a short list of tools in it. But we are looking for a benchmark / stress test tool like Stress linux but with a GUI.
 
My question is, is it posible to build of create a writable usb stick with a small linux distro on it. Then install some tools and place the folders on the PXE server. We then could start the environment with syslinux.
 
Does somebody already have done this, or isn't it possible.
 
Hope to hear, thanks
Paul

---

### Post by haqking on 2011-09-15
> **Paul dH said:**
> Hi there,
 
I've created a syslinux PXE environment within our Windows WDS server and already have a short list of tools in it. But we are looking for a benchmark / stress test tool like Stress linux but with a GUI.
 
My question is, is it posible to build of create a writable usb stick with a small linux distro on it. Then install some tools and place the folders on the PXE server. We then could start the environment with syslinux.
 
Does somebody already have done this, or isn't it possible.
 
Hope to hear, thanks
Paul


There are many ways to do this.

Seeing as you are posting here i presume you mean Ubuntu so :

Ubuntu
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

DSL
[http://www.pendrivelinux.com/all-in-one-usb-dsl/](http://www.pendrivelinux.com/all-in-one-usb-dsl/)

Fedora
[http://fedoraproject.org/wiki/How_to_create_and_use_Live_USB](http://fedoraproject.org/wiki/How_to_create_and_use_Live_USB)

the list goes on ;-) to be able to write to is you need to add a persistant overlay so changes are stored etc.

you can also partition it and use the seperate partition for data storage seperate to the OS itself

---

