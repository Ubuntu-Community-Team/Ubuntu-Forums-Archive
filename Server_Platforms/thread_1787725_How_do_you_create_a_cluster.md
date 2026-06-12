---
title: "How do you create a cluster?"
date: 2011-06-21
forum: Server Platforms
---

### Post by Sternfan on 2011-06-21
Hi all,
I've recently come into a number of old 1U servers (about 10 or more poweredge 1650s).  Individually they aren't much to speak of, so I thought it would be an excellent opportunity to do a cluster.  

Anyone ever try to make a cluster like this?  I did a google but didn't find much.  

Thanks,
Rob

---

### Post by JonRohan on 2011-06-21
There are a few kinds of clusers, web, storage, db, virtual. 

Did you have anything specific in mind? 

Some links and keywords:
heartbeat

[http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster](http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster)

[http://www.linuxjournal.com/article/5862](http://www.linuxjournal.com/article/5862)

[http://www.howtoforge.com/high-availability-storage-cluster-with-glusterfs-on-ubuntu](http://www.howtoforge.com/high-availability-storage-cluster-with-glusterfs-on-ubuntu)

---

### Post by Sternfan on 2011-06-22
Hi Jon,

I was thinking of using the cluster to run a number of virtualboxes.  That way the options are pretty much endless.  I looked into Xen, but it requires v-t enabled CPUs - which the pe1650s obviously don't have.

My understanding of clusters is this - two basic types - high availability (I think of this as a failover cluster) where one is active and the other passive.  The other type is high-performance - which I guess is what I am shooting for in this case (since an individual pe1650 can't do much).

Thanks,
Rob

---

