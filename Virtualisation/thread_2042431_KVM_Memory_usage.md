---
title: "KVM Memory usage"
date: 2012-08-14
forum: Virtualisation
---

### Post by Antoniya001 on 2012-08-14
Hi there,
 
I'm seeing some high memory usage and was wondering if it was normal.
 
I'm running 2 VMs on my Ubuntu 12.04 (server edition) :
 
1) Windows 2008R2 server which has 2048MB assigned to it.
2) Ubuntu server edition 12.04 which has also 2048MB assigned to it.
 
in TOP I get 2 processes : 
The first kvm process (windows 2008R2) uses about 2G of memory.
But the second kvm process (Ubuntu 12.04) uses more than 4G of memory.
 
2.03G in SWAP and 2G in RES.. Isn't that quite high for a simple lamp stack running a few websites ? (2x wordpress, subsonic, tools)
 
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  SWAP COMMAND
28616 libvirt-  20   0 2470m 2.0g 6916 S    7 25.9   0:24.38 435m kvm
 1324 root      20   0  833m 7488 3976 S    1  0.1   0:23.15 826m libvirtd
   36 root      25   5     0    0    0 S    1  0.0  13:35.79    0 ksmd
 2125 libvirt-  20   0 4467m 2.0g 6688 S    1 26.6  27:13.29 2.3g kvm
27695 sinnige   20   0  133m 2368 1040 S    0  0.0   0:00.29 131m sshd
    1 root      20   0 24452 2216 1296 S    0  0.0   0:01.03  21m init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00    0 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:01.88    0 ksoftirqd/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00    0 migration/0
    7 root      RT   0     0    0    0 S    0  0.0   0:00.48    0 watchdog/0
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00    0 migration/1
    9 root      20   0     0    0    0 S    0  0.0   0:05.55    0 kworker/1:0
   10 root      20   0     0    0    0 S    0  0.0   0:02.20    0 ksoftirqd/1
   12 root      RT   0     0    0    0 S    0  0.0   0:00.43    0 watchdog/1
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00    0 migration/2
   15 root      20   0     0    0    0 S    0  0.0   0:03.17    0 ksoftirqd/2
   16 root      RT   0     0    0    0 S    0  0.0   0:00.42    0 watchdog/2

```

---

### Post by teeks99 on 2012-08-15
I'm not sure why you're seeing the 4GB usage, but usually each VM will reserve the amount of memory that you set it with. If you have 1GB, 2GB, and 4GB VMs running, then you will see 7GB of ram allocate with the respective amounts for each of their processes. It doesn't seem to depend on what is running in each VM. Although, one would assume that if there was a chunk of RAM that wasn't being touched by a VM, then it would start swapping that to disk, but if Linux's caching is active on the VM this probably won't happend.

---

### Post by Dedoimedo on 2012-08-16
Virt is asked for allocation. Res is the actual usage.

Both/each your kvms take 2gb exactly. The fact they asked for more is not quite important. A process can ask for infinite memory and use only the allocated.

I believe your virtual machines are using whatever they need, and the host is allocating extra for its own needs. Whatever resides in swap could be pages from a snapshot or memory image or similar.

The real usage - you need to check inside the guest. Think of that 2gb limit as the real ram for the guest. And if your oses support kvm extensions, then you can overcommit and share, so your memory allocation won't be a hard limit.

Dedoimedo

---

