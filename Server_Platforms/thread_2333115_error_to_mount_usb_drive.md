---
title: "error to mount usb drive"
date: 2016-08-07
forum: Server Platforms
---

### Post by sed_faster on 2016-08-07
hello everyone,

When I tried mount the usb drive on my ubuntu server 16.04 lts I received this message:
```

sudo mount /dev/sdj1 /media/usb_zap mount: wrong fs type, bad option, bad superblock on /dev/sdj1,
missing codepage or helper program, or other error

In some cases useful info is found in syslog - try
dmesg | tail or so.

```
**Note:** Folder "usb_zap" has permissions only to root!

What did I wrong?
Tanks

---

### Post by Graham_Willis on 2016-08-08
First, does this **dmesg | tail -n50 **return anything relevant (do it immediately after trying to mount USB device)? Second, is this USB device formatted? Does it have any filesystem on it (if yes, what?), are you able to browse it on Windows? And third, are you sure that **/dev/sdj1** is the intended USB device?

---

