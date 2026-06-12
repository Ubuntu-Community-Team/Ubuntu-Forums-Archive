---
title: "Shielddsup at GRC.com shows Ports 20/21 and 500 are visible to the internet."
date: 2013-05-27
forum: Security
---

### Post by Silvertones on 2013-05-27
I just moved from a dialup connection to DSL from Frontier. I have a NetGear 7550 router. When I ran GRC with dialup everything was STEALTH. Now I get that port 20,21 & 500 are visible but blocked. How can I get them so they are also STEALTH. I'm using the FW in the router at MAX. I also still have UFW running. Thanks

---

### Post by CharlesA on 2013-05-27
Closed is the same thing as "Stealth." Steath is just a fancy term Gibson uses to tell you "we probed this port, but got not answer back"

Closed = Packet was rejected with a ICMP packet
"Stealth" = Packet was silently dropped

I wouldn't worry about it, but if you really want to know more information about what ports are open or closed, you could always use nmap.

---

### Post by Silvertones on 2013-05-27
> **CharlesA said:**
> Closed is the same thing as "Stealth." Steath is just a fancy term Gibson uses to tell you "we probed this port, but got not answer back"  Closed = Packet was rejected with a ICMP packet "Stealth" = Packet was silently dropped  I wouldn't worry about it, but if you really want to know more information about what ports are open or closed, you could always use nmap. Well to me STEALTH is like having a house that is invisible on your street vs having a house that is visible but the door is locked. I want to be totally invisible.

---

### Post by CharlesA on 2013-05-27
> **Silvertones said:**
> Well to me STEALTH is like having a house that is invisible on your street vs having a house that is visible but the door is locked. I want to be totally invisible.

No such thing as being completely invisible unless you are not connected to the Internet. Even if you drop ICMP packets, you can still be found if someone is determined enough.

The whole "closed vs stealth" argument is security thru obscurity and does nothing to prevent a determined attacker.

With that being said, if you have no open ports, there is nothing to attack, or why are you concerned about the "totally invisible" vs "door are locked" issue?

---

### Post by Silvertones on 2013-05-29
I used to be invisible with dial-up and with DSL I'm not. Just wondering why. Can I become invisible?

---

### Post by CharlesA on 2013-05-29
> **Silvertones said:**
> I used to be invisible with dial-up and with DSL I'm not. Just wondering why. Can I become invisible?

Check the settings on your router.

---

### Post by Silvertones on 2013-05-29
OK. What do I look for and what do I change? Thanks

---

### Post by CharlesA on 2013-05-29
> **Silvertones said:**
> OK. What do I look for and what do I change? Thanks

Depends on what modem/router you have. Do you know what model it is?

By the way, this is a good read:
[http://www.insanitybit.com/2012/05/30/stealth-ports-or-closed/](http://www.insanitybit.com/2012/05/30/stealth-ports-or-closed/)

---

### Post by Silvertones on 2013-05-29
Netgear 7550

---

### Post by Silvertones on 2013-05-29
OK that made sense to me. Thanks

---

### Post by CharlesA on 2013-05-29
> **Silvertones said:**
> Netgear 7550

> **Silvertones said:**
> OK that made sense to me. Thanks

Welcome.

If you still want those ports "Stealth" - read this:
[http://www.dslreports.com/forum/r27307502-FTP-Port-open](http://www.dslreports.com/forum/r27307502-FTP-Port-open)

---

### Post by Morbius1 on 2013-05-29
Um .... Shields up is finding those ports open on your router - not on your desktop.

---

