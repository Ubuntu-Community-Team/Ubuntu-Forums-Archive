---
title: "mdadm problems: should S25mdadm-raid come later?"
date: 2005-07-22
forum: Server Platforms
---

### Post by monkster on 2005-07-22
This past February in the development forum, Jeff and others agreed that  mdadm was a better way to go than raidtools2. But in the user forums, it seems some folks had trouble getting it going ("software raid5 with mdadm does not survive reboot" in  this forum and "my mdadm issues with sata drives" in Hoary 5.04 Hardware Help).

Its inclusion in Ubuntu being kinda new, I wonder if there are some kinks to work out as far as rcS.d links are concerned?   I have a system here that boots with /var mounted on /dev/md0, which is a 3 SCSI drive raid5 array (with one spare). 

After enabling MAKEDEV to write the /dev/md0 device file by setting auto=yes as an argument to ARRAY in /etc/mdadm/mdadm.conf, I overcame the initial problem I had of /dev/md0 not surviving the reboot.

However, until I moved S25mdadm-raid to S43mdadm-raid--after S40hotplug--the raid5 array would not come up unless I did mdadm -As at the command line. 

I wanted mountall.sh to see /dev/md0, so I moved that from S35mountall.sh to S45mountall.sh.

I think I could have avoided messing with the links in rcS.d if I had used an mdadm command to set up the array elsewhere.

But the question is:  is what I did above (changing the order of  mountall.sh and mdadm-raid) ill advised? Is there an important reason for mdadm-raid to be an S25 link?

---

