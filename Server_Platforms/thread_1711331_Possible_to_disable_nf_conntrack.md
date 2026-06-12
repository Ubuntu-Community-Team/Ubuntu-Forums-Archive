---
title: "Possible to disable nf_conntrack?"
date: 2011-03-21
forum: Server Platforms
---

### Post by abubin on 2011-03-21
I have a server running 8.04LTS with haproxy. This is a loadbalancer that handle port 80 connections.

However, I am seeing a lot of conntrack problems.

Mar 21 16:57:39 vn197 kernel: [3545831.896760] printk: 4489 messages suppressed.
Mar 21 16:57:39 vn197 kernel: [3545831.896764] nf_conntrack: table full, dropping packet.
Mar 21 16:57:44 vn197 kernel: [3545836.891206] printk: 4374 messages suppressed.
Mar 21 16:57:44 vn197 kernel: [3545836.891211] nf_conntrack: table full, dropping packet.
Mar 21 16:57:49 vn197 kernel: [3545841.882660] printk: 4733 messages suppressed.
Mar 21 16:57:49 vn197 kernel: [3545841.882663] nf_conntrack: table full, dropping packet.
Mar 21 16:57:54 vn197 kernel: [3545846.873118] printk: 4613 messages suppressed.
Mar 21 16:57:54 vn197 kernel: [3545846.873122] nf_conntrack: table full, dropping packet.
Mar 21 16:57:59 vn197 kernel: [3545851.864580] printk: 3815 messages suppressed.
Mar 21 16:57:59 vn197 kernel: [3545851.864584] nf_conntrack: table full, dropping packet.

The default value is 65536 already. I have googled around and some says 65536 is the max value to go but some says to double the value to 131052 and so on. I did try increasing the value but the error still come.

Some says this is due to synflood and so on. I don't think it's synflood as we do connections more than 65536 with this haproxy.

Some also said to disable nf_conntrack. I have searched but there are no guide on how to disable nf_conntrack in ubuntu 8.04. Anyone can help to shed some light into this problem?

Should I increase the value to some crazy high one like 252000 (does it work?) or disable nf_conntrack?

If I disable nf_conntrack, will firewall software like CSF still work???

Please help.

---

### Post by BkkBonanza on 2011-03-21
I don't think you can remove/disable the conntrack module but I could be wrong.

You may want to adjust settings related to timeouts so that connections aren't tracked for long. Minimal periods should cause them to be dropped quickly.

net.ipv4.netfilter.ip_conntrack_tcp_timeout_close = 30
net.ipv4.netfilter.ip_conntrack_tcp_timeout_time_wait = 30
net.ipv4.netfilter.ip_conntrack_tcp_timeout_last_ack = 120
net.ipv4.netfilter.ip_conntrack_tcp_timeout_close_wait = 30
net.ipv4.netfilter.ip_conntrack_tcp_timeout_fin_wait = 60
net.ipv4.netfilter.ip_conntrack_tcp_timeout_established = 30
net.ipv4.netfilter.ip_conntrack_tcp_timeout_syn_recv = 30
net.ipv4.netfilter.ip_conntrack_tcp_timeout_syn_sent = 30

You can check your current values with, sysctl -a | grep conntrack
and adjust these in the /etc/sysctl.conf

---

### Post by abubin on 2011-03-22
thanks for the suggestion. I will do that now.

However, what sort of issue (if there are any) will be seen from lowering those values?

---

### Post by abubin on 2011-03-22
i have discovered that ubuntu 8.10, 9.10, 10.10 distro does not have netfilter conntrack enabled. Why doesn't these have that whereas x.04 versions have it?

What's the rationale behind this?

So, I am going to be using .10 versions for my loadbalancers now...strange...

---

### Post by BkkBonanza on 2011-03-22
I have never heard of that. And it doesn't sound right. But I've never looked into it though. 

I don't think lowering those values will matter if you don't need connection tracking at all. Not knowing much about your situation though, I can't say I'm sure about that.

---

### Post by abubin on 2011-03-22
you can easily verify this using amazon cloud servers. If you have amazon account. A simple server can be setup in 5 min. Check that all the .10 versions do not have conntrack and then destroy the instance. Only cost few cents. Very good platform to test.

Anyway, thanks for the suggestion to lower the values. It now seems to be working better with less connections.

---

