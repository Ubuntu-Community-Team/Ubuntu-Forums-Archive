---
title: "Help on install ubuntu server with custom partition"
date: 2009-10-17
forum: Server Platforms
---

### Post by serverCrazy on 2009-10-17
The problem:

I have a server running ubuntu server 8.04, with 5 HDs, 4 of 1TB and 1 500GB. I want to set up a custom partition, i want to install the OS on the 500GB and leave the others to storage (prefirable with RAID 10). Is this possible? How would be the partition. can please someone help with it?

thanks in advance

---

### Post by R.Bucky on 2009-10-17
Never installed a RAID10. However, if you are operating RAID why would you want your OS on a non-RAID drive? If your OS drive dies, then you would have some work ahead of you to link up the RAID again.

---

### Post by Haegin on 2009-10-17
Hey,

It's very much possible, what you probably want to do is to set up the server on the 500GB partition and not worry about any of the other drives for now. The server install CD will take you through partitioning, just select manual partitioning and you can select whatever partition layout you want for your drive. Once the install is complete you can boot into your new server and set up the RAID there. You can then choose how you mount the drives and how you split them up

Of course, some of this depends on whether you are using hardware or software RAID.

---

