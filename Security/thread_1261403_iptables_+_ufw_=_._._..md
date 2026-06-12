---
title: "iptables + ufw = . . . ?"
date: 2009-09-08
forum: Security
---

### Post by pi.boy.travis on 2009-09-08
Hi!  OK, I have iptables setup for NAT and IP masquerading.  Can I use these rules in conjunction with ufw rules?  I know that ufw uses iptables. . . will there be conflicts?  Do ufw rules go in their own chain?  And finally, will the ufw rules apply to all packets, even those headed for clients behind the firewall?  Or would it just be easier to bite the bullet and study up on iptables?

Thanks in advance!

---

### Post by cariboo on 2009-09-10
A bump for the move.

---

### Post by koenn on 2009-09-12
since you're planing to try and mix ifw and iptables, i'd say forget ufw and just use iptables

ufw uses some custom chains, so to work out how that interacts with rules you add manually, you'd probably have to dissect the ufw rules anyway, and if your capable of doing that, iptables itself will look easy.

---

### Post by pi.boy.travis on 2009-09-12
Yeah, I tested it, and the ufw chains don't apply to the NAT table, and I'm too lazy to move them, so I'll just write them myself.

---

### Post by bodhi.zazen on 2009-09-13
I agree with the above advice.

iptables is not *that* complicated and if you can write rules for NAT you can write rules for iptables.

You then use iptables-save and iptables-restore

See :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

But mixing and matching between UFW (or any other configuration tool) and writing rules yourself is going to make it more complicated then it needs to be.

---

