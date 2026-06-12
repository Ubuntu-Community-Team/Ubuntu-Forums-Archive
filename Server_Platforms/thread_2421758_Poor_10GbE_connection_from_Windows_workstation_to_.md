---
title: "Poor 10GbE connection from Windows workstation to Ubuntu server"
date: 2019-06-26
forum: Server Platforms
---

### Post by finlandapollo on 2019-06-26
Hello everyone!


I've currently running Ubuntu Server 18.04 as my server build with Intel Xeon E5-1650V4 with X10SRM-TF from Supermicro. This build is working fine, but one major problem I've encountered, 10GbE performance. Even when I put my P3700 NVME to the machine, create own ZFS pool containing only that drive, create own SMB share and connect it through my Windows PC with Asus XG-C100C NIC, I'm unable to get the saturated 10GbE, even when the P3700 is able to saturate two lanes with the read speed (and probably single write lane). This has been confirmed when doing RAMdisk test, it just stucks at roughly 600MB/s transfer speeds (sometimes write speeds drop under 400MB/s). 

iPerf2 shows roughly 9.39-9.50Gbits/sec speed from server to workstation and similar results when doing from workstation to server. However, with UDP, the performance drops to 1.5-2.0Gbits/sec speeds with occasional packet loss. 

I've tried Jumbo Frames (9014), LRO is off, GRO is off, Ethtool shows that the link is 10GbE, so does Windows (in Windows, 10GbE link speed is manually set). I've changed TCP settings in Ubuntu to:


vm.min_free_kbytes = 524288
net.ipv4.tcp_sack = 1
net.ipv4.tcp_timestamps = 1
net.core.netdev_max_backlog = 250000
net.ipv4.tcp_low_latency = 1
net.ipv4.tcp_max_syn_backlog = 8192


net.core.optmem_max = 33554432
net.core.rmem_max = 33554432
net.core.wmem_max = 33554432
net.core.rmem_default = 131072
net.core.wmem_default = 131072
net.ipv4.tcp_rmem = 4096 87380 33554432
net.ipv4.tcp_wmem = 4096 65536 33554432
net.ipv4.tcp_mem = 8388608 8388608 8388608

Still, no luck. I've also tried with another 5m CAT6a, no luck



Any ideas what to do? These two machines are connected with CAT6a, 5 meter cable, and there's nothing between these two machines. They both are in own subnet also. I'm running out of ideas. Faulty Ubuntu X550T2 driver? Faulty settings? Poor thingies? Bad luckies? Lots of yuckies? Smickedy Smackeys?

---

### Post by volkswagner on 2019-06-26
Let's get our "apples and oranges" settled ;)

If you're getting "600MB/s transfer speeds" that's 600MBs*8=4800Mbs.

Lets make sure we are talking about Megabits across the board vs. mixing MegaBytes and Megabits.

---

### Post by finlandapollo on 2019-06-27
Thank you for correction / modification! :D 

But, it feels more and more like the OS drive is somehow the bottleneck or the traffic goes through it, as the maximum speeds that I get, is as high as the speeds of my OS SSD drive (2 x 1TB Crucial MX500 SSD in software RAID1). The drives are just mounted to /, no where else.

---

### Post by volkswagner on 2019-07-07
SMB has overhead. Have you tried other protocols like NFS, SSH, SCP? Are you copying a single large file? What file system are you using?  What are your hdparm test results?

---

