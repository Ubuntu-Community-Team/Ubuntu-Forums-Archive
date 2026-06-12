---
title: "Ubuntu Server 14.04 Swapped ethernet device, no ethx."
date: 2015-02-28
forum: Server Platforms
---

### Post by mattlach on 2015-02-28
Hey all,

So I have Ubuntu 14.04 running as a guest on an ESXi virtualized server.

Previously I was using the E1000 network emulation on this guest, but I now have a need for more than gigabit bandwidth, so I swapped it from e1000 to VMXNET3.

I have other guests that use VMXNET3 fine, but they were installed that way from the beginning.

When I swapped the device to VMXNET3 and rebooted, I have no ethx devices anymore.   (previously I had a single eth0)

I have confirmed that the vmxnet3 module is loaded.

On older server versions I would have confirmed that the new device was discovered in /etc/udev/rules.d/70-persistent-net.rules, and edited /etc/network/interface accordingly.

It would appear - however - that with the new version of udev, /etc/udev/rules.d/70-persistent-net.rules no longer exists.

Based on this, other than confirming that the module is loaded, I have no idea where to start my trouble shooting now.

Can anyone suggest where I might need to look?

Thanks,
Matt

---

### Post by mattlach on 2015-02-28
Well,

I switched back to e1000 and restored the image from a backup, and then switched back to VMXNET3 again, and this time it works.   Weird.

So, I no longer have a problem, but, how would one go about troubleshooting situations like this now that /etc/udev/rules.d/70-persistent-net.rules no longer exists?  Any thoughts?  This might be good to know in the future.

---

