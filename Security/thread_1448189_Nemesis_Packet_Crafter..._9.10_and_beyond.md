---
title: "Nemesis Packet Crafter... 9.10 and beyond?"
date: 2010-04-06
forum: Security
---

### Post by EJeanmaire on 2010-04-06
Has anyone been able to successfully install Nemesis (nemesis.sourceforge.net) in Karmic or newer?

---

### Post by Kinstonian on 2010-04-06
> **EJeanmaire said:**
> Has anyone been able to successfully install Nemesis (nemesis.sourceforge.net) in Karmic or newer?

Nope, I haven't tried.  However, I think [scapy](http://www.secdev.org/projects/scapy/) is what most people use now, so you might want to give that a try instead, if you haven't already.

---

### Post by EJeanmaire on 2010-04-06
> **Kinstonian said:**
> Nope, I haven't tried.  However, I think [scapy](http://www.secdev.org/projects/scapy/) is what most people use now, so you might want to give that a try instead, if you haven't already.

I like Scapy, however it doesn't have a nice clean bash command line interface (As far as I know), you have to use the interpreter, or code everything in python calling the scapy libraries.

---

### Post by Kinstonian on 2010-04-06
> **EJeanmaire said:**
> I like Scapy, however it doesn't have a nice clean bash command line interface (As far as I know), you have to use the interpreter, or code everything in python calling the scapy libraries.

In that case, you should probably post details of why you can't install Nemesis, such as the error message so someone can better help you.

---

### Post by EJeanmaire on 2010-04-08
Nemesis is old, relies on old libraries like libnet, and appears to no longer be supported.  Subsequently I did not post my many methods of failure in attempting to get it to install/compile.

However, if anyone else is looking for a packet crafting tool that can be easily used in Bash scripting, try nping, which comes with the latest dev version of nmap (5.30 Beta 1).

[http://www.nmap.org/nping](http://www.nmap.org/nping)

---

