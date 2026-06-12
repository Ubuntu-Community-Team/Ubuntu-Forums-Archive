---
title: "Ubuntu 18.04 as Router/Gateway NAT Performance"
date: 2018-09-25
forum: Ubuntu/Debian BASED
---

### Post by alexvalledor on 2018-09-25
Hello Ubuntu Forums,

I've been a Linux user for some time now and recently began replacing networking equipment with Linux based devices. So far I'm very happy with the performance improvement and flexibility it offers over off the shelf routers. 

I do have a question though. After some mildly extensive testing I have determined that the Ubuntu kernel is doing something under the hood than say CentOS, Debian, and even Arch Linux.

At home I have a 250/20 Mbps internet connection and at work I have a 1000/1000. Both locations have the same Gigabyte based all in one motherboard with dual network cards and Intel Celeron 847 Dual Core 1.1ghz CPU.

I have found that with Arch, CentOS, pfSense, and Debian my CPU usage is roughly 30-40% when running 250Mbps through iptables NAT and about 80-90% nearing 850Mbps NAT. However when I run the same tests on Ubuntu Server 18.04 LTS I am seeing much much better performance.

The Ubuntu machine is barely breaking 5% at home and 15-20% while achiving 940-950Mbps at work. 

It seems that the Ubuntu kernel is heavily optimized or has maybe a fastpath type feature enabled? I've done some searching and haven't been able to find if my results are accurate or if top, and htop are incorrectly reporting CPU usage. Even if that was the case I'm seeing much higher throughput on the 1000/1000 Mbps connection.

I am making this post primarily to learn more about Linux in general and determine what the difference is in the network stack between the distros tested above.

Sincerely,

Alex

---

### Post by wildmanne39 on 2018-09-25
Hello and welcome to the forum!

Please use your thread at the link below and do not create duplicate threads.

[https://ubuntuforums.org/showthread.php?t=2402072](https://ubuntuforums.org/showthread.php?t=2402072)

Thread closed!

Thanks

---

