---
title: "ubuntu servers -VM- 18.04 hanging issue"
date: 2021-09-15
forum: Server Platforms
---

### Post by lacid2 on 2021-09-15
I have a few virtual Ubuntu servers (18.04.5 LTS) running on VMware ESXi, 6.7.0. Once in every couple of minutes one or more of them hangs, you can't do anything but wait. The hanging is random,  The load is low, 1 or less. They hang for random commands (ls anywhere, ping, vi, top ps, etc).
While the hanging I'm noticing on the console messages like: [HTML][191519.941337] INFO: task whatever_process:21702 blocked for more than 120 seconds.[/HTML]
First I though about hardware issues, but on the same hardware I have other VM's running on FreeBSD which have no hangs or any other issues.
[IMG]https://ibb.co/mCMVqgq[/IMG]

Did you guys notice things like this before?

Here is a screenshot: [https://ibb.co/mCMVqgq](https://ibb.co/mCMVqgq)

[IMG]https://ibb.co/mCMVqgq[/IMG]

---

### Post by TheFu on 2021-09-15
Saw that with ESX and ESXi years ago.  We changed to using KVM.
Not seeing it with kernel: 5.4.0-81-generic or any recent kernel.  We've been running the HWE kernels for a number of months for 18.04 VM hosts. All good for the host and guest VMs.

---

### Post by lacid2 on 2021-09-15
I have 4.15.0-156
% uname -r
[HTML]4.15.0-156-generic[/HTML]

TheFu, can you tell me please how did you update the kernel only?

---

### Post by TheFu on 2021-09-15
search on "HWE ubuntu". It isn't a kernel only update and the root cause was the hypervisor, not the guest, in our experience.

---

### Post by lacid2 on 2021-09-15
Thank you TheFu!

---

### Post by MAFoElffen on 2021-09-16
Here...
```

sudo apt install --install-recommends linux-generic-hwe-18.04

```

---

### Post by lacid2 on 2021-09-20
It seems installing **linux-generic-hwe-18.04** and adding **nconnect=8 **to all NFS mounts in fstab has helped

---

### Post by TheFu on 2021-09-20
nconnect for nfs is fairly new. I learned about it earlier this summer. 

The best number is related to the network capacity between the NFS client and server AND number of threads the client can support.  On my workstations, I use either 2 or 4 connections. It depends on what the NFS server's NIC can support.  I really need to replace the server NIC on my storage LAN to get full GigE performance. The cheap Marvell NIC usually can't get even 600 Mbps.
```
$ iperf3 -c istar-storage
Connecting to host istar-storage, port 5201
[  4] local 172.22.21.6 port 52282 connected to 172.22.21.20 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  66.7 MBytes   559 Mbits/sec    0    402 KBytes       
[  4]   1.00-2.00   sec  64.5 MBytes   541 Mbits/sec    0    420 KBytes       
[  4]   2.00-3.00   sec  64.4 MBytes   540 Mbits/sec    0    420 KBytes       
[  4]   3.00-4.00   sec  64.5 MBytes   541 Mbits/sec    0    438 KBytes
```

Hopefully, the HWE actually solves this for you. Think we've been using the HWE on 18.04 for about a year now. No major complaints.

---

### Post by lacid2 on 2021-11-15
Thanks, so far it is looking better

---

