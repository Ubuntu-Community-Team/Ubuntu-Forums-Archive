---
title: "Migrating to a USB"
date: 2010-02-07
forum: Server Platforms
---

### Post by Iker Etxebarria on 2010-02-07
Hi

I would like to install Ubuntu server on a hard disk and clone it to a USB to get it running from a pendrive. ¿Is it possible? How could I do that?

Thanks

---

### Post by Vegan on 2010-02-07
I installed Linux from CD to a USB stick, no problem. It runs fine, so I use it to fix dead machines.

---

### Post by BkkBonanza on 2010-02-07
You can just boot on the Ubuntu CD and insert your USB stick. When it asks about where to install and partitioning etc. just choose the USB stick for the destination. Typically that would be /dev/sdb but it depends on what other devices are in the system.

You can also do this without burning a CD. Use VirtualBox to start up the Ubuntu iso image. Make sure the USB stick is mounted in the USB controls for the started VM and then install from the VM to the USB stick. Works the same way.

---

### Post by Vegan on 2010-02-07
I have used Ubuntu for a long time on a USB stick, and I have had no problems.

9.10 seems to able to live on a USB stick fine.

---

