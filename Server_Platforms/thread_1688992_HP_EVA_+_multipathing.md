---
title: "HP EVA + multipathing"
date: 2011-02-16
forum: Server Platforms
---

### Post by Skoude on 2011-02-16
Okay fellows.. I'm loosing my nervers here..

I'm trying to install Ubuntus Server 10.10 on HP Proliant BL460C G7 blade server with HP Eva 4400 SAN storage.. The problem is that I don't know how can I enable multipath.. 

Now i see all the paths as separate device: 
root@ETLMASTER:/# lsscsi
[0:0:0:0]    storage HP       HSV300           0953  -
[0:0:0:1]    disk    HP       HSV300           0953  /dev/sda
[0:0:1:0]    storage HP       HSV300           0953  -
[0:0:1:1]    disk    HP       HSV300           0953  /dev/sdb
[1:0:0:0]    storage HP       HSV300           0953  -
[1:0:0:1]    disk    HP       HSV300           0953  /dev/sdc
[1:0:1:0]    storage HP       HSV300           0953  -
[1:0:1:1]    disk    HP       HSV300           0953  /dev/sdd


and fdisk  shows:

root@ETLMASTER:/# fdisk -l

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9019

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1244     9990144   83  Linux
/dev/sda2            1244        1306      492545    5  Extended
/dev/sda5            1244        1306      492544   82  Linux swap / Solaris

Disk /dev/sdb: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9019

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1244     9990144   83  Linux
/dev/sdb2            1244        1306      492545    5  Extended
/dev/sdb5            1244        1306      492544   82  Linux swap / Solaris

Disk /dev/sdc: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9019

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1244     9990144   83  Linux
/dev/sdc2            1244        1306      492545    5  Extended
/dev/sdc5            1244        1306      492544   82  Linux swap / Solaris

Disk /dev/sdd: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9019

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1244     9990144   83  Linux
/dev/sdd2            1244        1306      492545    5  Extended
/dev/sdd5            1244        1306      492544   82  Linux swap / Solaris




But I should see this all as one device.. I installed the multipath package from apt, but I really don't undestand how to configure it correctly.. Does anybody know any good tutorial for this?

---

### Post by Skoude on 2011-02-16
Okay I got this solved.. It was too easy.. Just install clean system, log in. Run sudo apt-get update
then: sudo apt-get install multipath-tools multipath-tools-boot

then just restart

After logging in run: sudo apt-get dist-upgrade  

Just make shure that when installing system first install the multipath, restart and then run the dist-upgrade.. Otherwise it won't work.

---

### Post by pnkiller78 on 2011-03-15
Hi, I have BL460c G6 with a QLogic QMH2562 8Gb FC HBA. My EVA has dual controllers so the LUNs can be seen 4 times on each server.
I created a 30GB disk on EVA and presented to the host, configured the hba to boot from SAN.
After that, I installed ubuntu 10.10 amd64, and tried what you suggested, but the OS still shows me the 4 30GB HDD.
Did you used the x86 distro or the amd64 distro?

---

