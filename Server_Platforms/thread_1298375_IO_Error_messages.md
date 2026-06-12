---
title: "I/O Error messages"
date: 2009-10-22
forum: Server Platforms
---

### Post by gencha on 2009-10-22
During boot time I got a few error messages regarding I/O which I do not understand.
The refer to sdc which is part of a md Raid 5. My system has been performing normally. mdadm -D or mdstat don't report any problems.
The output of dmesg looks like this:
```

[   42.809695] attempt to access beyond end of device
[   42.809701] sdc: rw=0, want=3636142360, limit=2930277168
[   42.809704] Buffer I/O error on device sdc1, logical block 737231200
[   42.809759] attempt to access beyond end of device
[   42.809761] sdc: rw=0, want=3636142364, limit=2930277168
[   42.809762] Buffer I/O error on device sdc1, logical block 737231201
[   42.809814] attempt to access beyond end of device
[   42.809816] sdc: rw=0, want=3636142360, limit=2930277168
[   42.809817] Buffer I/O error on device sdc1, logical block 737231200
[   42.809869] attempt to access beyond end of device
[   42.809870] sdc: rw=0, want=3636142364, limit=2930277168
[   42.809872] Buffer I/O error on device sdc1, logical block 737231201
[   42.809927] attempt to access beyond end of device
[   42.809929] sdc: rw=0, want=3636142584, limit=2930277168
[   42.809931] Buffer I/O error on device sdc1, logical block 737231256
[   42.809982] attempt to access beyond end of device
[   42.809983] sdc: rw=0, want=3636142588, limit=2930277168
[   42.809985] Buffer I/O error on device sdc1, logical block 737231257
...
[   42.831621] attempt to access beyond end of device
[   42.831622] sdc: rw=0, want=7018997606, limit=2930277168
[   42.831629] attempt to access beyond end of device
[   42.831630] sdc: rw=0, want=7018997604, limit=2930277168
[   42.831632] attempt to access beyond end of device
[   42.831634] sdc: rw=0, want=7018997605, limit=2930277168
[   42.831636] attempt to access beyond end of device
[   42.831637] sdc: rw=0, want=7018997606, limit=2930277168
[   42.831641] attempt to access beyond end of device
[   42.831643] sdc: rw=0, want=7018997604, limit=2930277168
[   42.831645] attempt to access beyond end of device
[   42.831646] sdc: rw=0, want=7018997605, limit=2930277168
[   42.831648] attempt to access beyond end of device
[   42.831650] sdc: rw=0, want=7018997606, limit=2930277168
[   42.831654] attempt to access beyond end of device
[   42.831655] sdc: rw=0, want=7018997604, limit=2930277168
[   42.831657] attempt to access beyond end of device
[   42.831659] sdc: rw=0, want=7018997605, limit=2930277168
[   42.831661] attempt to access beyond end of device
...
[  136.052788] sdc: rw=0, want=3636142364, limit=2930277168
[  136.996075] attempt to access beyond end of device
[  136.996081] sdc: rw=0, want=3636142360, limit=2930277168
[  136.996259] attempt to access beyond end of device
[  136.996262] sdc: rw=0, want=7018997372, limit=2930277168
[  137.401348] attempt to access beyond end of device
[  137.401354] sdc: rw=0, want=3636142360, limit=2930277168
[  137.401523] attempt to access beyond end of device
[  137.401525] sdc: rw=0, want=7018997372, limit=2930277168
[  137.464537] NET: Registered protocol family 17
[  140.240253] loop: module loaded

```
Do I need to worry? Should I replace the device?

---

### Post by st.andrew on 2009-11-30
Hi, 
Got exactly the same situation. 
Ubuntu 8.04 server, sw raid5 consisting of 3 sata drives. Whole raid is used by iscsitarget. System seems to be working fine. But..Since recent we're experiencing some performance issues of several iscsi-initiators, especially at disk read-write operations. While troubleshooting the performance issue in /var/log/messages we're seeing many lines like: 
```
[   48.783763] sdd: rw=0, want=1953536118, limit=976773168
[   48.783766] attempt to access beyond end of device
[   48.783768] sdd: rw=0, want=1953536120, limit=976773168
[   48.807625] attempt to access beyond end of device
[   48.807630] sdc: rw=0, want=1953536002, limit=976773168
[   48.807633] attempt to access beyond end of device
[   48.807635] sdc: rw=0, want=1953536004, limit=976773168
[   48.807638] attempt to access beyond end of device

```

Don't know is that a cause of our problem. Google'ing didn't help us. 
Does anyone know how should we fix that?

---

### Post by gencha on 2009-11-30
After reading sites like [http://www.tuxmachines.org/node/35389](http://www.tuxmachines.org/node/35389) what confuses me the most that the error seems to indicate something is wrong with the filesystem on the disc.
But there isn't even a filesystem on the disc as it is part of the raid.

---

