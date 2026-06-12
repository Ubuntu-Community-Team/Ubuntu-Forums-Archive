---
title: "KVM Migration Problems"
date: 2011-10-23
forum: Virtualisation
---

### Post by xueliangfei on 2011-10-23
Hi all,
I find this in the docmentation.
Migration requirements
A virtualized guest installed on shared networked storage using one of the following protocols: 
Fibre Channel 
iSCSI 
NFS 
GFS2 
Two or more Red Hat Enterprise Linux systems of the same version with the same updates. 
Both system must have the appropriate ports open. 
Both systems must have identical network configurations. All bridging and network configurations must be exactly the same on both hosts. 
Shared storage must mount at the same location on source and destination systems. The mounted directory name must be identical. 
 
What I am not understand is whether the migrate can only take place based on the shared storage.
If migrate take place in this way, in my  opinion, I think it is not the complete migration.
It is just change the host such as the pointer.
I think the complete migration is "migrate the VM from source host to the destination host and the storge is independent . It is from one storge of source host the another storge of destination host. "
Can anyone help me?

---

### Post by TheR on 2011-10-23
Somo hipervisors have also storage migration option. KVM not at this time.

But it is on a roadmap. Other requirments are correct and migration mostly works. Based on Ubuntu 10.04.

by
TheR

---

### Post by xueliangfei on 2011-10-27
> **TheR said:**
> Somo hipervisors have also storage migration option. KVM not at this time.
 
But it is on a roadmap. Other requirments are correct and migration mostly works. Based on Ubuntu 10.04.
 
by
TheR
 
 
[http://www.linux-kvm.com/content/qemu-kvm-012-adds-block-migration-feature](http://www.linux-kvm.com/content/qemu-kvm-012-adds-block-migration-feature)

---

