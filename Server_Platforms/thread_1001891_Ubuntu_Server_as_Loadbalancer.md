---
title: "Ubuntu Server as Loadbalancer"
date: 2008-12-04
forum: Server Platforms
---

### Post by RemcoRed on 2008-12-04
Hi,

We're using Ubuntu Server 8.10 as a loadbalancer, using heartbeat and haproxy and experiencing problems when having a large load.

I believe the issue lies with the tcp / network configuration, because the haproxy, heartbeat and everything is working ok. 

When having a large load, the users are experiencing some lag. There is nothing in the syslog, but when looking at netstat I see that there are 50000+ time_wait sockets. So I'm currently thinking that the server is running out of sockets.

I've tried to do some optimization myself, but nothing seems to have effect:

net.netfilter.nf_conntrack_max=1048576 
net.ipv4.ip_nonlocal_bind=1
net.ipv4.netfilter.ip_conntrack_max=1048576
net.ipv4.tcp_tw_recycle=1
net.ipv4.tcp_tw_reuse=1
net.ipv4.tcp_synack_retries =2
net.netfilter.nf_conntrack_generic_timeout = 300 
net.netfilter.nf_conntrack_tcp_timeout_established = 1800
net.netfilter.nf_conntrack_tcp_timeout_fin_wait = 20 
net.netfilter.nf_conntrack_tcp_timeout_close_wait = 20 
net.netfilter.nf_conntrack_tcp_timeout_last_ack = 10 
net.netfilter.nf_conntrack_tcp_timeout_time_wait = 20 
net.netfilter.nf_conntrack_tcp_timeout_close = 10 
net.netfilter.nf_conntrack_udp_timeout = 10 
net.netfilter.nf_conntrack_udp_timeout_stream = 30 
net.netfilter.nf_conntrack_icmp_timeout = 5
net.ipv4.tcp_rfc1337=1

net.core.wmem_max=83886080
net.core.wmem_default=83886080

net.core.rmem_max=335544320
net.core.rmem_default=335544320

fs.filemax=65536
net.ipv4.tcp_max_tw_buckets = 2440000
net.ipv4.tcp_fin_timeout = 15
net.ipv4.tcp_max_syn_backlog = 65536
net.ipv4.tcp_syncookies=1
net.ipv4.ip_local_port_range = 1024 65535
net.core.netdev_max_backlog=100000

Any ideas?

Thanks,

Remco

---

