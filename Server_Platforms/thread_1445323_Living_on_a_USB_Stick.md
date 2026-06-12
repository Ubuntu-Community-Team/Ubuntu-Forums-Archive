---
title: "Living on a USB Stick"
date: 2010-04-02
forum: Server Platforms
---

### Post by Vegan on 2010-04-02
I am aware of the fact that Ubuntu can be installed and booted form a USB stick. No problem.

What I wanted to know is if this year's Ubuntu is smart enough to not trash the USB stick with excessive writes to a specific sector.

While USB sticks are not expensive, if the OS is going to thrash them, it limits its usefulness.

---

### Post by Bachstelze on 2010-04-02
Just don't create a swap and mount /var/log in RAM and you should be fine. If you're really that concerned, use a non-journaling FS like ext2.

---

### Post by DZ* on 2010-04-02
> **Vegan said:**
> What I wanted to know is if this year's Ubuntu is smart enough to not trash the USB stick with excessive writes to a specific sector.

Where stuff gets written on a flash is determined by its controller, not by Ubuntu. Since it doesn't know about things like partitions, wear leveling mechanism will switch data between partitions too.

---

