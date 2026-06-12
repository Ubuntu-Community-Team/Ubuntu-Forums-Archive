---
title: "Need to move VM to physical machine."
date: 2008-03-23
forum: Virtualisation
---

### Post by nagual on 2008-03-23
How would I go about taking an ubuntu server installed in a VM and migrating it to a physical machine.  Any help is appreciated.

---

### Post by talsemgeest on 2008-03-23
I would guess you would be able to do it by copying the files to a partition and then setting up the bootloader

---

### Post by dcstar on 2008-03-24
> **talsemgeest said:**
> I would guess you would be able to do it by copying the files to a partition and then setting up the bootloader

Or copying the VM files into one tar file, and then untaring into a fresh filesystem.

Then you would have to reconfigure the graphics from the VM settings.

---

### Post by HermanAB on 2008-03-24
Actually, I would not do that.  I would install VMware on the new machine and move the VM.  That may, you retain the flexibility.

---

### Post by talsemgeest on 2008-03-24
> **HermanAB said:**
> Actually, I would not do that.  I would install VMware on the new machine and move the VM.  That may, you retain the flexibility.
But they want a full machine, not virtual, which is the point of this thread

---

### Post by mvan83 on 2008-03-28
I would do a live boot on the target machine and from inside of that, partition the disk and create the file systems corresponding to those on the VM. Be sure to run mkswap on the swap partition.

From there, I would tar up the files on the source machine (I prefer to do so for each directory in / since there are some we want to leave out) using
```
tar czvpf root_backup.tgz root/
```

I would exclude proc and sys. However, since these need mountpoints on your target system, be sure to create the directories /proc and /sys on the target machine.

Mount the root partition from within the live boot.
Transfer the tgz files to the live booted target machine and unzip them in the appropriate place using:
```
mount /dev/*root_partition* /mnt/*root_mountpoint*/
```
```
cd /mnt/*root_mountpoint*/
```
```
tar zxvf root_bacup.tgz
```
...

Next, you'll need to copy the MBR from the source machine to the target machine, otherwise it won't be able to even reach grub or lilo. Now, if the VM you are transferring from has a different partition table, you'll need to only grab the first 446 bytes of it. The entire MBR is stored in 512 bytes. (More below).

First, find out which hard disk device you are booting off of:
```
sudo fdisk -l
```

Look at which disk has a bootable partition (indicated by a * under the boot column). Now, say it is /dev/sda1 that is bootable, run:
```
sudo dd if=/dev/sda of=mbr.iso bs=512 count=1
```
Notice how the device used is /dev/sda and not /dev/sda1 .
If you are copying to a target machine with different partitions (and therefore a different partition table), only copy the first 446 bytes:
```
sudo dd if=/dev/sda of=mbr.iso bs=446 count=1
```

Transfer that file to the target machine. Load it on the target machine (using /dev/sda contains your bootable partition on the target machine):
```
sudo dd if=mbr.iso of=/dev/sda bs=446 count=1
``` or:
```
sudo dd if=mbr.iso of=/dev/sda bs=512 count=1
```

Edit the /etc/fstab (remember that is relative to your root mountpoint, e.g. /mnt/*root_mountpoint*/etc/fstab - it's easy to forget when you're in a live boot) file to point them to the new partitions, if you've changed them.

Now you should have something that is bootable at least. I would probably change the xorg.conf file on the target machine to change the driver from "vmware" to whatever it is that is used by that machine (e.g. "nv", "ati", etc.).

The rest should probably just be changing the hardware configurations, which will be specific to your machine.

If you're lucky, that should be all you need. I've actually only done the opposite (p2v, rather than v2p also with RHEL3 instead of Ubuntu, although I imagine this will probably be easier) so there may be new issues here. Post here if you have any trouble or questions about my instructions.

---

