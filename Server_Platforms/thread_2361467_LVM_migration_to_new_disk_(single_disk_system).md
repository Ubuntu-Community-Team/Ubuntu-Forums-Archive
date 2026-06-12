---
title: "LVM migration to new disk (single disk system)"
date: 2017-05-16
forum: Server Platforms
---

### Post by timonoj on 2017-05-16
Hi guys,

I bought a 240GB SSD to upgrade my miniserver, currently at 64GB. With this I hope to host a few VMs within the SSD space. The whole system is installed in an LVM disk. I'd need to replicate this disk on the 240GB SSD. Just doing a backup/restore with acronis and similar didn't work. What would be the way to do this? I saw posts about pvcreate to get the disk formatted to LVM, then vgextend to add it to the cluster, pmove to move the data, then vgreduce and take out the old disk...but this applies in a cluster. Not sure if the procedure is any different when only a single disk involved, and this happens to be the GPT/EFI bootable disk?

Thanks!

---

### Post by darkod on 2017-05-17
I think that process would still apply for the LVM part, but you have to take care about the boot part yourself. Depending how you boot, the second disk will also need to have the EFI partition for EFI boot, or the bios_grub partition for legacy GPT boot.

For the LVM part, I think what you described applies exactly. After creating the boot partitions you need, make the rest one big partition for LVM and add it to the LVM. Then you simply move the used extents from one partition (on the old disk) to another partition (on the new one). Once the old disk has no more used extents, it is safe to take it out of the LVM without losing data.

---

