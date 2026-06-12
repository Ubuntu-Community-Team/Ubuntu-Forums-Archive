---
title: "iptables causing webserver crash"
date: 2007-02-14
forum: Server Platforms
---

### Post by tmonteit on 2007-02-14
Somethings going wrong on web server.  Every day at 7:30 my web page is inaccessible.  We believe it's associated with the 7:35 event in the tables below.     

/var/log/messages shows:
   Feb 11 07:11:57 localhost -- MARK --
   Feb 11 07:31:57 localhost -- MARK --
   Feb 11 07:35:04 localhost kernel: [17261443.800000] ip_tables: (C)
2000-2002 Netfilter core team
   Feb 11 07:35:05 localhost kernel: [17261444.636000] Netfilter messages via NETLINK v0.30.
   Feb 11 07:35:05 localhost kernel: [17261444.644000] ip_conntrack version 2.4 (8191 buckets, 65528 max) - 232 bytes per conntrack
   Feb 11 07:35:47 localhost exiting on signal 15
   Feb 11 07:35:48 localhost syslogd 1.4.1#17ubuntu7: restart.
   Feb 11 07:40:03 localhost exiting on signal 15

It was recommended I look at the ip_tables/netfilter configuration.  

What's going?   I know nothing about iptables.  So please advise at the beginner level.

I want to disable/kill/nuke whatever process is locking port 80 every morning causing this 7:35.

How do I fix this?

---

