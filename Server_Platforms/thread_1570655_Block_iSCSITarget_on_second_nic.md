---
title: "Block iSCSITarget on second nic"
date: 2010-09-08
forum: Server Platforms
---

### Post by bcdudley on 2010-09-08
I am running Ubuntu 10.04 with iscsitarget. I have shared out 3 luns of 1.5Tb each. The machine has 2 nics in it. The first is setup as a management interface and is on a 10.x subnet. The second nic is a 10Gbe interface at 172.168.1.x and is meant to be the primary interface for the iSCSI service. 

I am trying to block the iSCSI Target server from advertising on the 10.x management interface. My initiatiors.allow file is:

```
ALL 172.168.1.0/24
```and nothing else. My next step I can think of is to firewall the box, but is there another way I should be doing this?

Thank you.

---

