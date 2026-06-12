---
title: "SAN storage device"
date: 2008-12-16
forum: Server Platforms
---

### Post by quel on 2008-12-16
is there any possibility to mount / add SAN storage device with Fibre Channel to the Ubuntu Server ?

(Promise Technology VTrak E310f)

---

### Post by wirelessmonkey on 2008-12-16
Yes, iSCSI is what you're going to need to be reading about.

---

### Post by quel on 2008-12-17
thank you for reply.
i will check that solution :)

---

### Post by PilotJLR on 2008-12-17
If you already bought this promise array, then I don't see how iSCSI could be an option.

You'll need to purchase fibre channel HBA's for your Ubuntu server in order to see this storage.

If you haven't already bought this array, then I'd second the notion to go with iSCSI attach instead. This array won't even come close to being able to max out iSCSI or FC throughput. FC, though, is much more expensive. HBA's can be 1k a pop, and you should really have 2 of them.

---

### Post by Ferret-Simpson on 2008-12-20
I recommend 2Gb/s PCI-X cards at the moment. You can usually pick up Single 2Gb Qlogic cards second-user for about £30.

---

### Post by windependence on 2008-12-21
Check out FreeNAS.

Supports iSCSI, NFS, SAMBA and other mounts and you can build one out of an old PC or a MiniITX board and some hard drives.

-Tim

---

### Post by ALAA_AA on 2009-05-20
> **quel said:**
> is there any possibility to mount / add SAN storage device with Fibre Channel to the Ubuntu Server ?

(Promise Technology VTrak E310f)

Hello, 
As a reply to your question . Yes you can mount / add SAN storage device with fibre channel to the ubuntu server. 
You'll need an external storage with their controlers
you'll need a FC HBA card ( for example qlogic) on your server.
//if you have FC switches , make sure that your zonning is working well, and that your server and you storage are in the same domain. moreover, most of the FC HBA drivers are already in ubuntu , you load them to the kernel (if they are not loaded) with modprobe , and then you create your partitions and then mount them ...  :-) 

Good luck 

Alaa

---

