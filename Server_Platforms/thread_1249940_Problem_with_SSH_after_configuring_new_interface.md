---
title: "Problem with SSH after configuring new interface"
date: 2009-08-26
forum: Server Platforms
---

### Post by schapman43 on 2009-08-26
I just installed Ubuntu Server 9.04 on a machine with 3 nics.  I plugged eth0 into my network during install for updates etc.  eth0 will eventually be my internet connection so I left it as DHCP and then configured eth1 with a static IP.  After install I was able to SSH into eth0 which is actually where I configured eth1 etc.  Now that eth0 is disconnect and eth1 is configured and connected I no longer have SSH connectivity.  I am able to ping eth1 and able to get updates etc.  I have rebooted the machine and restarted SSH with no luck.  When I do netstat -an | grep 22 I end up with
TCP      0 0.0.0.0:22      0.0.0.0:*     LISTEN

nmap from another machine back to eth1 does not show port 22 being open.  Not firewall has been configured at this point.  Where do I go from here?




Also, when I try to connect with this machine I get.


ssh: connect to host 10.26.0.2 port 22: Connection refused

---

