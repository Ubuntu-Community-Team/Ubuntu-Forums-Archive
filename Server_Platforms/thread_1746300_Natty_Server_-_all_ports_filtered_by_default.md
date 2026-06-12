---
title: "Natty Server - all ports filtered by default?"
date: 2011-05-01
forum: Server Platforms
---

### Post by shades3 on 2011-05-01
Hi there. I tried to find a similar thread or a solution, but came out empty-handed...

I just finished setting up a Natty box to act as my home router / home web server. I installed beta2 a few days before the final was out and updated all of the packages (also tried a dist-upgrade just in case :P).

I performed the following setup:

- set up the webserver and sshd
- set up dhcp server and adressing
- set up rc.local to run rc.firewall with my filtering rules
- set the router live (rebooting it)

And that was basically it. Everything worked fine, except when I tried to open any of the sites that are hosted on the webserver from the outside world. It turned out that all of the ports on the external interface were blocked.

I decided to stop my firewall rules (flushing all rules) and then scan my box from the outside - still, all ports seemed to be filtered. I then decided to reboot the machine, disabling all mention of the rc.firewall script, but the ports were still filtered!

I then disabled apparmor and made sure ufw is disabled, but the ports are still filtered for the outside world. For the internal network they are not filtered.

Is there some other mechanism besides iptables rules that filteres packets?

---

### Post by falko on 2011-05-03
Please check your router's firewall.

---

### Post by ian dobson on 2011-05-03
Hi,

Check you router settings or see what your ISP (internet service provider) allows. Many block the "usual ports" (25,110,80,443)

Regards
Ian Dobson

---

