---
title: "disk partition information disappears on guest at shutdown"
date: 2014-10-27
forum: Virtualisation
---

### Post by milkman-the-milk-bar on 2014-10-27
Hello all,

I have an Ubuntu 14.04 host with kvm that also has an Ubuntu 14.04 guest with 3 virtual disks, all in qcow2 format.

I can boot the guest fine, but after I shut it down, it fails to boot again until I recreate the partition information and re-install grub. Has anyone observed this behaviour before and know how to resolve? I've done a few hours of web searching with little success.

I have a Sophos UTM as a guest (linux based) that doesn't suffer from the same problem, so can't quite understand why this is happening.

---

### Post by sudodus on 2014-10-27
Welcome to the Ubuntu Forums :-)

I have KVM + virt-manager system that can preserve Ubuntu guests. It *should* work also for you.

What is happening when you close the system. Could it be, that for some reason the modified file system is not saved properly before it is shut down? Can you notice any difference between the Ubuntu guest and the Sophos guest (at shut down)? Is the virtual disk big enough?

What happens if you run ```
sync
``` before shutdown?

---

### Post by milkman-the-milk-bar on 2014-10-28
Thanks for the welcome!

I ran the sync command and issued a "shutdown -h now", but the partitions disappeared still. So I have to mount the qcow2 image on the host and recreate the partitions:

```
root@bottle-o:/zpool0# qemu-nbd --connect=/dev/nbd0 /zpool0/Zimbra-disk1.qcow2
root@bottle-o:/zpool0# fdisk /dev/nbd0
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x8c5a5586.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```

Eventually add all the partitions back and end up with:

```
Command (m for help): p


Disk /dev/nbd0: 6442 MB, 6442450944 bytes
255 heads, 63 sectors/track, 783 cylinders, total 12582912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xad968f19


     Device Boot      Start         End      Blocks   Id  System
/dev/nbd0p1              63      257039      128488+  83  Linux
/dev/nbd0p2          257040    12578894     6160927+   5  Extended
/dev/nbd0p5          257103    11582864     5662881   83  Linux
/dev/nbd0p6        11582928    12578894      497983+  83  Linux swap / Solaris

```

I then use a rescue cd and get grub back on the disk, and the guest then boots ok. I decided to check what the partitions look like inside the guest, and get this:

```
root@coffeeshop:~# fdisk -l /dev/vda


Disk /dev/vda: 6442 MB, 6442450944 bytes
16 heads, 63 sectors/track, 12483 cylinders, total 12582912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/vda doesn't contain a valid partition table

```

---

### Post by sudodus on 2014-10-28
How are you using that partition? It seems good, but the virtual machine seems to have it set it up in the wrong way.

I use KVM, but must admit, that I am not an advanced user, so I hope someone with more experience will chip in an help us solve the problem.

---

