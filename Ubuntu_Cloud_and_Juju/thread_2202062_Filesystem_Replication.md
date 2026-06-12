---
title: "Filesystem Replication"
date: 2014-01-27
forum: Ubuntu Cloud and Juju
---

### Post by gopukrishnan on 2014-01-27
Hi all,

I would like to replicate two web-ervers servers (Ubuntu) which is hosted in Rackspace. Currently I use mysql master-master replication between the two servers (database replication). Please suggest me a better tool for the files replication. Currently I am using GlusterFS and facing some difficulties especially after one server reboot. Please suggest me a better tool for the files replication.

Thanks,

---

### Post by TheFu on 2014-01-30
There is a huge range of requirements about replication.  GlusterFS is a block-level method. There are others, but these might not be the best solution for any specific problem.
You've outgrown rsync and simply need quicker replication or really want synchronized writes to geographically separate locations to minimize data loss, at the expense of performance?  

You probably know this, but when I'm looking for alternative tools, I use a few tricks to find them, then ask for comments about each (showing that I did my homework) at my LUG and on forums.

* [http://alternativeto.net](http://alternativeto.net) - they didn't have anything this time.
* freecode.com - nothing useful that I saw. Didn't search too hard.
* Google with "glusterfs vs" ... to see options.
This last search brought back lots of options.
** DRDB
** Ceph
** FhGFS
** ZFS  - this seems out of place to me, but perhaps they use snapshots and zsend to the remote storage?
** lustre

---

