---
title: "Disable or wided netfilter restrictions?"
date: 2015-12-02
forum: Server Platforms
---

### Post by Asquirrel on 2015-12-02
I've spent the past two days trying to google how to do this. Long story short, I have 4000 VMs pointed at a single ubuntu server running mysql (mariadb 5.5). Once I go above 1000 VMs trying to chat with the server (all they are doing is a single insert statement every 10 seconds) the server basically goes 'gates closed', SSH sessions drop, inbound SSH connections are refused, etc. The target of the 4000 VMs is Ubuntu 14.04 LTS Server edition. 64-bit.

I see this message in syslog:
```
Dec  2 15:17:33 mysql01 kernel: [84039.877321] net_ratelimit: 2871 callbacks suppressed
Dec  2 15:17:40 mysql01 kernel: [84047.618194] net_ratelimit: 575 callbacks suppressed
Dec  2 15:18:08 mysql01 kernel: [84075.257781] net_ratelimit: 9573 callbacks suppressed
Dec  2 15:18:16 mysql01 kernel: [84083.293041] net_ratelimit: 3004 callbacks suppressed
Dec  2 15:18:33 mysql01 kernel: [84099.990519] net_ratelimit: 3001 callbacks suppressed
Dec  2 15:18:41 mysql01 kernel: [84107.825431] net_ratelimit: 575 callbacks suppressed
Dec  2 15:19:08 mysql01 kernel: [84135.131487] net_ratelimit: 9631 callbacks suppressed
Dec  2 15:19:16 mysql01 kernel: [84143.143240] net_ratelimit: 3003 callbacks suppressed
Dec  2 15:19:33 mysql01 kernel: [84160.159428] net_ratelimit: 3000 callbacks suppressed
Dec  2 15:19:41 mysql01 kernel: [84168.032751] net_ratelimit: 250 callbacks suppressed
Dec  2 15:20:08 mysql01 kernel: [84195.185459] net_ratelimit: 9430 callbacks suppressed
Dec  2 15:20:16 mysql01 kernel: [84203.192389] net_ratelimit: 3003 callbacks suppressed
```

They are also in kern.log

Because most posts about this get into TCP parameter tweaking, here is what I have in sysctl.conf:

```
net.core.somaxconn = 32768
net.core.rmem_max = 1048576
net.core.netdev_max_backlog = 250000
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_mem = 8388608 8388608 8388608
net.ipv4.tcp_congestion_control=htcp
net.ipv4.route.flush=1
net.netfilter.nf_conntrack_max=10485760
net.netfilter.nf_conntrack_generic_timeout=120
net.netfilter.nf_conntrack_tcp_timeout_established=54000
net.ipv4.ip_local_port_range=1024 65535
net.ipv4.tcp_max_syn_backlog=250000

net.core.optmem_max = 1048576
net.ipv4.tcp_tw_recycle=1
net.ipv4.tcp_tw_reuse=1
net.ipv4.tcp_syncookies = 0
```

Is it simply not possible to point that many connections at a single NIC? My throughput/bandwidth numbers are tiny, at best. I'm not flooding the network or the NIC with traffic. I think it purely has something to do with 4000+ connections on the same port (3306, mysql). Any ideas, anyone?

For additional context, this problem happens with 4000+ connections only to an NFS server (also Ubuntu, nfs-kernel-server). It has something to do with the number of connections, not the software itself. Mysql has been modified to handle the 4000+ connections. The server host...that's where I'm lost. :/

---

### Post by Asquirrel on 2015-12-03
The fix was the ARP table being too small. I was using a /16 network. The relevant fix is to increase these values in /etc/sysctl.conf

net.ipv4.neigh.default.gc_thresh1 = 8192
net.ipv4.neigh.default.gc_thresh2 = 16384
net.ipv4.neigh.default.gc_thresh3 = 32768

---

