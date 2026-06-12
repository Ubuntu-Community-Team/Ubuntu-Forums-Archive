---
title: "LVM Reduce Simply"
date: 2009-12-17
forum: Server Platforms
---

### Post by meggawhat on 2009-12-17
Shrink a Logical Volume

In the code below, replace volgroup and logicalvol with the volume group and logical volume names on your machine. lvmdisk scan will tell you what the names are, and how many GB are there.  resize your filesize to match the physical drive GB you want to move the actual data to.  Then you can move the data off the drives with pvmove and un-LVM them with vgreduce.

Then you can drop in those 2 new TB drives and reverse the process.

To shrink a LV first

umount the LVM, if the LVM is mounted as /home, log on as root after a
fresh reboot and
_umount /home_

scan
_lvmdiskscan_

check
_e2fsck -f /dev/volgroup/logicalvol_

resize the file system to the desired size
_resize2fs /dev/volgroup/logicalvol 400G_

reduce the LV by the desired size
_lvreduce -L -750G /dev/volgroup/logicalvol_

move the data off the drives you want to remove
_pvmove -v -/dev/mda7_

remove a physical volume from the volume group in this case 'md7' a raid drive
_vgreduce volgroup /dev/md7_

---

