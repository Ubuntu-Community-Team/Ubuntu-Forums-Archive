---
title: "RAID 5 Issues - need recovery help"
date: 2008-09-09
forum: Server Platforms
---

### Post by xefialtis on 2008-09-09
I recently created a RAID 5 Array with 3 WD250YS SATA Raid Disks. Everything worked fine, and I copied a ton of data over, and realized that I was going to run out of space.
I purchased another identical disk, added it to the system, formatted it, and then added it to the array.
Then the machine froze. I had to trouble shoot and found that this MoBo suffers from BIOS problems, which I have now fixed.
The trouble is, it was right in the middle of adding the new disk to the array...
Now it does not recognize the array.

I use the MDADM tool, do the scan, etc, and I get this message:
"sudo mdadm --query /dev/md0"
"/dev/md0: is an md device which is not active"

"sudo mdadm --detail /dev/md0"
"mdadm: md device /dev/md0 does not appear to be active."

"resize2fs /dev/md0"
"resize2fs 1.40.8 (13-Mar-2008)"
"resize2fs: Invalid argument while trying to open /dev/md0"
"Couldn't find valid filesystem superblock."

There is a lot of important data on the disk, I can recover the original location if I absolutely have to (I hope), but I was under the impression that the data on a RAID was easy to recover, if I could recover the Array...

PLEASE HELP...
I will give you whatever other information is needed, just ask...I am in need here. I don't want to have to start all over...thanks...

---

### Post by pksings on 2008-09-09
mdadm -QD /dev/md0

and if you are really curious you can look at each device
mdadm -QD /dev/sda1 or
mdadm --examine /dev/sda1

etc...etc.

You may have to assemble it. 
this one is from memory of a couple of weeks so may not be exact.
mdadm  --assemble --force /dev/md0

Or you may have to recreate it, it will know there is data and not overwrite it.

mdadm -C /dev/md1 --level=5 --raid-devices=4 /dev/sda1 /dev/sda2 /dev/sda3 /dev/sda4

This worked for me, showed a spare drive rebuilding and rebuilt just fine.

you can monitor with mdadm -QD /dev/md1

---

