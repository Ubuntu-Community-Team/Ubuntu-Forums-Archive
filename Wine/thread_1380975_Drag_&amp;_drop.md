---
title: "Drag &amp; drop"
date: 2010-01-14
forum: Wine
---

### Post by kdkolhapur on 2010-01-14
Dear All,
I am new to Ubuntu. I dare to install UBUNTU 9.10 on my desktop PC in Windows XP as a dual OS. I installed Wine Software to run Photoshop CS. It Run Successfully. But I can't Drag and Drop the Images from File browser. Please Help me to enable the drag and drop Utility.
REGARDS.

---

### Post by arubislander on 2010-01-14
Hi... I don't think it's possible to drag from nautilus and drop in a wine window...

---

### Post by kdkolhapur on 2010-01-14
> **arubislander said:**
> Hi... I don't think it's possible to drag from nautilus and drop in a wine window...
Thanks for your suggestion.
I tested Photoshop CS on Ubuntu with the help of wine. It works faster than Windows XP. But some bugs are there. When I close the Image in Photoshop, it get close but it left gray patch on screen. Might be the problem of virtual memory like Windows XP.
REGARDS.

---

### Post by dacha on 2010-01-19
> **arubislander said:**
> Hi... I don't think it's possible to drag from nautilus and drop in a wine window...

It is already possible, for Windows apps that use WM_DROPFILES. Photoshop uses OLE instead, so it doesn't work. See [http://wiki.winehq.org/DragAndDrop](http://wiki.winehq.org/DragAndDrop)

There is a patch at [http://www.winehq.org/pipermail/wine-patches/attachments/20070702/72a45183/dnd-0001.bin](http://www.winehq.org/pipermail/wine-patches/attachments/20070702/72a45183/dnd-0001.bin) you can try to compile Wine with for OLE drop support. Your mileage may vary.

---

