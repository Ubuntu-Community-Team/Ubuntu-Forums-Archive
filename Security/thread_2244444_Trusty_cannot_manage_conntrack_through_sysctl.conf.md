---
title: "Trusty: cannot manage conntrack through sysctl.conf... seriously?"
date: 2014-09-16
forum: Security
---

### Post by feanorknd on 2014-09-16
Hello:

Have several servers running Ubuntu Server... I am configuring new fronts with 14.04 running.

The problem is I usually generate sysctl.conf rules to manage conntrack, so:

net.nf_conntrack_max=500000
net.netfilter.nf_conntrack_generic_timeout=240
net.netfilter.nf_conntrack_tcp_timeout_syn_recv=30
net.netfilter.nf_conntrack_tcp_timeout_established=3600
net.netfilter.nf_conntrack_tcp_timeout_fin_wait=60
net.netfilter.nf_conntrack_tcp_timeout_close_wait=40
net.netfilter.nf_conntrack_tcp_timeout_time_wait=120
net.netfilter.nf_conntrack_tcp_timeout_close=10
net.netfilter.nf_conntrack_tcp_timeout_max_retrans=300
net.netfilter.nf_conntrack_tcp_timeout_unacknowledged=300
net.netfilter.nf_conntrack_tcp_max_retrans=3
net.netfilter.nf_conntrack_max=500000
net.netfilter.nf_conntrack_buckets=16384

This way, I can manage connections and timeouts and prevent flooding or exhausting conntrack connections available..

But in Trusty servers this is not possible as this /proc/ files are not present.

Tried to install conntrack package but it is just a commanding program... not recreate this /proc/ entries...

The question is: WHY????

This is something important to control for a sysadmin running webservers..... what is the solution propposed?

Thanks.

---

### Post by Doug S on 2014-09-16
The tcp close wait time is the only paramerer I consistently mess with. For me it has always been at:```
doug@doug-64:~/init$ [COLOR=#ff0000]ls -l /proc/sys/net/ipv4/netfilter[/COLOR]
total 0
-r--r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_buckets
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_checksum
-r--r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_count
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_generic_timeout
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_icmp_timeout
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_log_invalid
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_max
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_be_liberal
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_loose
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_max_retrans
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_close
-rw-r--r-- 1 root root 0 Sep 16 14:44 [COLOR=#ff0000]ip_conntrack_tcp_timeout_close_wait[/COLOR]
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_established
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_fin_wait
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_last_ack
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_max_retrans
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_syn_recv
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_syn_sent
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_syn_sent2
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_tcp_timeout_time_wait
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_udp_timeout
-rw-r--r-- 1 root root 0 Sep 16 19:54 ip_conntrack_udp_timeout_stream
```The files are not present until after the conntrack module is loaded when my iptables rule set loads, so I make the change to the close_wait timeout at the end of my iptables script.

---

