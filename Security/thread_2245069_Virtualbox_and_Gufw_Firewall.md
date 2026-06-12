---
title: "Virtualbox and Gufw Firewall"
date: 2014-09-20
forum: Security
---

### Post by HardTrickySecurity on 2014-09-20
Can I block incoming and outgoing traffic with gufw installed inside my guest and block also at the same my host incoming and outgoing traffic?


In other words can I block incoming and outgoing traffic in guest and host using only gufw installed inside guest?


So far I can block guest internet traffic but I can not block host internet traffic.


Should I use bridge or nat, what excatly should I use in this scenario.

---

### Post by TheFu on 2014-09-21
probably not.
Of course if the guest is running the router for the subnet and the host's traffic always goes thru the guest, then you can run the network firewall there ... however, I'm not certain I'd trust virtualbox bridges to be secure enough for that use without setting up specific tunnels for each host involved.  Also, I've have the hostOS use a different physical NIC than the firewall VM does.

---

### Post by thnewguy on 2014-09-21
No, the guest's firewall only affects traffic coming into or leaving the guest. The host needs its own firewall.

---

