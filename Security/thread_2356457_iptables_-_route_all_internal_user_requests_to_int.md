---
title: "iptables - route all internal user requests to internal ip?"
date: 2017-03-23
forum: Security
---

### Post by schworak on 2017-03-23
I am very new to iptables and redirecting of ip traffic so sorry if this is a beginer question...

What I want to capture anyone who is inside the network that is trying to access an external site and redirect them to an internal IP instaead.

For example... I want to go to bob.com and the DNS entry returns 40.123.32.44 and I am inside my own network. I want that to actually route to one of my boxes located at 192.168.0.10.


I was trying something like this based on things I had read but clearly this is not correct because it seems to do nothing...

iptables -t nat -I PREROUTING -p tcp -d 40.123.32.44  -j DNAT --to-destination 192.168.0.10


Any help would be greatly appreciated. 

PS: I want all ports redirected not just a specifc port. But if I have to list ports individually, I can do that.

THANKS!

---

### Post by TheFu on 2017-03-25
This assumes you don't want to perform the redirection on every single machine inside the LAN.  You'll want to perform whatever interception on the default router. 

Another way is to redirect all DNS results to only the machine you want.  Look up a **transparent proxy** for a way to do that.  Or you can check out the **pi-hole** project. Don't worry that they use a raspberry pi - that isn't important. It can be run on normal linux systems too.

Sorry, I don't have a 1 line answer.

---

### Post by SeijiSensei on 2017-03-26
Maybe you should remove the "-p tcp" protocol specification.  I think if you specify TCP you may need to give it a port number.  But according to [this source](http://linux-ip.net/html/nat-dnat.html), the rule
```
iptables -t nat -I PREROUTING  -d 40.123.32.44 -j DNAT --to-destination 192.168.0.10
```
should redirect all outbound traffic.

---

