---
title: "NON DESTRUCTIVE JFS expand"
date: 2008-10-16
forum: Server Platforms
---

### Post by anystupidname on 2008-10-16
I need to expand a JFS partition with important data on it that I cannot lose.

I have a 120GB drive with a partition on it with about 50GB of virtual machines on it. They used to be on EXT3. I used gparted to resize the ext3 partition to half the drive, then I created a JFS partition on the other half and I moved all the data over. I deleted the EXT3 partition and wanted to expand the JFS partition to use the entire drive again but gparted won't let me. Any help would be much appreciate!

You're supposed to be be able to use fdisk to delete the partition boundaries, recreate a partition using the larger area, write the changes, and then expand JFS with the funky command:
mount -o remount,resize /mount/point

That was ineffective for me (actually, it hosed the drive temporarily - thankfully, testdisk saved me)

Strangely enough, Gparted let me expand it normally after testdisk fixed it and a reboot...

---

