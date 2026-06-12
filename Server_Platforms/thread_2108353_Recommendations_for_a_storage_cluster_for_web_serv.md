---
title: "Recommendations for a storage cluster for web server farm."
date: 2013-01-24
forum: Server Platforms
---

### Post by bobsta63 on 2013-01-24
Hi guys,

Just wanted some advice really, I'm in the process of setting up a highly available web hosting platform, at the frondend I currently have two servers running HAProxy and Heartbeat which acts as a fault tolerant load-balancer to distribute load to the four web servers behind (in a round-robin LB configuration). - This setup is working great!

For the database (MySQL) I will create a MySQL cluster using NDB etc. - Which I'm happy to set-up and configure!

However I'm kinda stuck on what to do with the storage, obviously I could use a standard NFS server and have each of the web servers mount the shared NFS export folder however having a single storage server kinda makes the entire platform a waste of time, so I need to ensure that I can loose a storage node or two also... I've seen documentation online about setting up NFS & DRBD but also see that GlusterFS may be better for my requirements.

I'd love to know what you guys would recommend for a storage cluster, I'm assuming that GlusterFS is the way to go?

Cheers,
Bobby

---

### Post by bobsta63 on 2013-01-25
If no one can make any direct recommendations maybe someone wouldn't mind sharing how they currently have their shared storage environment set-up? Please??

---

### Post by Habitual on 2013-01-25
Bobby:

I read this post yesterday but refrained from "cheerleading" on the subject of Gluster|glusterfs.

I have used it successfully and as expected over at cirrhus9.com
It's pretty easy and behaved as I expected.

I only have the instructions|cheats|notes|recipe for configuring Two CentOS 5.7/x86_64 hosts and the gluster (v3.2.5) filesystem.

Good luck!

---

