---
title: "Starting a vmware file chops up my NIC....."
date: 2008-04-24
forum: Virtualisation
---

### Post by jingo811 on 2008-04-24
Starting a vmware file chops up my NIC from the external ip 163.13.13.89
into 2 additional virtual ips.  That makes it a total of 3 ips.
I believe this process is called NAT or something.

When this happen Ubuntu which previously had Internet connection looses its connectivity after starting up a vmware virtualization containing SuSE. The virtualization have Internet access but not Ubuntu any more.

The instructor told me that this may be a cause of badly configured DHCP at school.  **My question is this:**
    How can I from my student workstation find out what working DNS servers exists on my schools network (without looking at other peoples /etc/resolve files)?  Since starting up VMplayer seems to overwrite my working DNS and stuff making my Ubuntu loose Internet while SuSE have proper Internet.

---

