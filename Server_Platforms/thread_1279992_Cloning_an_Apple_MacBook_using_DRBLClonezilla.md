---
title: "Cloning an Apple MacBook using DRBL/Clonezilla"
date: 2009-10-01
forum: Server Platforms
---

### Post by waspinator on 2009-10-01
Hi,

I have successfully installed ubuntu 9.04 and configured drbl/clonezilla. My setup works for creating and delivering images to my windows/ubuntu computers (PCs), but my MacBooks won't boot. I hold down the 'N' key to initiate a network boot, and I see the flashing globe, but it just boots from hard disk after a couple of minutes. 

From what I read, Apple uses EFI instead of BIOS, and therefore does not have PXE. Instead it uses NetBoot, and that requires the use of boot service discovery protocol (BSDP). 

Is there a way for me to boot my Macbooks using ubuntu and drbl or do I have to get a mac server to do this?

Thanks

Waspinator

---

### Post by bjslights on 2009-11-10
I too would love to know if this is possible.  I'd rather not have to image our Mac labs with the clonezilla live CDs.

---

### Post by SlappyPappy on 2009-11-28
This is a great question. I'm trying to do this as well.

I've got Macs that we have to clone via the Clonezilla CD and it's a pain to have to do so many computers.

If anyone has details on how to get this going please post.

Thanks.

---

### Post by steelsteel on 2010-06-19
Hello! Im trying to use MacBook1,1 with DRBL/CloneZilla, too.

The DRBL Server is up and running - tested with a normal pxe-bootable vm.
But the Macbook (started even with DRBL's etherboot-net.zlilo) wont work.

Please help!

---

