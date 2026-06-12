---
title: "GFS2 in Ubuntu Server"
date: 2023-12-11
forum: Server Platforms
---

### Post by kladizkov on 2023-12-11
I want to set up a Global File System 2 ( GFS2 ) in Amazon AWS using EBS Multi-Attach using Ubuntu Server. This involves setting up pacemaker, DLM locking, LVM, fencing, AWS elastic IP for cluster IP etc. I'm looking for documentation that covers these. Is there comprehensive documentation on how to go about setting this up?

Please help.

---

### Post by MAFoElffen on 2023-12-12
> **kladizkov said:**
> I want to set up a Global File System 2 ( GFS2 ) in Amazon AWS using EBS Multi-Attach using Ubuntu Server. This involves setting up pacemaker, DLM locking, LVM, fencing, AWS elastic IP for cluster IP etc. I'm looking for documentation that covers these. Is there comprehensive documentation on how to go about setting this up?

I didn't answer this previously... It is just a filesystem used by clusters, that tries to "provide a shared namespace and manage coherency between multiple nodes..." 

I only know that from reading about it. I don't use that personally, but I know there is lots of documentation out there for it.

A quick Google search (let Google metrics be your friend):
[https://manpages.ubuntu.com/manpages/focal/en/man5/gfs2.5.html](https://manpages.ubuntu.com/manpages/focal/en/man5/gfs2.5.html)
[https://documentation.suse.com/sle-ha/15-SP1/html/SLE-HA-all/cha-ha-gfs2.html](https://documentation.suse.com/sle-ha/15-SP1/html/SLE-HA-all/cha-ha-gfs2.html)
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html-single/global_file_system_2/index](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html-single/global_file_system_2/index)
[https://docs.kernel.org/filesystems/gfs2.html](https://docs.kernel.org/filesystems/gfs2.html)
[https://www.linuxlinks.com/gfs2-clustered-filesystem/](https://www.linuxlinks.com/gfs2-clustered-filesystem/)
[https://medium.com/@mezgani/how-to-setup-gfs-on-rhel-e5e031832ae5](https://medium.com/@mezgani/how-to-setup-gfs-on-rhel-e5e031832ae5)
[https://linux-archive.web.cern.ch/scientific6/docs/rhel/Global_File_System_2/](https://linux-archive.web.cern.ch/scientific6/docs/rhel/Global_File_System_2/)
[https://www.techtarget.com/searchdatacenter/tip/Mount-Global-File-System-2-avoid-corruption-in-RHEL-High-Availability](https://www.techtarget.com/searchdatacenter/tip/Mount-Global-File-System-2-avoid-corruption-in-RHEL-High-Availability)
[https://aws.amazon.com/blogs/storage/tag/red-hat-global-file-system-2-gfs2/](https://aws.amazon.com/blogs/storage/tag/red-hat-global-file-system-2-gfs2/)
[https://aws.amazon.com/blogs/storage/clustered-storage-simplified-gfs2-on-amazon-ebs-multi-attach-enabled-volumes/](https://aws.amazon.com/blogs/storage/clustered-storage-simplified-gfs2-on-amazon-ebs-multi-attach-enabled-volumes/)
[https://www.redhat.com/en/blog/bringing-red-hat-resilient-storage-public-cloud](https://www.redhat.com/en/blog/bringing-red-hat-resilient-storage-public-cloud)
[https://blocksandfiles.com/2021/02/18/red-hat-supports-high-availability-apps-in-aws-and-azure/](https://blocksandfiles.com/2021/02/18/red-hat-supports-high-availability-apps-in-aws-and-azure/)

---

