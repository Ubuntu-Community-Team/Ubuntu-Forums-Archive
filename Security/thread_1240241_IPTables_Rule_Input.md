---
title: "IPTables Rule Input"
date: 2009-08-14
forum: Security
---

### Post by OffbeatAdam on 2009-08-14
Greetings Everyone,

My apologies up front, I have a habit of being long winded.

Within our DC we have a set of systems running one of our online products. This system, unfortunately where the server(ice) is written in Java, has a bad habit of being easily DOSed. While I understand best case scenario is to address this in the code with the developers, as many know pulling teeth is more fun.

I've taken it upon myself to inconvenience the developers enough by directing all complaints from my current task in this environment directly to them, including all phone calls. However, I'm sick of waking up at 3am and coming in and resolving down servers so... here goes.

We have multiple systems on public IPs. All on the same subnet. I have the majority of my throttling rules within IPTables determined, but either my network-fu has succumbed to too much beer or I'm far more rusty than I thought... I need a little advice on the methods by which I can do what I need.

I need to set up a firewall as a gateway to these devices while these devices maintain their public IPs, if at all possible. I suspect that I will still need to use NAT. I have a feeling though, in order to do this, I would need to segment out the /24 that they are on and add an additional gateway that essentially becomes this firewall. If that is the case... then I will go the other route and just simply give them a small private class C and use regular natting.

So, that is the question:

Can I set up an IPTables gateway that stands inline between this cluster and the rest of humanity, without having to change the public IPs of the cluster, without having to break up a /24 that is very happily full at the moment and doesn't need to add more work to an already overloaded admin?

If this is confusing in any fashion I'll be glad to do some ASCII art.

Thanks,

Adam

---

### Post by lensman3 on 2009-08-14
Go and google for "Arno's iptables firewall" and take a look at this.  This is one "h*ll" of a firewall.  I just discovered it so my experince level is low.  I run it on a Fedora Core 10 firewall/server machine.  You can restrict ports between multiple ip adresses. 

I don't know if will work for you, but it is worth a look.  It is still under development with an active listserv.

Hope this might help.

---

