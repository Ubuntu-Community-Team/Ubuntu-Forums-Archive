---
title: "mdadm config lost over reboot"
date: 2016-07-28
forum: Server Platforms
---

### Post by karel2 on 2016-07-28
I have two harddisks, on each are 4 primary slices, I wish to make 4 mirrors of them with mdadm. As illustrated, one of these is to become the root volume, but I will noly attack this one when the rest are ok. A second is meant for the swap, the two others are extra filesystems. Only the root must obviously not be erased, the others do not hold any critical data.

This can be set up with no problem, see the mdadm.conf below. However, with the machine running fine and apparently flawlessly, when I reboot only the md0 mirror remains; the other three are lost, their slices are used to build dummy mirrors called md125 md126 md127
It is no problem to destroy these then re-create the desired arrays with mdadm -A but of course I would prefer the config to remain constant across reboots. What am I doing wrong?

Things I tried / checked:
* after correcting the mdadm environment, save config with mdadm --detail --scan >/etc/mdadm/mdadm.conf
* disable udev as described somewhere on this forum
* zero-superblock the slices before creating the arrays to make sure they forget about their (wicked?) past

mdadm.conf:
[I]ARRAY /dev/md0 metadata=1.2 name=suske:0 UUID=4b70921c:f497cfad:a9e89a65:b05ad206
ARRAY /dev/md1 metadata=1.2 name=suske:1 UUID=5be586f3:a0db10cc:356a6001:e7ec6e41
ARRAY /dev/md2 metadata=1.2 name=suske:2 UUID=bdf4143d:527f59d2:696bc13c:0f1d3092
ARRAY /dev/md3 metadata=1.2 name=suske:3 UUID=da6f04fa:5ef1657d:37fcd2b5:8b74a463
[/I]
state of mdadm after reboot:
[I]root@suske:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0]
      61406720 blocks super 1.2 [1/1] [U]
      
md125 : active (auto-read-only) raid1 sdb2[0]
      33535296 blocks super 1.2 [1/1] [U]
      
md126 : active (auto-read-only) raid1 sdb4[1] sda4[0]
      162567104 blocks super 1.2 [2/2] [UU]
      
md127 : active (auto-read-only) raid1 sdb3[1] sda3[0]
      230562176 blocks super 1.2 [2/2] [UU]

[/I]/etc/fstab:[I]
/dev/sda1        /            ext4    errors=remount-ro 0       1
/dev/md1        none            swap    sw              0       0
/dev/md2        /var/shared.local    ext4    rw    0    0
/dev/md3        /vdi.local        ext4    rw    0    0

[/I]

---

### Post by darkod on 2016-07-28
In the ARRAY definition in mdadm.conf try to leave only the /dev/mdX and the UUID. You don't need anything else (like the array name and the metadata version).

It was doing something similar to one of my arrays (renaming it to /dev/md127) and after I did the above it has never done it again. I don't know why, but it seems to work...

Also after creating new arrays and mdadm.conf modification I'm not sure if you needed to run something like:
```
sudo update-initramfs -u
```

That would update the initramfs and doesn't hurt running it i think.

PS. Also in fstab it is better to use the UUID instead of /dev/mdX. That way even if an array is renamed it will still mount it correctly. But note that you need to use the UUID of the formatted filesystem on the array, not the actual array UUID. They are different. You can get all UUIDs with:
```
sudo blkid
```

---

