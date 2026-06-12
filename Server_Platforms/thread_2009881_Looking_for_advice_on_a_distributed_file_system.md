---
title: "Looking for advice on a distributed file system"
date: 2012-06-25
forum: Server Platforms
---

### Post by atm999 on 2012-06-25
Hi all,

We're looking for advice on what distributed file system to use for a new system. We have been looking at XtreemFS, Ceph, GlusterFS, LusterFS, and MooseFS, although we are open to any suggestions. Does anybody have pros and cons for any of these? 

A little background on our use case: we currently have ~25TB of scientific data in filesizes varying from ~4MB - ~10GB, and are looking for a new way to store it. We have ~200 users managed in an LDAP database, 12 of whom have write access, and the others can only access the data. Because of a new instrument that we just acquired, we will now likely be generating data at a rate of ~20TB/year, and need somewhere to put it where it can be readily accessed by everyone. Most of the people accessing this data will do so over a LAN, but some are off-site and will be connection limited. Latency isn't a huge issue, we care much more about data bandwidth, and if communication between the front-end server and the storage nodes could be encrypted that would be ideal. 

The data should ideally all be accessible from one front-end server, and we are flexible about the backend, but cost is an important factor. Right now we've built one head node and storage node each, with operating systems running on raid1 SSD's, and the storage node having 2 10-drive raidz2 pools (basically raid 6). As soon as we have a distributed FS up and running we'll add a second chunk server. Finally, this is a brand new build that we can afford to mess up as much as we want for testing until the data is migrated over, so feel free to suggest things. 

Thanks for any advice you can offer!

---

### Post by spynappels on 2012-06-25
I did some testing of GlusterFS about a year ago for a project I was working on at the time, and it worked quite well as long as the network links were good, I created 4 x 1 GbE Bonded interfaces for the data connections between storage nodes  and a 4 x 1GbE bonded connection to the backbone switch.

Performance was acceptable, although I never got to do much resiliency testing.

I do remember there were questions about long term stability with large volumes of data stored, but one of the things I found good was that even if Gluster died, you could still access the data stored on individual nodes independently.

I don't know if it was put into production as I left the company shortly after.

I've not worked with the rest, so can't make any comments on those.

---

