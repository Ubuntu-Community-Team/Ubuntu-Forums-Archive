---
title: "virtio_net performance"
date: 2011-01-30
forum: Ubuntu Cloud and Juju
---

### Post by wcorey on 2011-01-30
In the course of helping a fellow UEC user he, and consequently we, hit a potential bug. In the case of a system with an e1000 or even a Realtek NIK or simulated NIC performance sucks with the emulated driver in an instance. But changing the eucalyptus.conf settings for virtio_* to 1 the generated kvm command line uses virtio where possible. This brings performance up substancially. In the case of an e1000 or Realtek NIC performance is right about 800Mbs (very close to hardware speed. This is wonderful and way better than using a fully virtualized driver.

------------------------------------------------------------
Client connecting to 172.19.1.8, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[ 3] local 172.19.1.7 port 60596 connected with 172.19.1.8 port 5001
[ ID] Interval Transfer Bandwidth
[ 3] 0.0- 1.0 sec 67.4 MBytes 566 Mbits/sec
[ 3] 1.0- 2.0 sec 90.0 MBytes 755 Mbits/sec
[ 3] 2.0- 3.0 sec 90.5 MBytes 759 Mbits/sec
[ 3] 3.0- 4.0 sec 98.4 MBytes 826 Mbits/sec
[ 3] 4.0- 5.0 sec 91.9 MBytes 771 Mbits/sec
[ 3] 5.0- 6.0 sec 92.9 MBytes 779 Mbits/sec
[ 3] 6.0- 7.0 sec 94.0 MBytes 789 Mbits/sec
[ 3] 7.0- 8.0 sec 97.1 MBytes 815 Mbits/sec
[ 3] 8.0- 9.0 sec 103 MBytes **860 Mbits/sec**
[ 3] 9.0-10.0 sec 95.7 MBytes 803 Mbits/sec
[ 3] 0.0-10.0 sec 921 MBytes 772 Mbits/sec

However for people running 10GB NIC cards by specifying virtio_net only brings their speed up to just over 1GB/s.

ubuntu@172:~$ ./nuttcp 172.19.1.4 <- virtual machine speed
1283.1875 MB / 10.00 sec = **1076.4544 Mbps** 39 %TX 45 %RX 0 retrans 1.49 msRTT

Same test at the base install level.... <- real measured machine speed

hoot@cloud1:~$ ./nuttcp 10.10.10.3
11048.6250 MB / 10.00 sec = **9265.0703 Mbps** 38 %TX 87 %RX 0 retrans 0.22 msRTT

From just anecdotal hits on Google this appears to be an introduced bug in recent versions of either KVM or Linux Kernel. I saw a thread where if one were to recompile and install a different kvm-qemu the problem is rectified. I open this thread in order to provide a central place to separate fact from fiction and, hopefully, provide closure on this issue.

If such a fix exists, will, or can,  it be included in U11.04?

References:
[http://www.mail-archive.com/kvm@vger.kernel.org/msg42690.html](http://www.mail-archive.com/kvm@vger.kernel.org/msg42690.html)
[http://forum.proxmox.com/threads/5002-good-virtio-net-performance](http://forum.proxmox.com/threads/5002-good-virtio-net-performance)

---

### Post by kim0 on 2011-02-04
Since you're referring to a bug, I would think a bug report is more appropriate. Not much developers check this forum

---

