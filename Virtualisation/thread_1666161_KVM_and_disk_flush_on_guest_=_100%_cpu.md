---
title: "KVM and disk flush on guest = 100% cpu"
date: 2011-01-13
forum: Virtualisation
---

### Post by RRJ on 2011-01-13
Hello,

I'll start from that I've searched the forums for the problem solution, but wasn't able to find.
so here it is:
host:
ubuntu 10.04.1 LTS
2.6.32-27-server x86_64
2x Intel(R) Xeon(R) CPU E5620 (total of 16 cpus for os)
12GB RAM
2x software raids:
160GB and 2TB
the 160GB one is for system and 2TB one is for kvm images

guest:
Ubuntu 10.04.1 LTS
Disk: virtio
network: virtio

Problem:
the problem starts when the flush process starting.
it becomes using 100% of cpu for a while and then ok. and this happens on random periods of time
  ```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND

 869 root      20   0     0    0    0 S   117  0.0   0:17.80 flush-252:0
```

252 is the vda disk:
monitor@monitor:~$ ls -l /dev/vda
brw-rw---- 1 root disk 252, 0 2011-01-13 16:44 /dev/vda

and this feels bad: guest responses very slowly for the time flush process is active. it doesnt seem to affect host.
the server is just bought. no errors in dmesg about SW raid.

any ideas to solve it? ot mby turn off that sick flushing on the guest?

---

### Post by RRJ on 2011-01-13
update:
seems like this problem exists only with virtio block driver! (virtio hdd). made it ide and no more such problems. a bug?


!!!!!!!!!!update!!!!!!
in the 10.10 guest same problem with virtio driver.
if some1 interested in debugging, answer plz, as time is critical for me and if you try to search for my posts here, they are never answered. only trivial posts are answered here. seems like ubuntu and its community is pretty weak and raw yet. wouldn't install it on the new server if i had more time... but i need something with fresh kernel and kvm+ksm. i will try to install 10.10 on the host tomorrow, if there are no answers.

---

### Post by RRJ on 2011-01-16
well, 10.10 same problem with virtio disk. kind of a bug. where to report?

---

### Post by saceirdoth on 2011-01-23
Hello (sorry, i have a very poor english),

Host : 
Debian Squeeze, Linux 2.6.32-5-amd64
AMD Athlon 5050E
2x2go ram
guest are on LVM (not in images)

(Randomly) same problem with guest like :

Zentyal 2 (Ubuntu 10.04 - Linux 2.6.32)
Disk: virtio 
network: virtio
Partitions : **ext4** with LVM (because of default install of Zentyal)

LinuxMint10 (Ubuntu 10.10 - Linux 2.6.35)
Disk: virtio 
network: virtio
Partitions with **ext4**

No problem with this guest :

Debian Squeeze (Linux 2.6.32)
Disk: virtio 
network: virtio
Partitions with **ext3**

---

### Post by saceirdoth on 2011-01-24
Finaly, i've tested zentyal with ext3 and i have the same problem as ext4 (cpu usage 100%, vm not responding)
So, ext4 is not the problem.

---

### Post by sh1ny on 2011-01-25
Try adding cache='none' to the disk definitions. Also using the 'noop' elevator inside the guest helps.

---

### Post by srowlain on 2011-05-09
Hi,
I am new to the Forum. I guess this thread is solved.
Just for anyone reading this thread and
looking at the same problem, refer to
[http://www.linux-kvm.org/page/Tuning_KVM](http://www.linux-kvm.org/page/Tuning_KVM)  -> Storage

Cheers,
srowlain

---

