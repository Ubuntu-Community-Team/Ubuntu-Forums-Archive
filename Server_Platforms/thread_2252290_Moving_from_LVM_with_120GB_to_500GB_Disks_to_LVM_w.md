---
title: "Moving from LVM with 120GB to 500GB Disks to LVM with 4TB disks."
date: 2014-11-10
forum: Server Platforms
---

### Post by MAFoElffen on 2014-11-10
Planning how to do this hopefully, somewhat painlessly.

I have a 14.04 Server that I started out with a 120GB LVM, that has grown to 5 disks... 120GB through 500GB in size. This box has hot-swap 10 SAS6 slots. I want to replace them all with 4TB drives, so I can grow it smarter. I'm thinking I can probably shrink it down to a single less-than 1TB LVM volume of a single 1TB drive (I have a spare), then what? (ideas) Set up the first 4TB drive as LVM and rsync it to that drive? Then grow it with the other 4TB's? 

The system is also my primary DNS, DHCP, LDAP, KMS and Docker host. But I have a secondary DNS, DCHP and LDAP which be be up while this is down... I also have 2 more identical hardware boxes (Dell Poweredge 2900), which I can fiber channel together... to use to make it easier if need be. 

Ideas?

---

### Post by MAFoElffen on 2014-11-12
Odd, that no-one has any advice on that... lol.

I've been looking through the LVM recipe's. Thinking that instead of doing a vgexport/vgimport, that since I'm trying to move a Root VG, that I'll prep the first new disk with a primary partition for the LVM boot and a partition for the PV to go to, mount the disk and copy the LVM boot partition over from the original old LVM boot partition; install grub to the disk; then use pvmove... That way, it might be a safer course of action(?: hoping)...

---

### Post by MAFoElffen on 2014-11-16
Hit a stumbling block. The 4TB drive would only show on this box as 2TB. Got with Dell Server support and found that the 6i PERC SAS6 RAID controller in this will only support up to 2TB drives. Ordered a smaller drive to start over... 

Actually getting comfortable with pvmove.

Not real comfortable with setting up an LVM Boot from scratch though. I found reference for doing this on an MBR drive. Found reference for setting up grub on Large GPT drives, But did not find much of anything about trying to do both at once. Found that it need At least one bios_boot partition, for grub to install on a large GPT drive, but was having difficulties on just what command structure to point grub to the LVM boot partition... when I found that the drive was just not reporting right on that system... so was having issues on grub not pointing to the right place?

So stalled at the moment.

---

### Post by MAFoElffen on 2014-11-30
Bought 2TB disks.

Partitioned on with 3 partitions:
1 type ef02 bios_boot (unformatted)
2 type 8300 (LVM boot to be mounted as /boot, formatted as ext2 filesystem)
3 type 8e00 LVM

Used pvmove to move all the extends to the 3rd partition on the 2TB drive.
Mounted partition 2 of the 2TB drive and copied all the files over from the old /boot to it.
Used the UUID from the 2nd partition of the new drive and updated the /boot mount in the fstab.
After copying the files, released the mount of that new partition.
Released the mount of the old boot partition from the old drive.
Mounted the new boot partition to /boot
Installed grub. Shut it down. Took out the old drive. Booted right up.

---

