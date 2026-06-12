---
title: "Server Setup (VMs and Partitioning)"
date: 2008-05-19
forum: Server Platforms
---

### Post by TheGameAh on 2008-05-19
Hey guys.

Going to try to combine two servers.  (A Vmware server and a file server).

Do you think software RAID can handle file sharing (which I know isn't a big deal) plus hosting 2 virtual machines?  I'm going to use RAID10, software raid.  With a fast Core 2 Duo, was wondering if Software raid might be a bottleneck.

Also, more of a general setup question.

What is the reason behind dividing your partitions up into /var, /boot, /tmp  (etc.).

---

### Post by stefangr1 on 2008-05-19
I think the recources needed for RAID 1+0 are only limited, and should not be a problem.

When using a software raid /boot should always be on a separate non-RAID partition (preferable on all partitions, so that booting is still possible in case of disk failure). /var and /tmp could be put on separate partitions (on the RAID array) from a security viewpoint. Especially in a server environment this might be a good idea.

---

### Post by windependence on 2008-05-19
> **stefangr1 said:**
> I think the recources needed for RAID 1+0 are only limited, and should not be a problem.

When using a software raid /boot should always be on a separate non-RAID partition (preferable on all partitions, so that booting is still possible in case of disk failure). /var and /tmp could be put on separate partitions (on the RAID array) from a security viewpoint. Especially in a server environment this might be a good idea.

Be aware that this doesn't always work. I personally don't like software RAID at all as i have had bad experiences in mission critical applications with it. Hardware RAID controllers can be had fairly cheap right now. Do you even need RAID? RAID is not a substitute for backup. Just because you have a mirrored volume doesn't mean your data is safe. If one disk is compromised, the other one is immediately compromised as well. Think about that.

-Tim

---

### Post by TheGameAh on 2008-05-19
Ah, in my test labs I've always just used used a root partition and a swap (sometimes a /home as well).

So the extra paritions (/var and such), are for security reasons?

---

### Post by windependence on 2008-05-19
> **TheGameAh said:**
> Ah, in my test labs I've always just used used a root partition and a swap (sometimes a /home as well).

So the extra paritions (/var and such), are for security reasons?

No, not so much. For example, /var is where your logs are kept. If the log file grow too large they can fill up your root partition and crash your server. If you make a separate partition for /var, you won't have that problem. Similar reasons for other partitions.

-Tim

---

