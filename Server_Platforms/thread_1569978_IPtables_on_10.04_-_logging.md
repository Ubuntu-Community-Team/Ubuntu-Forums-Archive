---
title: "IPtables on 10.04 - logging"
date: 2010-09-07
forum: Server Platforms
---

### Post by linorics on 2010-09-07
Hi I'm trying to get logging to log droped packets in 10.04. ICMP is being blocked fine but I don't get any logging.

Inside /var/log/messages all I see is
Sep  7 10:01:21 DaVinci kernel: [  691.420240] ip_tables: (C)
2000-2006 Netfilter Core Team


$iptable -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
LOGNDROP   icmp --  anywhere             anywhere
DROP       icmp --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain LOGNDROP (1 references)
target     prot opt source               destination
LOG        tcp  --  anywhere             anywhere            limit:
avg 2/sec burst 10 LOG level warning prefix `TCP LOGDROP: '
LOG        icmp --  anywhere             anywhere            limit:
avg 2/sec burst 10 LOG level warning prefix `IMCP LOGDROP: '
DROP       all  --  anywhere             anywhere

Did I config my rules wrong? are the logs saved somewhere else in 10.04??

---

