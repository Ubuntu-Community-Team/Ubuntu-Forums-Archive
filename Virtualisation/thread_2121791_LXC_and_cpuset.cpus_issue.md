---
title: "LXC and cpuset.cpus issue"
date: 2013-03-03
forum: Virtualisation
---

### Post by Moptop650 on 2013-03-03
Hi all,

I'll start out by saying I'm new to LXC. I'm using it on a fresh 12.10 64 bit install. I haven't done much besides install the OS, and create a ubuntu container named "test".

Now, in my search to limit this container to a single cpu core, I found that this line added into /var/lib/lxc/test/config would accomplish limiting this container to the 4th core on my machine:

> lxc.cgroup.cpuset.cpus = 3

However, this causes my container to fail to start.

The debug log of the start process shows this:

> lxc-start 1362298114.518 DEBUG    lxc_cgroup - Failed to find cgroup for cpuset

I'm not sure what to do from here.

---

