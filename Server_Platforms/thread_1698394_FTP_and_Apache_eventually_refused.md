---
title: "FTP and Apache eventually refused?"
date: 2011-03-02
forum: Server Platforms
---

### Post by CrusaderAD on 2011-03-02
This has me completely stumped. I installed Ubuntu Server 10.04 on a dell inspiron, twice just to make sure I didn't mess something up. Apache and SSH work fine post boot. Eventually, just inexplicably, it stops working. SSH is refused and Apache doesn't seem to be running, or it is and it's blocked. What really gets me is that I installed ssh on many many other machines on the same network, even the same ip range and they work fine. They never eventually refuse access for no reason. I checked the startup on the machine and ssh / apache do start at boot... so I'm not crazy there. It does have a static IP but so do many other machines... so I can't believe it's the router / firewall. Especially when I can connect at some point, then it just decides to stop. Any ideas?

---

### Post by dtfinch on 2011-03-02
Could there be another system on the network with the same IP? It can happen sometimes mixing dhcp and static ips, if you forget to either reserve or exclude the static ip from the dhcp pool.

---

### Post by CrusaderAD on 2011-03-02
I'm pretty sure that's not the issue. I have the IP reserved on the firewall for this machine's mac address. Is there a way to resolve the machine's hostname when I ping it? This way I can tell for sure that the machine refusing the connection is the right one?

---

