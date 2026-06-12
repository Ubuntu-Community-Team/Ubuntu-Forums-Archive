---
title: "Stateless Cluster setup"
date: 2016-02-02
forum: Server Platforms
---

### Post by extremis11 on 2016-02-02
I have followed this tutorial:

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

I have already set up the server and client node and everything works just fine; i am running Ubuntu Server 14.04.3. I would like to add more client nodes to the Cluster, but i am afraid that there might be some conflict, since all the nodes will read/write the same image.

1) What are the directories/files that Ubuntu Server writes?
2) What is the best strategy, should i mount those directories on tmpfs, local storage (all the nodes have local SSDs), or NFS?
3) How exactly to do this? I think just putting these in /etc/fstab won't work.

Thank you in advance for any suggestions,
                                                                 Kostas

---

### Post by extremis11 on 2016-02-23
One solution is to use a Union Filesystem (aufs) that merges a ro image on nfs with a rw filesystem on local RAM:

[http://shitwefoundout.com/wiki/Diskless_ubuntu](http://shitwefoundout.com/wiki/Diskless_ubuntu)

I have already created a virtual cluster on VirtualBox: one VM is setup as a root server while 2 other VMs netboot from the first one. So far everything works just fine. Time to move on to the real thing...

---

