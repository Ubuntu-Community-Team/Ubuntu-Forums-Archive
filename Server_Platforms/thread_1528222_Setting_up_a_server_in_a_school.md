---
title: "Setting up a server in a school"
date: 2010-07-10
forum: Server Platforms
---

### Post by dleik on 2010-07-10
Newbie here.  We are planning on converting our school to Ubuntu 10.04 from Windows (small school).  I have most of it figured out, but I am struggling with 2 areas : 

File service Folder Security : I have created groups, but they don't appear to be accessible when I go to assign them to a folder.

Thin Client : I have Dell GX110s that I want to use a thin clients.  Anyone had success on creating a bootable CD for them?

Thanks

---

### Post by Bachstelze on 2010-07-10
> **dleik said:**
> 
Thin Client : I have Dell GX110s that I want to use a thin clients.  Anyone had success on creating a bootable CD for them?

Generally, thin clients are booted from the network, not from a CD.

Have you looked at Edubuntu?

---

### Post by dleik on 2010-07-10
> **Bachstelze said:**
> Generally, thin clients are booted from the network, not from a CD.

Have you looked at Edubuntu?

Yes.  My plan is to have Edubuntu as the server and connect the thin clients to it.  The reason I'm looking for a CD boot is because the network cards don't support PXE boot.  I have some laptops that support PXE network boot, so I have tested that it works correctly.  For the desktops that don't support PXE network boot, there are solutions that allow you to create a CD which will emulate a PXE boot.  I'm wondering if anyone has done that before?

---

### Post by swMan on 2010-07-21
Dleik,

This site make bootable floppy disk/CD. The floppy/CD will connect to PXE server. It emulates a network card boot rom. After boot, it connect to PXE server. 
[http://www.rom-o-matic.net/gpxe/gpxe-1.0.1/contrib/rom-o-matic/](http://www.rom-o-matic.net/gpxe/gpxe-1.0.1/contrib/rom-o-matic/)

at "1. Choose an output format:",  select 
Floppy bootable image(.dsk) = bootable Floppy diskette
ISO bootable image(.iso)  = bootable CD

at "4. Generate and download an image:",
click "get image" and download the file. Then write the image to floppy(dsk image) or CD (iso image)

---

