---
title: "Edgy Won't Boot After installing mdadm"
date: 2006-11-20
forum: Server Platforms
---

### Post by igb on 2006-11-20
I have a couple of servers that were running Dapper. Both are configured with  the root partition on its own drive /dev/hda1 and have two additional drives (hdc and hdd)set up as  software RAID1 mirrors.

Today I did an upgrade on both servers. One server was fine, but the other hangs on booting. In an attempt to debug it I wiped hda and installed Edgy server from a CD. This went fine until I apt-get mdadm. The server now hangs during boot and won't even boot in recovery mode.

I am about to try installing from the Alternate CD. In the meantime does anyone know what's going on? I have seen several posts about RAID in Edgy, but none like my problem?

Ian.

---

### Post by Velox Letum on 2006-11-21
I've also had problems with Edgy hanging on boot with Software RAID. As of yet, I've been unable to find a solution.

---

