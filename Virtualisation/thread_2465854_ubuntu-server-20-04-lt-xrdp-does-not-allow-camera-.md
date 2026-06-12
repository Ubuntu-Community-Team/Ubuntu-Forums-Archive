---
title: "ubuntu-server-20-04-lt-xrdp-does-not-allow-camera-redirection"
date: 2021-08-13
forum: Virtualisation
---

### Post by yalvarez0002 on 2021-08-13
i would like to know how many people with ubuntu server 20.04 lt or below have managed to redirect their pc camera to their virtual machine by xrdp? i don't understand how to use my laptop camera on the virtual machine by xrdp. any idea that i can do?? yeah I'm using an ubuntu server with graphical interface.

thanks!!

---

### Post by TheFu on 2021-08-13
The virtual machine hypervisor needs to be known. Some support USB passthru better than others.  Why use xrdp at all?  You've lost me there.  SPICE is the fastest protocol for host-to-VM desktop sharing either on the same machine or remotely over the LAN.

---

### Post by MAFoElffen on 2021-08-13
if you are using virt-manager, then in add hardware select add usb host device > select the device > add/update... then it will be passed through.

Note: Once you hardwire that as a pasthrough... Two things will happen. The first is that you will not be able to access it from your host. The second- VM will not start if you unplug it or move it to a different port, because it will not find that hardware asset and error out on startup of the VM. (You would have to remove it from the devices in the virt-manager details or from the domain.xml).

---

### Post by yalvarez0002 on 2021-08-20
[SIZE=3][FONT=arial]]hello, thanks for your contribution. but I forgot to point out that it is a machine in azure.[/FONT][/SIZE]

---

### Post by TheFu on 2021-08-20
> **yalvarez0002 said:**
> [SIZE=3][FONT=arial]]hello, thanks for your contribution. but I forgot to point out that it is a machine in azure.[/FONT][/SIZE]

Way to bury the lead.  Sorry, can't help with Azure.  How do you expect to connect a camera so someone else's data center racks?  This makes no sense.

---

### Post by MAFoElffen on 2021-08-20
So you are talking about an XDRP client on remote access to A cloud instance of Ubuntu? Which specific XDRP client?

---

