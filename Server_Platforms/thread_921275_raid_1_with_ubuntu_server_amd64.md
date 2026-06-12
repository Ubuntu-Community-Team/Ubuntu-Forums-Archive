---
title: "raid 1 with ubuntu server amd64"
date: 2008-09-16
forum: Server Platforms
---

### Post by tumandro on 2008-09-16
Hello,

I am currently reinstalling ubuntu on a server that I am running and I'm having problems with the partitioner in the install set up. I'm trying to set up a software raid on the hd's with 4 partitions. I create the partitions exactly the same on both drives as follows:

#1 primary 1 GB Swap
#2 primary 296.1MB raid
#3 primary 100GB raid
#4 primary 398.8GB raid

My problem is that when I try to do the configure software raid option, then go to create new md device, the install disc has already set up 4 raid 1 devices, each one being a seperate partition on the hard drive (IE: I'll have two 100 GB software raid devices). When I try to delete the devices so that they will show in the selection for raid, it claims that they are currently in use and cannot be deleted.

I've tried using the mdadm command to delete the devices, but nothing seems to work. Anyone have any ideas?

EDIT: Found out the solution right after typing this. Have to use the command mdadm --stop /dev/mdX. Hope that helps anyone else who has this issue.

---

