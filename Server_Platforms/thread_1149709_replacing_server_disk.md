---
title: "replacing server disk"
date: 2009-05-05
forum: Server Platforms
---

### Post by shayfisher on 2009-05-05
Hello all,

I have a running server (HP computer) which has 2 SATA controllers, on which 4 drives are connected.
drive 1 contains the OS and is connected to ide0.
drive 2 is connected to ide0 also. drive 3 & 4 are connected to ide1.
I have a VG made from drives 2,3 & 4. I'm running out of space in this VG and would like to replace one of the disks with a larger one.

Does anyone know how to move extents using pvmove to another disk over the network (iSCSI ?). I would need to initialize the new large hard drive on another computer because I cannot attach it to the server.
After the extents were moved, Does using vgexport and vgimport would work ?

Thanks in advance for anyone who can help on this.
shay

---

