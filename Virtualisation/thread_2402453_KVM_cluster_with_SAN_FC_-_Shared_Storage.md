---
title: "KVM cluster with SAN FC - Shared Storage ?"
date: 2018-09-30
forum: Virtualisation
---

### Post by bilalinamdar on 2018-09-30
Hi,

We want to move from Hyper-v to KVM.
We have 4 node to work with And **SAN (FC based)**
We need to have a shared storage for all the 4 node with the LUN.
We are still confused as we **don't** have a ISCSI feature.

Currently we are using mediator like OPEN filler which convert LUN to NFS.
We need a good but easy solution for the same. We do not want to use any mediator as the openfiller is on other platform.
Please suggest.

edit : We  also checked glusterfs,ceph, gfs2 etc but confused on what will be well suited for our scenario of 4 node

---

