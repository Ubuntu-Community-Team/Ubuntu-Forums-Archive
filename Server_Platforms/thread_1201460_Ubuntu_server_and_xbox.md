---
title: "Ubuntu server and xbox"
date: 2009-07-01
forum: Server Platforms
---

### Post by prongs_386 on 2009-07-01
Hi there, I know there have been threads regarding the xbox 360 here before but none of the ones I've seen have the same problem as me.

I'm running ubuntu server 9.04 as a gateway, so I have my two nics connected to the router and all other devices connected to the same router via cable or wireless.

The problem with the xbox is when it uses my server as a gateway it complains that the MTU setting is too low.
The modem mtu is 1492 and by default both my nics were set to 1500.
I tried specifically setting them to 1492 but that didn't fix the problem.

If I set the gateway to be the router from the xbox it works perfectly.

Is there something I'm doing wrong or any fix for this mtu problem?

Thanks

---

### Post by prongs_386 on 2009-07-12
bump.

Something I thought might be an issue is mss, so i had that clamped to mtu.. but still no luck.

Its nothing to do with the network interfaces on the devices, they all have correct mtu settings... I think it might be iptables/nat doing something funny.

---

### Post by prongs_386 on 2009-08-17
Ok, with a bit more of a look into it i think it might be some thing to do with the firewall and icmp.
The xbox ends an icmp ping in order to determine mtu, if that ping can't get out then the mtu test will fail.

My problem is i've tried all sorts of settings and I just can't achieve anything by adding rules to accept icmp.

Does anyone know how i can allow icmp to get back through the firewall to the xbox?

---

### Post by prongs_386 on 2009-08-26
Ok, I have solved the issue.

It was due to ICMP packets not being allowed through the firewall properly. The default settings from webmin actually do work with the xbox.. I had just put my own settings in which stuffed it up.

---

