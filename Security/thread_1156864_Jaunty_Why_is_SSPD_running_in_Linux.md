---
title: "Jaunty: Why is SSPD running in Linux?"
date: 2009-05-12
forum: Security
---

### Post by mibadt on 2009-05-12
Hi,
I'm on a fully updated Kubuntu Jaunty (9.04). While running I've noticed several outgoing SSPD UDP communications trials on port 1900 which were blocked by my FW.
Why is SSPD running in Linux (I know it runs on XP), is it necessary, and, if not, how do I get rid of it?

Best Regards,

Michael Badt

---

### Post by lovinglinux on 2009-05-12
It is related to UPnP functionality. If you are using an application with UPnP enabled it will multicast on port 1900 to the address 239.255.255.250. 

Simply disable the UPnP option in the software you are using with UPnP support and it should stop sending these packets. But if you want to allow, for example, your torrent client to open the necessary port on the router automatically, then you should allow this port/ip in the firewall and enable UPnP on the software.

---

### Post by mibadt on 2009-05-12
Thanks a lot for the clarification!

Michael Badt

---

