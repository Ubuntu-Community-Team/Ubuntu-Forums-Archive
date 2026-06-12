---
title: "LXC, cgred and cgconfig strangeness"
date: 2013-10-28
forum: Virtualisation
---

### Post by gyre007 on 2013-10-28
I have a question regardgin cgroups and LXCs.
Recently I've been playing with these and I came across something I don't quite get.
I have installed cgroup-bin package for easier cgroup management
Now, when I create a hierarchy in /etc/cgconfig.conf like this:

mount {
    cpuset  = /sys/fs/cgroup/cpu_and_mem;
    cpu     = /sys/fs/cgroup/cpu_and_mem;
    cpuacct = /sys/fs/cgroup/cpu_and_mem;
    memory  = /sys/fs/cgroup/cpu_and_mem;
}

and then start cgconfig like this: sudo service cgconfig start , hierarchy is correctly created as per configuration.
NOW, what I noticed is:
when I now UPDATE the above hierarchy so that it looks like this:

mount {
    cpuset  = /sys/fs/cgroup/cpu_and_mem;
    cpu     = /sys/fs/cgroup/cpu_and_mem;
    cpuacct = /sys/fs/cgroup/cpu_and_mem;
    memory  = /sys/fs/cgroup/cpu_and_mem;
    blkio   = /sys/fs/cgroup/diskio;
}

And then RESTART cgconfig, sudo service cgconfig restart, 2 things happen:
1. cgred daemon dies:
2. NEW hierarchy (ie diskio) is NOT created

So my question is - how do I add new hierarchy simply without moun-vfs-kung-fu ? Id prefer just edit a cgconfig file and restart cgconfig...

Another really strange thing is, I can't see ns and net_cls hierarchies in the list of all available subsystems:

$ lssubsys -a 
devices
freezer
blkio
perf_event
cpuset,cpu,cpuacct,memory
$ 

Are these 2 network controllers even implemented in Ubuntu 12.04 ? I'd be surprised, as LXCs are using NS subsystem, however the above tool is not listing it mm.
Thanks in advance!
M.

---

