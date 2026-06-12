---
title: "how to build a super computer?"
date: 2010-02-13
forum: Server Platforms
---

### Post by userkiller on 2010-02-13
Am trying to build a main frame computer, in order to learn more about them.

Can any please explain.

---

### Post by Vegan on 2010-02-13
Mainframes are expensive, but obsolete. If you want to run an old IBM 360 or something along those lines, then the Hercules-360 project will work with Windows or Linux and allow you to load VMS or even Linux for the mainframe.

If you want a real mainframe, there are some in some museums that are still plugged in.

---

### Post by jflaker on 2010-02-13
Beowulf cluster.

You can assemble a room of computers running as a cluster

[http://www.flashmobcomputing.org/](http://www.flashmobcomputing.org/)

You can get some good crunching going with a few machines and the more the merrier.

---

### Post by userkiller on 2010-02-13
Am saying i have 4 different servers do all of them have to be the same spec, same brand same specs?

---

### Post by jflaker on 2010-02-14
> **userkiller said:**
> Am saying i have 4 different servers do all of them have to be the same spec, same brand same specs?

For BEST performance...yes.  According the the link, many different types of systems were walked in and it worked well.  If you want good performance, your cluster should be similar and be on a GB Switch.

---

### Post by hessiess on 2010-02-15
Find a few original PS3's (not slimline) and put Linux on them.

---

### Post by userkiller on 2010-02-15
> **jflaker said:**
> For BEST performance...yes.  According the the link, many different types of systems were walked in and it worked well.  If you want good performance, your cluster should be similar and be on a GB Switch.

So, let suppose i have 15 Mbps upstream when am clustering i need a 1000 mbps in order so for the server to communicated at a fast rate?

---

### Post by smc18 on 2010-02-15
The Gb switch is going to be used for the servers in the cluster to communicate between locally on your LAN.  Your 15Mb uplink is most likely your WAN speed, which shouldn't affect the cluster speed at all.

---

### Post by falconindy on 2010-02-15
> **Vegan said:**
> Mainframes are expensive, but obsolete. If you want to run an old IBM 360 or something along those lines, then the Hercules-360 project will work with Windows or Linux and allow you to load VMS or even Linux for the mainframe.

If you want a real mainframe, there are some in some museums that are still plugged in.
Mainframes are hardly obsolete. You'll find one running just about every financial institution. My last job had a Unisys NX series running Clearpath/MCP. [SunGard](http://www.sungard.com/), a company in eastern PA, handled our disaster recovery. I remember going there one weekend and being "greeted" by a room larger than my house full of mainframes and peripherals.

That said, they're **damn** expensive because of what goes into them. Given equivalent price, and comparing a mainframe to a top end computer today, you'd get better processing power out of the desktop.

---

### Post by arvevans on 2010-02-16
This might be interesting if you are just looking for more computing power.

[INDENT][http://www.calvin.edu/~adams/research/microwulf/]("http://www.calvin.edu/~adams/research/microwulf/")[/INDENT]

Clusters are a way to make several motherboards work as a team.
_._

---

### Post by userkiller on 2010-02-28
> **arvevans said:**
> This might be interesting if you are just looking for more computing power.

[INDENT][http://www.calvin.edu/~adams/research/microwulf/]("http://www.calvin.edu/~adams/research/microwulf/")[/INDENT]

Clusters are a way to make several motherboards work as a team.
_._

Ok thanks i read everything.

---

