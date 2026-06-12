---
title: "Using sfdisk on VDI fixed-size image"
date: 2009-03-20
forum: Virtualisation
---

### Post by przemoc on 2009-03-20
Hi,

I created simple shared library for sfdisk to fool him on VDI fixed-size images. The idea was to make VDI header somehow invisible for sfdisk. Name of my nano-project is vdiwrap.

If you're interested why exactly I created vdiwrap:
[Using sfdisk on VDI fixed-size image](http://news.przemoc.net/2009/03/using-sfdisk-on-vdi-fixed-size-image.html)

If you're interested in technique, which I have used for skipping VDI header in sfdisk:
[Interposing System Calls](http://troves.przemoc.net/2009/03/interposing-system-calls.html)

If you're interested in vdiwrap alone:
[vdiwrap.c](http://wiki.przemoc.net/snippets/c#vdiwrap.c)

No warranty. Use it at your own risk!

Example of usage can be found here:
[Mounting partition from VDI fixed-size image](http://wiki.przemoc.net/tips/linux#mounting_partition_from_vdi_fixed-size_image)

---

