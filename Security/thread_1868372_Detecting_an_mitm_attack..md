---
title: "Detecting an mitm attack."
date: 2011-10-24
forum: Security
---

### Post by FOn1NbX244 on 2011-10-24
Is it possible to detect an mitm attack using traceroute to the gateway?...Let's say the attacker is using ettercap.What other ways to detect a middle man?

---

### Post by emiller12345 on 2011-10-24
First of all, you should examine the man page for ettercap.
```
man ettercap
```
it looks like there are 4 different types of ways of preforming a mitm.  looking for this packets on your network is probably a good indicator of a mitm(/attempt).

---

### Post by Dangertux on 2011-10-24
Detecting a man in the middle attack can be extremely difficult, or extremely easy depending on what the attackers objective and level of skill is.

There are a couple of types of MITM to consider.

If you're talking about a MITM attack via arp spoofing with SSL involved your task becomes a little bit easier.

You will be looking for key signatures on SSL certificates, it is unlikely that the attacker will have the correct signature, and you will likely be presented with a warning in your browser or SSH or whatever your method for creating a secure connection is.

If you're dealing with the same but in an unencrypted environment it becomes almost impossible to detect, though the traffic could be just as easily sniffed so a MITM is much less likely under these conditions.

If you're dealing with dns poisoning you can do so by comparing traceroutes and nslookups on what you feel is the victim versus an uncompromised third party. Bear in mind loadbalancing techniques when testing this.

If you're getting into packet injection with things like airpwn, you can essentially track the race condition created. Packets will not be able to be blocked to the destination so you will be receiving ACK from both the destination and the "man in the middle" you can detect this relatively easily by use of tcpdump or wireshark.

I hope this helps.

---

