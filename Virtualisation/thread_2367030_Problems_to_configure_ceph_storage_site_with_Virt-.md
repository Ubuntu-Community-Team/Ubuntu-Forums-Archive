---
title: "Problems to configure ceph storage site with Virt-Manager"
date: 2017-07-25
forum: Virtualisation
---

### Post by jorgerodriguezing on 2017-07-25
Hi everybody,

I have a POC with 2 KVM host servers and a ceph cluster standed by 3 OSDs and 1 monitor servers. Everything is working fine as I'm able to create VMs and then change the virtual HD to use one from RBD pool defined at Ceph cluster (via virsh edit).

The problem comes when I try to configure a new storage site in virt-manager for any of the KVM Servers for the ceph system: I always receive error "Operation not permitted"; I suspect it's a ceph auth problem but I'm unable to find the user used to connect to ceph monitor server by virt-manager, or maybe it's another problem/error by my side.

I have searched for virt-manager doc about ceph storage but I haven't found anything...

Any clue/help?

Thanks in advance

Jorge

---

### Post by jorgerodriguezing on 2017-08-01
Bump.

---

### Post by QIII on 2017-08-01
After a week without a bump to bring your post back to the surface it is not likely to be noticed.

You may bump your post after about 12 hours without a response by replying to it with the word "Bump" to raise it to the top.

---

