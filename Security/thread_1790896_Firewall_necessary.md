---
title: "Firewall necessary?"
date: 2011-06-25
forum: Security
---

### Post by Zomby Woof on 2011-06-25
I am currently on a home VOIP router that has NAT and some minor "firewall" features. Would there be any advantage to connect my home network to that router through an iPcop firewall machine? And/or I could put the iPcop firewall on the output of my cable modem and put the home network on one subnet and the Voip router on a DMZ. Am I over complicating things?

---

### Post by Dangertux on 2011-06-25
You might be overcomplicating it a little bit. However , it really depends on how many machines you have and how you want your network set up.

It also depends on the functionality of your existing VoIP router, for instance if it's a low end router, it probably doesn't really offer much in the way of firewalling outside of the innate discretion that NAT grants.  Where as IPCop can be used as both a firewall (stateful) an IDS , and an intelligent routing instrument. So if it's baseline security you're looking for the IPCop probably offers you more in the way of features, again depending greatly on what exactly your VoIP router offers. 

If it was me personally, I would use the IPCop to separate the two networks IE: everything VoIP on one network (not necessarily dmz'ed but a seperate network). Then all your personal equipment on a different network. The reasoning behind this is you don't really want a direct routing path from your VoIP to your home network.


                                                                       Edit: My diagram didn't come out right more explanation coming lol...

Ok so for lack of an awesome ascii diagram I made I will instead attempt to explain what I came up with in my head...

Internet connecting to IPCop Box

Route from internet to 3 different networks , for instance 192.168.0.x (home network) , 172.0.0.x ( Voip Network Using the VoIP router or not) , 10.0.0.1 (Optional DMZ or wifi network).

Seperating your networks in such a manner will help isolate penetration if it does occur, using the IPCop at the front line you can also run an IDS on it which makes it relatively easy to monitor all network traffic, as opposed to just a portion of it, which would occur if your VoIP router is in front. Just how I would do it if I wanted a paranoid home security set up.

Granted this is a bit paranoid and would require your IPCop box have 4 network interfaces. However, if I was on a binge to secure my home network I would do something along these lines.

---

### Post by Zomby Woof on 2011-06-26
That's exactly what I was thinking. I wanted to make sure I wasn't overcomplicating my network.

---

