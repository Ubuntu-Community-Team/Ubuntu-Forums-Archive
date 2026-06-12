---
title: "How to rebuilt a software RAID5 after two members removed"
date: 2012-02-15
forum: Server Platforms
---

### Post by lisinc on 2012-02-15
Hello All -

Please feel free to laugh at my rookie mistake. I had installed Ubuntu 10.04 on a Dell PV 754N with four disks, set up as RAID5 for the main data partition and swap partitions, RAID1 for the boot partition (I believe it was RAID1, going from memory here, it's whatever the system requires as dictated by the installer app). There might have been one more partition but I can't recall.

All was well and the system ran great, sat on the shelf for many months. Today I booted it up and, long story less long, systematically rendered it un-bootable by removing first one, then a second hotswap drive, plugging each back into it's original slot before removing the other. I was thinking that each drive would automatically add itself back to the array. I guess I forgot that it was NOT hardware RAID, which will typically rebuilt automatically. Ubuntu software RAID, as you all know, requires a couple of commands to add back a raid member. Well now I know too.

I had pulled drives 0 and 3 in turn. The system boots to the busybox prompt. Can anyone tell me what commands I need to issue to make the RAID whole again and get this system back up, or am I doomed to start over?

Thanks in advance!
- Ed

---

### Post by bakegoodz on 2012-02-17
I don't think you lost the raid. I think mdadm just needs to go back and discover all the pieces of the raid that is still there. 

try this command: mdadm --assemble /dev/mdx (maybe it's /dev/md1 if the Raid 1 is /dev/md0)

Then you can check it's progress with: cat /proc/mdstat 

Good Luck!

---

