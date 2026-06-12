---
title: "Discovering Users and Connecting (Ldap)"
date: 2008-09-09
forum: Server Platforms
---

### Post by chrispottrell on 2008-09-09
Hi guys,

I've got approximately 30 clients which are running from my Ubuntu server, I followed ricky's excellent openLdap discussion on the forums to get to this point.

I think/hope this is more of a general question that people have come across before. I'm looking to remotely install software on each machine via a script I have already created. The problem i'm having is finding the machines, for example..

I need to go into the first users computer via ssh and execute a simple script, for each user. Doing this 30 odd times is pretty frustrating.

Is there a way to develop a script to ssh into the user's box by just inputting their username for example?

So I type in "Chris" and it scans the logs for the user "Chris"'s IP address. 

Or am I over complicating things? Is there a simpler way. 

I'm trying to install RainLendar on each of the 30 machines.

---

### Post by HermanAB on 2008-09-09
You have two solutions: DHCP with fixed addresses, or DNS.

You could reconfigure DHCP to always issue the same addresses to each machine - based on the MAC address.  This will work but is a crappy solution at best.

Alternatively, you could give each machine a FQDN and configure each in a local copy of BIND 9, so that each machine name will resolve on the LAN.  Then you need to set each machine to point to this DNS only, through DHCP.

The DNS method is better.

Cheers,

Herman

---

### Post by chrispottrell on 2008-09-09
> **HermanAB said:**
> You have two solutions: DHCP with fixed addresses, or DNS.

You could reconfigure DHCP to always issue the same addresses to each machine - based on the MAC address.  This will work but is a crappy solution at best.

Alternatively, you could give each machine a FQDN and configure each in a local copy of BIND 9, so that each machine name will resolve on the LAN.  Then you need to set each machine to point to this DNS only, through DHCP.

The DNS method is better.

Cheers,

Herman

Option 2 sounds do-able.

So you have the FQDN for the machinenames via a local copy of bind.. how then would you find out who is logged in on what machine to then install the software remotely via the script?

Many thanks for your help.

---

