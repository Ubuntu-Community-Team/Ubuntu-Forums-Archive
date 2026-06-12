---
title: "swarms of servers"
date: 2014-03-09
forum: Server Platforms
---

### Post by Vegan on 2014-03-09
ram sticks have fallen down to < $500 each for 32 GB DDR3 so its possible to stuff a lot of RAM into a given pizza box

I guess my servers will need SAMBA for the LDAP so its possible to keep track of a swarm better

storage is more of a question, with swarms of servers, hard disks, solid state modules and so on become more abstract. I know how to mount storage, that is a basic administrator skill

Over at Microsoft, they have this idea of storage pool, where JBOD is all that is needed, no more RAID cards etc. Linux would be handy for lower cost storage boxes. Cheap controller cards are plentiful.

Ideas to best take advantage of all the resources needed?

---

### Post by nerdtron on 2014-03-09
That is basically the concept behind ceph and glusterfs.
Ceph basically is a highly scalable distributed storage where it treats other computer as nodes, which can be dynamically added or removed from the cluster. Storage is also distributed on all nodes automatically based on its own algorithm and data is replicated to ensure that enough "good copy" of data is present in case any of the nodes or storage drives fail.

---

### Post by LHammonds on 2014-03-11
Keep in mind however that not all storage is created equal.  You still need to clump together storage based on speed of the drives, location, etc.  If your storage needs do not demand high performance and lowest common-denominator is just fine, then no problem.  But if you need to ensure maximum performance for specific applications, you might want to keep various tech separated by type and location (SAS, SATA, SSD, BuildingA over Fiber, BuildingB over CAT5, etc.)

---

### Post by Vegan on 2014-04-12
another issue popped up, what can I do about making the swarm safe and secure 

the recent OpenSSL problem is only one of many things in mind

what can Linux provide for a SSL based web site operating in a workgroup

---

### Post by lukeiamyourfather on 2014-04-14
> **Vegan said:**
> 
Over at Microsoft, they have this idea of storage pool, where JBOD is all that is needed, no more RAID cards etc. Linux would be handy for lower cost storage boxes. Cheap controller cards are plentiful.


Are you referring to Microsoft ReFS? Many of the design features are inspired by ZFS which dates back to 2005 (originally developed by Sun). It has since been ported to other platforms including Linux. ZFS is a much more mature and complete option in my opinion. ReFS has a lot of catching up to do but to be fair ZFS had a long head start.

[http://zfsonlinux.org/](http://zfsonlinux.org/)

> **nerdtron said:**
> That is basically the concept behind ceph and glusterfs.
Ceph basically is a highly scalable distributed storage where it treats other computer as nodes, which can be dynamically added or removed from the cluster. Storage is also distributed on all nodes automatically based on its own algorithm and data is replicated to ensure that enough "good copy" of data is present in case any of the nodes or storage drives fail.

Sort of, Ceph and GlusterFS are distributed storage platforms but they don't handle the underlying file system on each node or redundancy at the node level. Though ZFS can be used as the underlying file system for distributed storage platforms, in fact that's what motivated ZFS on Linux (to be used as a backend for Lustre).

[http://zfsonlinux.org/lustre.html](http://zfsonlinux.org/lustre.html)

---

