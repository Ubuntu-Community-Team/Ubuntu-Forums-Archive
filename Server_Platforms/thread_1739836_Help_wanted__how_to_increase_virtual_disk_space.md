---
title: "Help wanted | how to increase virtual disk space"
date: 2011-04-26
forum: Server Platforms
---

### Post by lazerz on 2011-04-26
Im using ubuntu as my client machine and running esxi 4.1 on dell server 2850. My image originally is sized as 15 Gb but i want to extend it to 100 Gb which is the available amount given in the actual physical drives attached to the server.

If i try to change the disk space by editing the settings it doesn't change the internal disk space used by ubuntu. ?

Can someone help me how can i change the settings so the virtual disk grows as the capacity of the physical drives increases?

thanks

---

### Post by TheFu on 2011-04-26
> **lazerz said:**
> Im using ubuntu as my client machine and running esxi 4.1 on dell server 2850. My image originally is sized as 15 Gb but i want to extend it to 100 Gb which is the available amount given in the actual physical drives attached to the server.

If i try to change the disk space by editing the settings it doesn't change the internal disk space used by ubuntu. ?

Can someone help me how can i change the settings so the virtual disk grows as the capacity of the physical drives increases?

thanks

This is a VMware question first, before being an ubuntu question.  

The easiest way to add storage to an ESX VM is to add another datastore and connect that to the Ubuntu VM. Then using fdisk, partition the new VMDK as desired. You can add swap if you like or just more normal Linux partitions (EXT3/4, XFS, JFS, whatever).  The fact that you have 100GB of storage in the ESXi machine is good, but you need to make that available to the client OS by creating a VMDK datastore.

Doing this may complicate your backups and many people will want to migrate everything from the old VDISK into a new, larger VDISK rather than having multiple VDISKS attached to a single VM. Your needs will dictate which is best.

For exact steps, I'd google on "esxi increase disk storage" and read a little. Seems there were some ESXi bugs that impacted some of the ways you'd want to increase storage. The specific version of ESX(i) being used matters.

---

