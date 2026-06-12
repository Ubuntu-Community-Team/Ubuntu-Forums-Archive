---
title: "Slow internet access on 10.04 server"
date: 2012-04-01
forum: Server Platforms
---

### Post by dlcobb on 2012-04-01
I need suggestions on how to determine what is going on with my 10.04 server that I recently migrated to a different computer.

The problem is that several hours after a re-boot, internet access slows to a crawl so that updates fail and BOINC cannot receive and send tasks.

Other computers using the same router and DSL modem operate normally.

After a re-boot, everything seems fine for a time.

Hardware:
 Dell Optiflex 745, 1gb memory, three 500 gb drives, Intel NS4000 NAS.  The NAS is connected directly to the Dell on eth1.  All other network is on eth0. 

Software:

Ubuntu 10.04 Server, Raid 1, usual server programs, BOINC, APCUPSD, Backuppc

TOP does not show any significant or unusual activity.  File sharing seems unaffected.   

Thanks

---

### Post by nsnidanko on 2012-04-03
when you experience slowness please check what is accessing network using **netstat** command. Also there is another nice utility called iptraf, which allows you to monitor network activity. Those are the first steps to troubleshooting network connectivity assuming that physical layer is ok.

---

