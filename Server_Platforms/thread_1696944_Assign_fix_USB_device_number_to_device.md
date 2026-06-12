---
title: "Assign fix USB device number to device"
date: 2011-02-28
forum: Server Platforms
---

### Post by geohei on 2011-02-28
Hi.

I need to configure USB bus and device permanently into a config file of a binary. However, Ubuntu 10.04 server reassigns the device number differently at startup (not always, but sometimes ... scheme not detectable). This requires later on manual change of the config file.

```
root@vm90:~# lsusb
Bus 002 Device 004: ID xxxx:xxxx my_device_1
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID xxxx:xxxx my_device_2
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

How can I tell the server to always use a user defined device number for a specific device?

Thanks,

---

### Post by geohei on 2011-03-01
Hi.

In other words ... is it possible to lock the USB device number to a certain value during boot?

Thanks,

---

