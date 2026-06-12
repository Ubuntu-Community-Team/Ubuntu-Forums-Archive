---
title: "Kali linux VM - no wireless"
date: 2019-04-25
forum: Virtualisation
---

### Post by jjayjohn on 2019-04-25
I need some assistance.

I have ubuntu installed on my laptop. I installed virtual box. I have kali linux running within virtual box. 
My ubuntu OS has wireless working with no issues. However, my kali vm does not have any drivers installed.
I read different online articles talking about compat-wireless2.6. 
However, some sites didn't have the driver to download etc. 

I need some help getting wireless to work in my kali vm.

Can anyone help?

---

### Post by thenailedone on 2019-04-25
Guest OS's in virtualbox connect to the network of the Host OS through a virtual network bridge. The Guest never actually directly connects via the wifi.

---

### Post by TheFu on 2019-04-27
Kali is a hacking tool, which we aren't allowed to help with in these forums.  Best to ask hacking/kali questions elsewhere.

thenailedone is correct, normally the devices presented to a VM are 100% virtual and have very little to do with actual hardware on the host system.  Normally, either virtio or e1000 NICs should be presented for best performance and greatest compatibility regardless of the actual hardware.

The different hypervisors each support 3 types of networking at a minimum.
* bridged
* NAT and
* host-only NAT
You can read up about these in the virtualbox manual: [https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)

The only way to get a wireless device into a VM is to use either PCI or USB passthru. This would remove the device from the hostOS, since only 1 OS can have exclusive access to a device.

---

