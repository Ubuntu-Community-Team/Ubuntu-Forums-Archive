---
title: "What firewall do you use?"
date: 2007-09-11
forum: The Cafe
---

### Post by nowshining on 2007-09-11
What firewall do you use to setup iptables with. I use arno-iptables-firewall and the reasons are as follows:

1. Easy to setup
2. Can change 1s to 0s to enable and disable in the firewall config
3. Can input your own firewall rules in an easy to use config file - custom.conf
4. Can write up your own plugins
5. Has an Block list to block certain Ips and ranges

And much much more and the custom and block lists are just really copy and paste your own rules and ips in there and restart the firewall, it's really simple allowing both advanced & basic easy setup for beginners. :) compared to Guarddog and the rest such as firestarter I give this 20/10 stars.. :)

---

### Post by executor on 2007-09-11
smoothwall her, on ann old p233 96 ram

---

### Post by stmiller on 2007-09-11
Yeah the arno iptables thing is quite nice. Though at the moment I'm just using dd-wrt on my router.

---

### Post by some_random_noob on 2007-09-11
I don't bother, I'm behind a router anyway. Sometimes using IPTABLES via the commandline is good for blocking ad servers. But aside from that, I have no reason to use a "firewall".

---

### Post by LookTJ on 2007-09-11
iptables on my router....dd-wrt

---

### Post by n3tfury on 2007-09-11
WRT54GL and DD-WRT v24 Beta std (SVN revision 7457)

---

### Post by RandomJoe on 2007-09-11
I use my fingers! :lolflag:

Back when I first set up my firewall box, there were no snazzy interfaces.  Was a right pain learning (what was it at first?) ipfw?  Then ipchains.  And just when I got the hang of that, iptables!  

But now I can whip up changes to my firewall without referring to anything, and the more esoteric stuff is just a quick review of a manpage or website away...

I did try using webmin to administer the firewall on our DSL line at my last job (not the "corporate LAN", just a standalone line we used for various things) so others could more easily make changes.  But in the end I'm happier just ssh'ing in and using the console!

Gee, guess I qualify to start using the "and you kids get off my lawn!" line now! :biggrin:

---

### Post by JBAlaska on 2007-09-11
I'm behind a NAT router as well, but I still like having iptables working for me.

I use Firestarter to modify my iptables, very easy program to setup/use.

---

