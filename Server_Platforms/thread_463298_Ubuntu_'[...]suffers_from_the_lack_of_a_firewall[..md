---
title: "Ubuntu '[...]suffers from the lack of a firewall[...]'"
date: 2007-06-03
forum: Server Platforms
---

### Post by Catsworth on 2007-06-03
Hi Guys,

The subject line is part of a quote from a magazine review of several of the main Linux distros, here's the relevant part in full:

> 
[...]In terms of firewalling, we find it unnaceptable that many distros come without a firewall enabled.  Slackware was the worst offender here, because not only does it arrive firewall-less, but it also has five ports open to the world.  **Ubuntu also suffers from the lack of a firewall, but at least it's provided with no open ports and so minimises the attack vectors.**[...]

[RIGHT]- *"Distro showdown", Linux Format, Issue 94, July 2007*[/RIGHT]

The version of Ubuntu under scrutiny was 7.04.

Now.....it's my understanding that Ubuntu (if not _all_ Linux distros) comes with a firewall called *iptables* running, and that the only thing missing by default is a graphical interface for managing it.

I've never written to a magasine before for any reason, but I was thinking of writing in response to this article and putting the record straight.

So.....before I do this:

1.  Am I right, and
2.  What's the best way to explain why I'm right and they're wrong?

I'll be sure to include a credit in my letter for anybody who's information/wording makes it into the final response :D

Cheers.

---

### Post by Wim Sturkenboom on 2007-06-03
You're wrong.
My Ubuntu Dapper does not have iptables configured by default; only when I start my PPPoE, they get configured. Same for my Slackware 10.2.
So having iptables running without configuring them is the same as not having a firewall.

---

### Post by Brazen on 2007-06-03
Actually Iptables is just the command line interface for working with the firewall.  Netfilter is the actual firewall component, and yes it is a part of the kernel and therefore a part of every distrobution, but some distros leave it unconfigured (essentially, turned off).  Redhat does configure the firewall by default, but it leaves a few incoming ports open, so I don't see how they could be less critical of that than a distro that leaves the firewall off but only has a few daemons listening on outside interfaces.  The end result is the same anyway.  Personally though, I always turn on the firewall as one of the first things I do on an Ubuntu machine and I close up the default ports on Redhat boxen.

To learn more, go here: [http://www.netfilter.org/](http://www.netfilter.org/)
Some parts of that site get really technical though, IIRC.

---

### Post by Catsworth on 2007-06-04
Ok guys, thx.

---

### Post by PetePete on 2007-06-04
but is there really any need for a firewall to block ports if you dont have any ports open in the first place?

or maybe you want to drop ICMP etc.

---

### Post by eentonig on 2007-06-04
I'm behind a NAT and I don't have any public services open. Why should I waist system ressources on running a firewall that isn't going to protect anything?

---

### Post by darell_m on 2007-06-05
If any one is curious if they are susceptible go and test your setup - use shields up and leak test and try and crack into your own computer. I have an was 100% stealth with FF 7.04
 
[http://www.grc.com/default.htm](http://www.grc.com/default.htm)

---

