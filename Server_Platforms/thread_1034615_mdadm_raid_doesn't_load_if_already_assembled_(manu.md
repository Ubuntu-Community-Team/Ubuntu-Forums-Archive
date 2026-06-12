---
title: "mdadm: raid doesn't load if already assembled (manual assembly required)"
date: 2009-01-08
forum: Server Platforms
---

### Post by stokkes on 2009-01-08
This is related to my reply to this post: [http://ubuntuforums.org/showpost.php?p=6518638&postcount=21](http://ubuntuforums.org/showpost.php?p=6518638&postcount=21)

I decided to create my own thread since I've narrowed down the problem..

**Situation:**
3x1.5TB Seagate drives in a raid5 config (/dev/md1).

**Problem:**
If I assemble the array (or put the ARRAY line in /etc/mdadm/mdadm.conf), the raid will **not** start and the partitions (/dev/sda1, /dev/sdb1, /dev/sdc1) **do not appear in /dev**. The only way for me to get them to appear in /dev is to do a /sbin/blockdev --rereadpt /dev/sda (sdb,sdc).

*However*
If I stop the array (mdadm --stop /dev/md1), remove the ARRAY line in mdadm.conf and re-initialize initramfs (update-initramfs -k all -c), the partitions **do show up in /dev/** and I can re-assemble the raid (mdadm --asssemble /dev/md1 /dev/sda1 /dev/sdb1 /dev/sdc1) and then mount it.


Anyone have any ideas why this is happening? I have two raids (my boot raid is made up of 2x320GB WD drives) and works fine, but this raid doesn't... :(

---

### Post by Cracauer on 2009-01-09
Please post /proc/mdstat from all these states.

---

