---
title: "How do I perform maintenance on a master DNS/DHCP (BIND9/ISC-DHCP) Ubuntu server?"
date: 2013-09-06
forum: Server Platforms
---

### Post by Sniperm4n on 2013-09-06
Hi everyone,

I'm running non-GUI Ubuntu Server 12.04.2 LTS (64-bit) on my 2 DNS/DHCP  servers. Both servers are running BIND9 9.8.1-P1 and ISC-DHCP-SERVER  4.1.ESV-R4-0ubuntu5.6. Please note that for DNS I'm running them in a  master/slave configuration, and for DHCP they are running a failover  configuration. Ideally, I'd like to perform maintenance on the  master/primary first, and once it's back up and running, I'd like to  then take care of the secondary/slave. Maintenance will consist of  installing various updates and performing a restart. I'm uncertain how  to gracefully bring each machine down without losing/interrupting  service. Any advice is greatly appreciated!

Thanks,
-Snipe

---

### Post by houstonbofh on 2013-09-06
It should failover correctly when you just shut down one.  And it is a good time to test that! :)  But choose a good time where downtime will be less noticed.

---

### Post by Sniperm4n on 2013-09-09
I know that DNS/BIND9 will work just fine since my slave has all of the same zone files. It's the DHCP failover aspect that I was concerned with. I was under the impression that you had to use RNDC to set one of the servers to a partner-down state, but wasn't certain (I'm not a Linux System Admin by trade).

---

