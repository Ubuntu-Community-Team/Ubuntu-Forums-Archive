---
title: "securing the network"
date: 2007-03-21
forum: Server Platforms
---

### Post by jeisma on 2007-03-21
hi!

just wondering if this basic setup is secured?

email  \
proxy  ---- router --- internet
web    /

i was told that the servers behind the router is already firewalled, but..

i was thinking like:


email  \
proxy  ---- firewall --- router --- internet
web    /

and then perhaps, maintain the firewall on the servers/services behind the main firewall..

may i know your thoughts?


thanks!

joey

---

### Post by Mr. C. on 2007-03-21
Your question can't be answered yes/no.

Security isn't just about the devices or their connections.  It is very much about how you manage the services, firewall, policy, and understand the risks associated with each.

Your "router" I presume is a consumer commodity router, that likely has a built-in firewall.  If so, then adding a second adds some complexity to your setup, but not necessarily any more protection.  If your router is a pure L2/L3 router, then a firewall would be appropriate.

If you have more defined needs or questions, let's here them.

MrC

---

### Post by jeisma on 2007-03-21
hello!

thank you for the reply. really, my question is very subjective.

router is cisco 805. im not sure if this is L2/L3 (how am i supposed to know?)

i believe packet filtering is enabled on the router.

is this enough to prevent intrusions?


thanks!

joey

---

### Post by Mr. C. on 2007-03-21
You're welcome.

But again, we're back to the Yes/No questions!

I would suggest some reading and learning about the basics of TCP/IP, firewalls, and routers in general.  Someone like yourself should be able to lookup the Cisco 805's capabilities.

Ask yourself a question - how can you feel secure, if you don't know what your own hardward does!

MrC

---

### Post by jeisma on 2007-03-21
thanks.

alright. so i guess i have to get a lot of reading first before i even consider modifying what i have right now.


thanks again!


joey

---

