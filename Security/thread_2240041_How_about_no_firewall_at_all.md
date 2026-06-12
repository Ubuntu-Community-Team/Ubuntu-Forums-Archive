---
title: "How about: no firewall at all"
date: 2014-08-17
forum: Security
---

### Post by Dominic--- on 2014-08-17
He guys,

I have been wondering, I am implementing a VPN server and ran a few times into trouble (connectivityissues) mostly due to the firewall.
Now the ports that are open aren't blocked. So basically my firewall allowes the data to pass through the open ports.
When the ports are closed, no process is listening to it anyway.

Considering this: how about to disable the firewall completely?
I know it sounds stupid, and I won't do it, but what are the risks? There is only one option i.m.o. and that is when an intruder open ports himself, but considering that the root account is 'rooted' the whole system is breached anyway.

Note that I am only talking about iptables/ufw here, I am NOT talking about programs like fail2ban, tripwire, psad etc.
Just want to know how you guys think about this.

---

### Post by uRock on 2014-08-17
I'd get everything properly configured, before I gave up and disabled security services. If you need help configuring iptables/UFW(the firewall), fail2ban(IPS/IDS), tripwire (IPS/IDS) or any other security feature, then I am sure someone'd be willing to help. Just post the topic in the Security Discussions sub-forums.

---

### Post by CharlesA on 2014-08-17
What VPN software?

---

### Post by Dominic--- on 2014-08-17
@CharlesA - OpenSwan, ppp and xl2tpd

@uRock - Thank, i will do that. I am running a few tweaks atm to fix the problems but when that fails I will let you know.

---

### Post by CharlesA on 2014-08-17
Eh, I don't have experience with those, but OpenVPN only needed the listening port open and the ip forwarding rules in place.

---

### Post by bashiergui on 2014-08-17
Turning the firewall off because you can't configure it properly is as good an idea as leaving your garage door open because it's too hard to close. A server listening on the internet needs a firewall to prevent people connecting and taking over your server. An attacker that knows what they're doing can get around a firewall, but why make it easier for them? Make them work for it which will make you a less attractive target.

---

### Post by Dominic--- on 2014-08-17
Well fixed the problem with some tweaks.
I agree that a firewall always should be turned on. 
What I was looking for were technically well founded arguments on how such an situation could be exploited by an attacker.
I ask because I simply cannot answer this one myself, except because of the 'unknown' ofcourse but again, thats not a argument I myself was looking for.
Thanks 4 all replies!

---

### Post by Hungry Man on 2014-08-17
An inbound firewall provides essentially nothing, unless configured quite specifically, and even then it is questionable. The only thing it can do that is relevant is close ports to local services, but anyone behind a router has nothing to fear there either.

Outbound firewalls are also useless, moreso maybe, as any program within the context of a user can manipulate all other programs within that contaxt, and any single port like 80 is enough to attack a system.

So don't feel too bad if you shut it off.

---

### Post by axiomanarcho on 2014-08-18
It would be completely irresponsible to disable a firewall to VPN server. 

You will need to make a rule in the iptables firewall to allow a port for VPN access.

---

### Post by ian-weisser on 2014-08-18
Since the default settings on a fresh install of Ubuntu are to allow all packets, it's very much like already turned off.

---

### Post by sedawk on 2014-08-19
If the only open ports on your server are the ones that are reachable from outside via firewall, then the firewall has actually no functionality at all (more or less for stupid and simple firewalls that it).
But normally there are more ports open, e.g. to access the server from inside LAN, like port 22 for ssh or port 80 to see some browser statistics about VPN. And therefore you need a firewall!
I normally turn off any software firewalls (iptables, firewalld, whatsoever) because the network is additionally protected by other firewalls (router, commercial firewalls).
And there is nothing worse than firewalls inside your protected (!) private LAN making things more complicated ...

---

