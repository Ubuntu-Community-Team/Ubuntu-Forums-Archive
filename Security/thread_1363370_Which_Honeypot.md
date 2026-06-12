---
title: "Which Honeypot"
date: 2009-12-24
forum: Security
---

### Post by iamgeniusrnti on 2009-12-24
So I have this old PC and was running Smoothwall for a few weeks.  It was fun but the computer ultimately slowed down my overall Internet connection and I just got bored.

So I'm thinking about installing Ubuntu with either Snort or a Honeypot.  I am intrigued by teh idea of the honeypot and am thinking of giving that a whirl.

When I went into Synaptic, I discovered there is the infamous Honeyd but then there were a few others that popped up like Labrae?  Which one of these projects are you guys using?

---

### Post by __p1n__ on 2009-12-24
What are you trying to do?  Snort is an IDS and honeyd is a tarpit; both are quite different.

The utility of a tarpit on a private LAN that sits behind a firewall that's configured to drop unsolicited inbound connection requests is not that great IMHO.  If you're just curious about potentially bad traffic *within* your LAN then you'll get more mileage out of Snort.

Labrea was the original tarpit that was used to embarrass Gregor Freund's zonealarm firewall (a toy security app that only filtered winsock traffic and not all traffic) however it hasn't been touched since 2003.  Honeyd is a modern tarpit with a lot more functionality.  It was last updated in 2007.

To my understanding the idea behind a tarpit is to tie up an attacker who's trying to reconnoiter your network by forcing his probes to wait until a timeout occurs to complete rather than getting instant feedback.  Practically speaking just set your external firewall to drop unsolicited inbound tcp and udp traffic (with the possible exception of ports 80/443 if you're running one or more webservers) and you won't see the attack probes let alone need to slow the recon down.

If all you want to do is tie up incoming connection requests then you don't need a tarpit: just use netcat instead.

Have fun.

---

### Post by bodhi.zazen on 2009-12-25
See these pages (I only linked the first of 3)

[http://www.securityfocus.com/infocus/1659](http://www.securityfocus.com/infocus/1659)

I would say, the answer to your question depends on what you want to do with collecting the information a honeypot has to offer.

If you are just wanting to explore the concept, try them all =)

In general, with something like a honey pot, use the latest available application, installing from source if necessary.

You might have more fun with DVL 

[http://www.linux.com/archive/articles/60267](http://www.linux.com/archive/articles/60267)

---

### Post by iamgeniusrnti on 2009-12-26
Sorry about the delay--with the holiday and all. Also sorry about the vagueness of my question. I was running Smoothie (Smoothwall 3) with Snort and a Guardian package which could add potential attackers to the IP Block tables for a certain period of time.
 
Then the damn Smoothie crashed after reboot and I lost all my configs... not the worst that could happen, I was bored with it anyways but since I have this old box, I may as well try something different. I am using a run of the mill router (DGL 4500) which has a standard firewall. What I want to do is DMZ a tarpit and/or forward certain ports to allow certain attacks into the tarpit and then study what the hacker is doing while he thinks he's "in".
 
Drawbacks of this is if he thinks to look at the hardware, he may be discouraged if he finds out he made it into a PIII900 running 256M of Ram.
 
Looks like Ubuntu with Honeyd is the way to go.

---

