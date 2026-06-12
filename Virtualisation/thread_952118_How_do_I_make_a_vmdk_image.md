---
title: "How do I make a vmdk image?"
date: 2008-10-18
forum: Virtualisation
---

### Post by josephellengar on 2008-10-18
or a vdi- I just need some software or utility to make a virtual disk image.  I can't believe that this is so difficult.

---

### Post by theojepsen on 2009-05-04
I managed to create an image with Qemu.

```
sudo apt-get install qemu
```
and then
```
qemu-img create -f vmdk  myimage.vmdk 4GB
```
creates a 4GB vmdk.

Hope this was helpful.

---

