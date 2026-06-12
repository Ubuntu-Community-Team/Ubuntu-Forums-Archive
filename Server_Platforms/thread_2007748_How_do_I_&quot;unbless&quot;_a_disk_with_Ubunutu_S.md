---
title: "How do I &quot;unbless&quot; a disk with Ubunutu Server installed?"
date: 2012-06-21
forum: Server Platforms
---

### Post by nissarup on 2012-06-21
My server has two disks. One I set up ages ago with a LTS version of Ubuntu server which is no lunger supported. Something happened (don't ask me what) and the system on that disk is unable to boot. I have googled how to fix that particular problem, but haven't found a solution other than reinstalling the system.

Luckily my server has two disks. I installed a much newer version of Ubuntu on the other disk, booted from that disk and copied the data from the old disk. Everything works. Well... Except booting.
When the server reboots fro some reason, it tries to boot from the first disc, and stops.

Is there anyway I can "unbless" the first disc? Make the boot process skip the first disc and jump straight to the second one? Preferably without having to restart the server and mess with the BIOS.

--Nis.

---

### Post by rubylaser on 2012-06-21
The easiest and proper way to do this is to go into your BIOS and change the hard drive boot order.  It's literally a 1 minute job.  Just save your settings after you've changed the order, and you should be ready to go.

---

