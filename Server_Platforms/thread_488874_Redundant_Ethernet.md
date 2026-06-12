---
title: "Redundant Ethernet"
date: 2007-06-30
forum: Server Platforms
---

### Post by borahshadow on 2007-06-30
Hi I just noticed in another thread someone said to make sure to have redundant power and ethernet
I have a home server (if you have not noticed my other threads) and while I don't think I the cost is worth it to run redundant power should I run dual ethernet? I have an old NIC card so it would not cost me anything could I get a speed boost (if both my NICs are 10/100 and my router and cableing is too?) or would it be purely backup
if so how would I set it up? would the PCI NIC interfere with my onboard?
Thanks

---

### Post by dj 2501 on 2007-06-30
having 2 nics connected to one internet connection doesnt mean it will be redundant. to  have it truly redundant  you would have to have 2 different isp lines coming into the server not 2 nics hooked up to one isp connection. I hope that makes sense. if your running a linux webserver from home like me just get the fastest uplink possible for residential use and if your site grow to where it needs wore speed you can either spend mucho dollars on a t1 or t3, get a dedicated server at a datacenter or send your server to a dc for collation.

EDIT:truly redundant servers have ups backups, multiple isp backbones, loadbalancers,and HA (heartbeat, rsync, etc)

---

### Post by borahshadow on 2007-07-03
this is actually just a file server locally so it does not connect to the outside internet (not for serving purposes just for downloading packages) so basically 2 NICs would be pretty pointless especially where downtime is not a huge issue (5 minutes to switch a pci card)
Thanks for your input

---

### Post by crazyjx23 on 2007-07-03
You could always go to fiber channel 10gigabit Ethernet lol if ya want crazy speeds. (Cheap Sarcasm.)

---

### Post by borahshadow on 2007-07-03
and I'd have to sell my arm and leg to pay for it :P

---

