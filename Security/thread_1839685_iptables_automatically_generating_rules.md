---
title: "iptables automatically generating rules"
date: 2011-09-06
forum: Security
---

### Post by blort on 2011-09-06
Hi

I'm using 10.04.

I can't access hostgators cpanel without dropping my firewall. That's annoying enough, so I drop my firewall with script that clears my iptables rules.

Trouble is, every few minutes, the old rules come back into existance. This also stops me from ssh'ing around my network.

I've got a script with the iptables rules that I want. This script lets me have ssh access, and access to hostgator's cpanel (which is just a web service over port 2082).

How do I prevent old, useless iptables from coming back from the dead?

---

### Post by bodhi.zazen on 2011-09-06
You have a "script" that seems to be malfunctioning and you want us to tell you why ?

What services do you have installed, what script are you running ?

---

### Post by CharlesA on 2011-09-06
+1 to malfunctioning script.

iptables rules wouldn't "automagically" be applied unless there was script running that reapplies them or something else is not set up right.

---

### Post by The Cog on 2011-09-07
I don't know for sure as I've never used either, but I would suspect that you have firestarter or ufw installed, and that is re-writing iptables with its own rules. 

I think you need to find out which firewall application you have installed, and disable / remove that if you want to use your own script instead. You will probably need to use "completely remove" in synaptic, to ensure that the relevant firewall configuration files are also removed.

---

