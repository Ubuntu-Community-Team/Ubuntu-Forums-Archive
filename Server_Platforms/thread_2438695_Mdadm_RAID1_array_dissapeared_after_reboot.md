---
title: "Mdadm RAID1 array dissapeared after reboot"
date: 2020-03-16
forum: Server Platforms
---

### Post by gnugradyn on 2020-03-16
Hi! I created a raid1 array using ```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sde /dev/sdf
```

After rebooting, /dev/md0 did not exist. 

I tried rebuilding the array with ```
sudo mdadm --build /dev/md0 --level=1 --raid-devices=2 /dev/sde /dev/sdf
```

This appears to have rebuilt the array, but trying to mount /dev/md0 returns ```
mount: /mnt/plex: wrong fs type, bad option, bad superblock on /dev/md0, missing codepage or helper program, or other error.
```


What should I do?

Update: testdisk finds the ext4 partition and can display its files, but cannot restore the partition with reason ```
Write isn't available because the partition table type "None" has been selected.
```

---

### Post by darkod on 2020-03-17
First of all, it is better to use partitions instead of whole drives in mdadm.

The array did not autoassemble after reboot because you have to put a line in /etc/mdadm/mdadm.conf to make it assemble the array on boot.

If you don't have any important data on the array, I suggest to stop the current array, zero the superblocks on sde and sdf, then make partition on those disks.

After that create a new blank array. Don't reboot right away.

When you complete the above we can talk how to add it to mdadm.conf.

---

