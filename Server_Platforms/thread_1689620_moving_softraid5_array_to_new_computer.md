---
title: "moving softraid5 array to new computer"
date: 2011-02-17
forum: Server Platforms
---

### Post by sjhupp on 2011-02-17
Hi, hoping for some guidance please.
I have a home media server with raid5 and wish to move all the drives to a new motherboard.  I'm fairly sure I'll end up with different sd[abcd..] for each drive, so wanting to understand what I need to do in preparaiton.  I may not have enough room to backup all the data, though I will first get the most important stuff copied off.
I installed mdadm on the new computer in preparation.
I have only 3 sata drives currently forming md0 array.
Once moved physically, do I reassemble the array?
current conf:

cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=eee3305c:36550fc5:ccd38b8e:ced81dc6

# This file was auto-generated on Sat, 04 Sep 2010 16:38:25 +1000
# by mkconf $Id$

Should I be ok with UUID defined here?
Thanks.

---

