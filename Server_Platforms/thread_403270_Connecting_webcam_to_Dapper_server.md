---
title: "Connecting webcam to Dapper server"
date: 2007-04-06
forum: Server Platforms
---

### Post by sliorda on 2007-04-06
Hi, 
I'm trying to connect a webcam to my dapper server (in order to create a stream later).

After connecting it, the `lsusb` still output only zeros, although `dmesg` says that a new usb is now connected (but without the device's name or function).

1. How can I "automount" the webcam? I believe it is not even recognized by the server.
2. How can I know what driver (kernel module) the webcam needs? the windows' driver is zs211, and I couldn't find any Linux equivalent.

Any help would be appreciated.

---

### Post by ajmorris on 2007-04-06
What model webcam is it?
also go into a Command Line and type ```
sudo mount -a
```
and see if that mounts it.

To automount it you must add an entry to /etc/fstab.

---

