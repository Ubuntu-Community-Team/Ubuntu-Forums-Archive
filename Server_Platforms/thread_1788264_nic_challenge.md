---
title: "nic challenge"
date: 2011-06-22
forum: Server Platforms
---

### Post by expatCM on 2011-06-22
just fishing for ideas ....

I have just had to change a motherboard.  Replaced with the same make and model.  One nic onboard and one as a separate card.  From past experience I know that the nic will not work until the old entries have been removed so I went to /etc/udev/rules.d/70-persistent-net.rules and cleared out the entries and rebooted.  New entries created ..  no problems.

I look at ifconfig and can see both cards.  If I ping google.com I can get an echo and there is rx and tx activity there so I know the wan facing card is working.  The other card faces the lan (onboard).  If I ping a client I get nothing.  There is no rx or tx activity.

As a test I installed an extra nic and renamed it as eth0 swapping with the onboard card.  However ...  no joy, the card also has no activity.

I do not understand why this should be since I have changed nothing at all.

Am I doing something really stupid or have I missed a step?

---

### Post by YesWeCan on 2011-06-22
Hi. Don't know. Have you checked your routing table? What if you swap the cables over, does the problem follow the card?

---

### Post by expatCM on 2011-06-22
Thanks for your suggestion.  Could I just confirm that I understand.

What you are suggesting is that if the problem stays with the cable then there may be an issue with the SATA port? (or the cable)

I can take a look at the routing table but where do I find it?

---

### Post by bab1 on 2011-06-23
> **expatCM said:**
> Thanks for your suggestion.  Could I just confirm that I understand.

What you are suggesting is that if the problem stays with the cable then there may be an issue with the SATA port? (or the cable)

I can take a look at the routing table but where do I find it?

If you have a host with 2 operating interfaces then by definition you have a multi-homed host (a gateway (router)).  Have you set this up to forward packets back and forth between the 2 interfaces?

SATA is what defines the bus (connection) on a hard drive.  What does that have to do with this situation?  Now I'm confused.

To see the routing table from the terminal try this```
route -n
```

---

### Post by YesWeCan on 2011-06-23
> **expatCM said:**
> Thanks for your suggestion.  Could I just confirm that I understand.

What you are suggesting is that if the problem stays with the cable then there may be an issue with the SATA port? (or the cable)

I can take a look at the routing table but where do I find it?
Just to make sure the problem is to do with the interfaces and not the network they are attached to. Probably not the issue but an easy thing to eliminate.

Would post the output of [COLOR="Blue"]route -n[/COLOR] and [COLOR="Blue"]sudo iptables-save[/COLOR] and [COLOR="Blue"]ifconfig[/COLOR] and [COLOR="Blue"]cat /etc/network/interfaces[/COLOR]

---

