---
title: "Firestarter Question....semi advanced I guess"
date: 2011-03-29
forum: Security
---

### Post by Dalek Draco ON LINUX on 2011-03-29
hey,  so I've installed firestarter to try and increase my network security (I've had a few mates getting attacked recently, and I figured given my needs are so basic (pidgin messenger, firefox, updates, etc) I might as well clamp my computer down like a vice barring those things.  

So I've set firestarter to restrictive by default, whitelist traffic. Now I want to be able to run pidgin messenger, empathy, chromium and firefox. 

So I have:  

Inbound: unchanged from default  

Outbound: Allow connections to:  - 
Allow service: 
http 80 192.168.X.Y (which allows firefox, pidgin and updates I assume)

msnp 1683 everyone (which allows pidgin I think)

https 443 192.168.X.Y (to allow yahoo mail I think)

unknown 843 192.168.X.Y (yahoo mail)

mmcc 5050 192.168.X.Y (yahoo mail).

Is this ok? I seem to be able to connect to pidgin, firefox and update my system etc. Does this mean I've got an uber secure firewall, or have I put a big hole in my security?   Any help would be appreciated.

---

### Post by uRock on 2011-03-29
Firestarter is out dated. If you have a router and haven't forwarded any ports, then you don't need a firewall installed.

---

### Post by Dalek Draco ON LINUX on 2011-03-29
> **uRock said:**
> Firestarter is out dated. If you have a router and haven't forwarded any ports, then you don't need a firewall installed.

hm that awkward moment when I've wasted my time :S. Thanks lol.

---

### Post by d3v1150m471c on 2011-03-29
> **uRock said:**
> Firestarter is out dated. If you have a router and haven't forwarded any ports, then you don't need a firewall installed.

IMO it's a good idea. Contrary to popular belief, unwanted connections can still come across a router. Secondly, i don't know if he's using wireless, has a laptop and takes it to wireless hotspots, etc., but "internal" threats are still threats. Third, yes firestarter is no longer maintained but i've been using it forever and a day, the source code is available, and it's just a graphical front-end for iptables which is preinstalled. Unless he's installing shady code on his system firestarter not being maintained is hardly a problem. Third, say his system does become compromised or a program wants to obtain access without his knowing or permission, a firewall is absolutely important when it comes to mitigating this.

---

### Post by Soul-Sing on 2011-03-29
> Unless he's installing shady code on his system firestarter not being maintained is hardly a problem

software not being maintained is hardly a problem?
software not being maintained is always a problem. Firestarter has
its bugs on launchpad, and they are "left alone..."

---

### Post by Grenage on 2011-03-29
> **d3v1150m471c said:**
> IMO it's a good idea. Contrary to popular belief, unwanted connections can still come across a router. Secondly, i don't know if he's using wireless, has a laptop and takes it to wireless hotspots, etc., but "internal" threats are still threats. Third, yes firestarter is no longer maintained but i've been using it forever and a day, the source code is available, and it's just a graphical front-end for iptables which is preinstalled. Unless he's installing shady code on his system firestarter not being maintained is hardly a problem. Third, say his system does become compromised or a program wants to obtain access without his knowing or permission, a firewall is absolutely important when it comes to mitigating this.

Isn't that what apparmour is for?

---

