---
title: "DHCP Server Slow and Times out"
date: 2007-07-25
forum: Server Platforms
---

### Post by hogman23 on 2007-07-25
Guys,
I need some help and fast!!!!  I have a dhcp server running on Feisty Server and for some reason all of a sudden it got really slow and clients are timing out.  I moved the exact same dhcpd.conf file to another server and brought it up and everything works fine.  I had the same problem a couple of weeks ago on this server that I just moved back to.  I don't see anything abnormal in the syslog or in messages.  Does anyone have any ideas or has anyone seen this problem?
Thanks

---

### Post by hogman23 on 2007-07-25
Ok, a little more info now.  This seems to be a tcp/ip problem and not just related to dhcp.  When a tracert is done, it takes forever to get to the box.  If you run the tracert on the new box, it is extremely fast.

---

