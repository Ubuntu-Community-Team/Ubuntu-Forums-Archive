---
title: "Cant set DVD DMA?"
date: 2007-12-20
forum: System76 Support
---

### Post by system77 on 2007-12-20
hi,
It seems I can set the DMA mode for the DVD writer (Pangolin).


hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)


Any idea

---

### Post by thomasaaron on 2007-12-21
Looks like it is a bug that's been around since Feisty.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636)

---

