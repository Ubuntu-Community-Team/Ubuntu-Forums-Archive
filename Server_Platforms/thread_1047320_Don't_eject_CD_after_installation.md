---
title: "Don't eject CD after installation"
date: 2009-01-22
forum: Server Platforms
---

### Post by cstork on 2009-01-22
Is there a way to prevent the installation CD from being ejected after the installation is complete?  (I want to perform a remote installation and if something goes wrong the first time I'd have to get someone on location to push in the CD again... which would just be ridiculous.)

---

### Post by aaron.d on 2009-01-22
actually, after installation is finished and your computer reboots, the cd tray generally pulls itself in during post. Not sure how this works with slot loads or those spring load locking drives (i dont know what that mechanism is referred to as, but is actually common in servers).

Other than that, I don't know.

---

### Post by Thirtysixway on 2009-01-22
To be honest, I don't remember if the server version ejects the cd.  I haven't installed the server in such a long time.

I looked around for screenshots of the installation
[IMG]http://www.debianadmin.com/images/ubuntulamp/35.png[/IMG]

It almost looks like it asks you to remove it but it doesn't say that it ejects it.  I'm just taking a guess though, I really don't know.

---

### Post by cstork on 2009-01-22
> **Thirtysixway said:**
> 
[IMG]http://www.debianadmin.com/images/ubuntulamp/35.png[/IMG]

It almost looks like it asks you to remove it but it doesn't say that it ejects it.  I'm just taking a guess though, I really don't know.

That's exactly what I thought, when I tried it locally, and I can assure you that the CD was ejected.  (I'm pretty sure that Ubuntu ejected it and not some BIOS routine.)

---

### Post by Dr Small on 2009-01-22
> **cstork said:**
> That's exactly what I thought, when I tried it locally, and I can assure you that the CD was ejected.  (I'm pretty sure that Ubuntu ejected it and not some BIOS routine.)
I installed Debian recently, had a similar screen, and don't remember it ejecting automatically. But, whether it does eject or not, the drive will be pulled back in during POST to read and see if there is something in the drive.

---

### Post by aaron.d on 2009-01-22
> **Dr Small said:**
> I installed Debian recently, had a similar screen, and don't remember it ejecting automatically. But, whether it does eject or not, the drive will be pulled back in during POST to read and see if there is something in the drive.

yeah that's what im saying. It WILL be ejected by Ubuntu umount routine, but during post, the drive is pulled back in in the cases i have seen.

The other thing, however,is that if you changed the BIOS to boot from cd/dvd, it will boot that media again (this is the reason for ubuntu asking for the disk to be removed in the first place). there is an option to boot the first harddisk in that menu, but this is still going to require someone on-site.

---

### Post by redroad55 on 2009-01-22
can you do a pxe install ?

---

### Post by redroad55 on 2009-01-22
or usb ?

---

### Post by cstork on 2009-01-23
> **redroad55 said:**
> or usb ?

Oh, of course that's a great idea.  The only disadvantage is that a CD would be read-only and would give some sense of securty if I have to boot from it again if problems occur later on but that would have been only a nice bonus of the CD solution.  Thanks that helped. :-)

---

