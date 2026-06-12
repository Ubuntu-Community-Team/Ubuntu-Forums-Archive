---
title: "HA apache2 cluster"
date: 2010-07-16
forum: Server Platforms
---

### Post by snarf77 on 2010-07-16
Hi everybody,

not used to use forum so please forgive in advance if I don't post in the right way.

I kept on searching the web for my problem and I found that I'm not the only one in that case but I can't succeed in founding a solution...

Basically my problem is :
I'm trying to set up a 2 node apache cluster based on two VM ubuntu server 10.04 with pacemaker/heartbeat/corosync.

The IP failover is working fine but I can't automatically start the apache process (here after the result of crm_mon:)

============
Last updated: Fri Jul 16 13:30:31 2010
Stack: openais
Current DC: dnsvm2 - partition with quorum
Version: 1.0.8-042548a451fce8400660f6031f4da6f0223dd5dd
2 Nodes configured, 2 expected votes
1 Resources configured.
============

Online: [ dnsvm1 dnsvm2 ]

 Resource Group: group1
     ip1        (ocf::heartbeat:IPaddr2):       Started dnsvm1
     apache2    (ocf::heartbeat:apache2):       Stopped

Failed actions:
    apache2_monitor_0 (node=dnsvm1, call=3, rc=5, status=complete): not installed
    apache2_monitor_0 (node=dnsvm2, call=3, rc=5, status=complete): not installed


I read that it should come from a problem with ocf which looks for a httpd PId which does not exist (even if I start apache2 by hand) but I can't find/understand any workaround ....

any help will be appreciated..

thanks in advance

Snarf

---

### Post by snarf77 on 2010-07-16
I found it...

indeed, the heartbeat resource should not be apache2 but apache. I really cant't figure out what difference it makes but replacing
 
ocf::heartbeat:apache2 
by 
ocf::heartbeat:apache

in crm configure edit file has finally made it work....

Thanx anyway

---

