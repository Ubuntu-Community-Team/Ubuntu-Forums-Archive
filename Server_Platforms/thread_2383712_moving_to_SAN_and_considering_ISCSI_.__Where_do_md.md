---
title: "moving to SAN and considering ISCSI .  Where do mdadm, lvm and LUKS fit ?"
date: 2018-01-28
forum: Server Platforms
---

### Post by rperkins on 2018-01-28
Hello

For for a long time I've had a fileserver utilizing NFS, LVM and mdadm. Recently purchased a used 1U rack server that has much more processing power not many bays.  Have ordered some used 10Gb SFP network cards and plan to direct connect the fileserver with the rack server.  No SFP switch.  Latest Ubuntu LTS

Will be used for file serving ( movies, documents, photos, etc ) and also storage for VM images ( I use kvm/libvirt/virt-manage )
The drives currently consist of qty4 spinning drives in a (mdadm) RAID10  and 2 SSD probably in a raid0.

Ok so much for my setup .  here are my questions

1. Been reading about the different solutions for SAN and am leaning towards ISCSI .  am open to comments/suggestions if there are better solutions
2.  Can the LVM /mdadm be constructed on the iscsi  target and then export the /dev/mdx ?  should it be done that way ?
3.  where would LUKS encryption fit into this setup ?  can this be on the target also or does it need to be on the initiator ?
4. is it completely off target to do all this on the fileserver ( target ) and provide the LUKS password upon boot and have iscsi export the (un)encrypted device ?

Maybe someone can point me to a typical recipe for a configuration like this.

I've been doing a lot of reading ( and backing up :-) )waiting for my parts to come in 
thanks in advance

---

