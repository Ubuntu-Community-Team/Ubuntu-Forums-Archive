---
title: "How to use and install Honeytrap/Honeynet/Honeyd"
date: 2009-10-21
forum: Security
---

### Post by -Sky on 2009-10-21
Hey there, does any one knows what exactly it works?
What i know about these are:
They creates virtual network to "trap" intrusions.

But i don't know how it works, how it's done, how to make it work, what do i need. eg. server?
because recently I kept getting intrusion attacks triggering on my firewall. so my friend suggested me using this.

---

### Post by unspawn on 2009-10-21
> **-Sky said:**
> recently I kept getting intrusion attacks triggering on my firewall. so my friend suggested me using this.
Your friend should read less Marvel comics and more basic security docs. Instead of playing games you should invest time in hardening your machine, firewall it properly, maybe use fail2ban or equivalent and maybe deploy an IDS like Snort. 

* It's not like I'm telling you that you shouldn't run a honeypot but it's not necessary and it's not the first thing you should look at.

---

### Post by ACagliano on 2013-02-10
A honeypot is not at all easy to set up. Nor is it entirely a trap. A honeypot is set up to emulate certain services that hackers tend to exploit. This serves two functions. First, it distracts them, at least for a time, from your actual computer. Second, it allows you to log the activities of the hackers and determine how they operate. Honeypots are often represented by Hollywood as "counter-attacking tools" that launch an attack on the attacker, but this is not accurate. These counter-attack tools are set up by experienced hackers and may or may not be TRIGGERED BY the scan of a honeypot, but this is not a necessity.

What you are thinking about is an "intrusion detection" program. Intrusion detection programs detect things like pings and port scans on your computer and can be set up to respond to the attack. This may be to stealth the ports on your computer or it may be to run a counterattacking script. My personal advice, being in the internet security field, is to set up "iptables" or your firewall of choice, then to install and configure "PortSentry" to run in audp and atcp modes, set its TCP and UDP action to "Block", and set it to interact with your firewall when it detects a threat (default action is to pass a deny rule). PortSentry is a pretty good intrusion detection program and will protect you from pretty much everything except a really determined hacker.

---

### Post by wildmanne39 on 2013-02-10
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

