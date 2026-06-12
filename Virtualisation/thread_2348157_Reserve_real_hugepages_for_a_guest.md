---
title: "Reserve real hugepages for a guest"
date: 2017-01-01
forum: Virtualisation
---

### Post by edgar.helmut on 2017-01-01
I am using ubuntu 16.04 as host and qemu kvm 2.5 for virtualization. Trying to bring up a guest with its memory backed by host's hugepages, but not anonymous/transparent hugepages. 
I am following the libvirt documentation but only get guest backed by AnonHugePages Rather than by using HugePages_Free.
I allocate total of 8G hugepages on boot time (i tried with 2M and with 1G page size) and the guest needs only 2G.

Note i capablebto use my allocated hugepages only using applications running on the host  (e.g. Running a dpdk based applications).

How do I back my guest memory with real hugepages of the host?

Thanks

---

### Post by KillerKelvUK on 2017-01-02
Hi, have you been looking here [https://help.ubuntu.com/community/KVM%20-%20Using%20Hugepages](https://help.ubuntu.com/community/KVM%20-%20Using%20Hugepages).  Using that guide with my Windows vm it correctly uses HughPages_Free as you require.

---

