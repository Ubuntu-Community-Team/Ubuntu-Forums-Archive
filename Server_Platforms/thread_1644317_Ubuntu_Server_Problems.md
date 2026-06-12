---
title: "Ubuntu Server Problems"
date: 2010-12-13
forum: Server Platforms
---

### Post by ameanberg on 2010-12-13
I tried installing Ubuntu 10.04 AMD64 Server Edition on my Presario SR1910NX ([Specs]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00680695&jumpid=reg_R1002_USEN"))
So I installed it with GRUB and after installing it just showed a black screen after showing a thing or two on the command line. Than I tried installing Ubuntu 10.04.1 I386 Server Edition with GRUB and it showed GRUB and than, once again, a black screen.
Anyone got any suggestions?

---

### Post by elico on 2010-12-13
you can erase the mbr of the drive using rescue disk mode and then reinstall the os.
        dd if=/dev/zero of=/dev/hda bs=440 count=1 

will make the basic thing you need without erasing the partitioning stuff.
        dd if=/dev/zero of=/dev/hda bs=512 count=1 

will give you full mbr erasing and also will make your partitioning "blank".

---

### Post by CharlesA on 2010-12-13
> **elico said:**
> you can erase the mbr of the drive using rescue disk mode and then reinstall the os.
        dd if=/dev/zero of=/dev/hda bs=440 count=1 

will make the basic thing you need without erasing the partitioning stuff.
        dd if=/dev/zero of=/dev/hda bs=512 count=1 

will give you full mbr erasing and also will make your partitioning "blank".
That won't fix the problem.

Sounds like it doesn't like your video card.

---

### Post by elico on 2010-12-14
well you are right about the screen thing.
but i dont now what exactly the computer shows and what not.
if you can get into rescue mode and change the graphic settings for grub it could help a lot.
(sorry if i got you the wrong direction im humen and sometimes im off the hook)

---

