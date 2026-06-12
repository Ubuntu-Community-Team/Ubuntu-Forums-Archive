---
title: "Moving from FreeBSD to Ubuntu on a gateway machine"
date: 2009-01-24
forum: Security
---

### Post by kestasjk on 2009-01-24
Hello,

I've been using FreeBSD for our home's local gateway machine for as long as I can remember. I prefer Ubuntu to FreeBSD a lot, and I'd like to move to something easier to maintain and with more support than FreeBSD, which can be a hassle sometimes.

The problem is I'm using PF as my firewall on FreeBSD, and it's excellent. I've got packet queueing set up, NAT, port redirects, as well as having a very nice firewall which gets the security vs convenience just right and fits in seamlessly with the NAT.

So that is what has always held me back from moving over; whenever I've looked at trying to learn iptables to replace pf I've been amazed by how complicated it is, and the firewall GUI tools are far too simplistic to use on a gateway machine.


Here is my pf.conf: 
[http://kestas.kuliukas.com/pf.conf/pf.conf.template.txt](http://kestas.kuliukas.com/pf.conf/pf.conf.template.txt)

I'm not looking for someone to give an iptables translation of course, but has anyone been in the same situation and can anyone tell me if it'd be worth trying to learn iptables?

Thanks,
Kestas

---

### Post by mikewhatever on 2009-01-24
While iptables is complicated indeed, take a look at ufw.
[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

