---
title: "Desperate: Raid 5 array degraded on main File Server"
date: 2010-10-18
forum: Server Platforms
---

### Post by enigmait on 2010-10-18
Hi,

Really desperate for help on this raid 5 issue.

Came into work this morning and the raid 5 is degraded. Here is the output.

cat /proc/mdstat

md1: inactive sdc2[2](s) sda2[0](s) sdb2[1](s)
      834954048 blocks

md2: active raid5 sdc5[2] sda5[0] sdb5[1]
     29238016 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md0: active raid1 sdc1[2] sda1[0] sdb1[1]
     96256 blocks [3/3] [UUU]

unused devices: <none>

 Doing: mdadm -D /dev/md2 for the raid 5 tells me:

Raid Devices: 3
Total Devices: 3
Preferred Minor: 2

Active Devices: 3
Working Devices: 3
Failed Devices: 0
Spare Devices: 0

If there are no failed devices why isn't the array working?

How can I get the array back up and running please?

---

### Post by enigmait on 2010-10-18
It asks me if I want to start the degraded array and I say yes.

It says not enough operational devices devices for md1 (2/3 failed)

SMART says that the drives are fine.

Can I force the array, what would happen?

mdadm -A /dev/md1 --force /dev/sdc2 /dev/sda2 /dev/sdb2

---

### Post by dtfinch on 2010-10-18
Though I'm fairly inexperienced with mdadm (I haven't had to rebuild a failed one yet), the "(s)" after each partition stands out to me. Failed should be "(F)". Spare would be "(S)" (though it sometimes appears on non-spares). I can't find documentation on what "(s)" means.

Anyway, if it failed those two at different times, it'll help to know which of the two is more up to date when you bring it back up. If you bring it back up with the non-failed disk and the disk that failed first rather than last, and writing happened in between, you would get some corruption.

If I wasn't worried about what "(s)" means, if I were in that situation I might try to bring it back up with only two disks (the unfailed and the most recently failed) and the --assume-clean option if it'd let me, then mount read-only and copy the data off before adding the third normally. And I'd worry about accidentally doing something that would make mdadm think I was adding a new disk and erase it.

---

