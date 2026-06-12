---
title: "SiS900 troubles"
date: 2008-03-01
forum: Server Platforms
---

### Post by SimondelaCourt on 2008-03-01
I have a colocated server running Ubuntu 6.06 LTS with the latest updates, the server had a perfect uptime score until a couple of weeks back, I installed some updates, new clamav, probably also new security updates, and than downtime began. Pings go dead, server seems to be running but it shuts down all connections. For a while I could not find any messages in my logs, but than I found this:

```

Feb 29 06:25:48 jackabuzah kernel: [43260905.930000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:48 jackabuzah kernel: [43260906.210000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:48 jackabuzah kernel: [43260906.210000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:49 jackabuzah kernel: [43260907.220000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:49 jackabuzah kernel: [43260907.220000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:49 jackabuzah kernel: [43260907.250000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:49 jackabuzah kernel: [43260907.250000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:50 jackabuzah kernel: [43260907.410000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:50 jackabuzah kernel: [43260907.410000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:50 jackabuzah kernel: [43260908.220000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:50 jackabuzah kernel: [43260908.220000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:51 jackabuzah kernel: [43260908.930000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:51 jackabuzah kernel: [43260908.930000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:52 jackabuzah kernel: [43260909.420000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:52 jackabuzah kernel: [43260909.420000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:52 jackabuzah kernel: [43260909.440000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:52 jackabuzah kernel: [43260909.440000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:52 jackabuzah kernel: [43260910.220000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:52 jackabuzah kernel: [43260910.220000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:53 jackabuzah kernel: [43260910.610000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:53 jackabuzah kernel: [43260910.610000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:53 jackabuzah kernel: [43260911.250000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:53 jackabuzah kernel: [43260911.250000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:54 jackabuzah kernel: [43260911.440000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:54 jackabuzah kernel: [43260911.440000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:54 jackabuzah kernel: [43260912.220000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:54 jackabuzah kernel: [43260912.220000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:56 jackabuzah kernel: [43260913.470000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:56 jackabuzah kernel: [43260913.470000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:56 jackabuzah kernel: [43260913.820000] eth0: NULL pointer encountered in Rx ring
Feb 29 06:25:56 jackabuzah kernel: [43260913.820000] cur_rx:1385556, dirty_rx:1385556
Feb 29 06:25:57 jackabuzah exiting on signal 15


```

The system has a SiS900 onboard card and I am running kernel version 2.6.15-51-server, this seems to be a common problem.

But how do I fix this? I have moved nearly all my websites to a backup server, but I want my server back alive. What are my options? 2.6.15-51-server is the newest kernel for 6.06 LTS. What is the easiest way, without actually going to my server (because I do not have the time to get there right now) to fix this..  A dist-upgrade?

Thanks in advance,

Simon de la Court

---

### Post by smileypaul on 2008-03-03
I had the same problem when using a Marvell Yukon Card.. i tried switching to a different compatible driver, but that didtn work for me. I suggest trying a different driver, and failing that, do some research and pick up a highly compatible card. 

For reference, I have an Intel 10/100/1000 Card.. No issues.

HTH

---

