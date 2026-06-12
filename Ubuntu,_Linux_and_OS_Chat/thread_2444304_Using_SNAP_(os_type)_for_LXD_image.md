---
title: "Using SNAP (os type) for LXD image?"
date: 2020-05-28
forum: Ubuntu, Linux and OS Chat
---

### Post by ykoehler on 2020-05-28
Hi,

I am exploring the possibility of running LXD within Ubuntu Core.  I can easily install the LXD snap as part of Ubuntu Core, yet, to launch a custom image (not ubuntu) it appears one has to use a tarball.  

Is there support for a snap of type os instead?  Since Ubuntu Core is all about snap, and snap vs tarball at least to me appears to be quite similar (snap being a squashfs compressed image).  

I would hope for something like the example below as to start a LXD container with a rootfs as provided within this SNAP I created of type: os

lxc image import custom_image.snap

---

