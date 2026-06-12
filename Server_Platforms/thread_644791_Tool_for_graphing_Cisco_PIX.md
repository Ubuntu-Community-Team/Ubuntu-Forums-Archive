---
title: "Tool for graphing Cisco PIX"
date: 2007-12-19
forum: Server Platforms
---

### Post by lee_connell on 2007-12-19
What is a useful tool that will monitor a cisco pix most likely by SNMP where I would be able to look at all the internal IP's making outgoing connections and the bandwidth usage and all external IP's coming in?

I would like to see something that would list all the IP's that the PIX see's and then graph it.  Reason for this would be to determine which IP is the culprit for causing high download streams.

-thanks

---

### Post by xdice on 2007-12-20
> **lee_connell said:**
> What is a useful tool that will monitor a cisco pix most likely by SNMP where I would be able to look at all the internal IP's making outgoing connections and the bandwidth usage and all external IP's coming in?

I would like to see something that would list all the IP's that the PIX see's and then graph it.  Reason for this would be to determine which IP is the culprit for causing high download streams.

-thanks

Have you looked at 'ntop'?  That would do what you want, albeit from server side, rather than looking at the pix. You may have to run ntop on a server that's connected to the same VLAN/network where you suspect the traffic is coming from.

Oh a higher level, I use Cacti on my production PIX firewalls - I have them setup to graph all active interfaces.  With that info showing me which interface has the high usage, I would know where to run ntop at, which will show me the bandwith-using culprit in short order.

Darkstat is another option that is similar to ntop, but Synaptic mentions that darkstat is more stable than ntop.  Both are available in synaptic, however.

Overview for ntop here: [http://www.ntop.org/overview.html](http://www.ntop.org/overview.html)

---

### Post by lee_connell on 2007-12-21
Hi xdice,

I am familiar with ntop, the only problem here is if the network is on a switch, doesn't the switch filter out all that broadcast traffic?  This would mean ntop wouldn't capture all data right?

I am also familiar with setting cisco switches up to send all traffic to a "monitor" port which could plug the computer in on that port and run ntop.  What if I had a switch that didn't have that capability what to do then?

---

### Post by mellowd on 2007-12-21
MRTG, great tool

---

### Post by xdice on 2007-12-21
> **lee_connell said:**
> Hi xdice,

I am familiar with ntop, the only problem here is if the network is on a switch, doesn't the switch filter out all that broadcast traffic?  This would mean ntop wouldn't capture all data right?

Yes, which is why I use Cacti and Ntop in tandem when needed.

One thing I failed to mention in my prior message - if your switch supports SNMP, then Cacti can graph the active ports of the switch, which may give you another way to track down the person over-using bandwidth.

> **lee_connell said:**
> I am also familiar with setting cisco switches up to send all traffic to a "monitor" port which could plug the computer in on that port and run ntop. What if I had a switch that didn't have that capability what to do then?

Using a monitor port is precisely how I do it at work.  If your switch doesn't have that capability, then it will be more of a trial-and-error process.  This can be made easier, depending on the compleity of your network, if you can view the arp table of your switch (sh cam dynamic for a cisco switch, for example.).  Since I don't know how complex your network is, it's hard to make a stronger recommendation as to which way to solve the issue.  

I would at least get Cacti setup - it's pretty simple to do so, and I know there is an excellent template set specifically for the PIX firewalls (I use it myself.).  That will get you started collecting stats (if you haven't already, of course.).

---

