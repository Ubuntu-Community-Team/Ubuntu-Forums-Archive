---
title: "KVM - Cant remote LVM storage pool with virt-manager - mounted partitions"
date: 2014-08-01
forum: Virtualisation
---

### Post by npinn001 on 2014-08-01
Hi there,

So I have virt manager installed on my PC, and I use it to manage a remote server with KVM.

On the server, I have LVM set up on a 250GB HDD, with say 50GB taken up by Root and Swap, the volume group is called vm-vgroup

I added the lvm group to the storage pool, so it now shows my Root and Swap partitions in there, and the free space available to use. I tried to remove this as I wanted to set up just one partition to use for .img files but it wont let me because root and swap are active partitions. Questions are:

Is there anything I can do to remove this from the pool list?

Is this a problem set up this way?

Thanks in advance for your help.

---

### Post by npinn001 on 2014-08-01
Think I found the answer:

When deleting an LVM group-based storage pool, the LVM group definition will be erased and the LVM group will no longer exist on the host system. The configuration is not recoverable and all volumes from this pool are lost. 
 

So looks like I cant remove this. I wonder, if I purge KVM from the host system, and then delete the config files, if I re-install KVM would this solve it do you think?

Or is it a clean install of the Ubuntu host?

---

