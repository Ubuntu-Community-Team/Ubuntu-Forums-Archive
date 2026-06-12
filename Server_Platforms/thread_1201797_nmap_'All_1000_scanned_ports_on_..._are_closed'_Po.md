---
title: "nmap: 'All 1000 scanned ports on ... are closed' Potential security problems?"
date: 2009-07-01
forum: Server Platforms
---

### Post by PryGuy on 2009-07-01
Good day, everyone!

I have a question: I have nmapped my server with firewall from the outside and it said:> All 1000 scanned ports on XXX.XXX.XXX.XXX are closed I do not have open ports and there is ```
iptables -A FORWARD -o $LAN -m state --state RELATED,ESTABLISHED -j ACCEPT
``` that works fine for me. I'm building a nice and secure firewall and my question is: are there potential problems that I shoud worry about? Your suggestions are very welcome here!

---

### Post by PryGuy on 2009-07-02
Anybody? Please...

---

