---
title: "GlusterFS and AoE questions."
date: 2010-04-23
forum: Server Platforms
---

### Post by mysteron on 2010-04-23
Hi.

I've been searching for a simple solution for getting a clustered filesystem up and running. I started tinkering with redhat-cluster-suite but cannot find good information on how to implement GFS on Ubuntu. Then I came across GlusterFS.

I now have some questions regarding GlusterFS and ATA-over-Ethernet. Does someone know if it is possible to do this scenario:

Two independent Ubuntu 9.10 servers, both autodiscover the AoE disk system, but does not mount any filesystem, as the ext4 filesystem would be corrupted if two servers mount it.

I'd like to use GlusterFS to mount the ext4 filesystem on the AoE disk system, but I do not know how to do this. Is it even possible to do this?

Feedback would be greatly appreciated :)


Thx,
/mysteron

---

