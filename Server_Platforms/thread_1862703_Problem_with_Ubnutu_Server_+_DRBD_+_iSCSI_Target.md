---
title: "Problem with Ubnutu Server + DRBD + iSCSI Target"
date: 2011-10-17
forum: Server Platforms
---

### Post by gushtera on 2011-10-17
Hello friends, 
I have problem with Ubuntu Server with DRBD and iSCSI Target 

That's my configuration:
2 Nodes with Poweredge 850 + 12 Port RAID Controller 3ware
1 Gigabit Switch 24 Port SMC 
and each server have 2 NICs 1Gbps 
2 ESXi Servers with 2 NICs

so... when i test drbd replication between 2 nodes the replication speed is around 50Mbps how can i reach more traffic and where is the problem with my replication.

and... when i test the traffic of the iSCSI with installed on Virtual Slackware on the ESXi i test with dd and the traffic is around 18MB/s on the test but the traffic that I see with iptraf and bmon on the ubuntu server is around 100Mbps when i try to test read speed the speed is around 60MB/s so where is my problem?

Please Help me! ;)

Best Regards,
Plamen Petkov

---

