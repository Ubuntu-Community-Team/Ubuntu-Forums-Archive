---
title: "DNS server syncing"
date: 2007-11-07
forum: Server Platforms
---

### Post by bss on 2007-11-07
I have a network setup shown in the attached *.txt file below.
I want to sync my app web server's DNS (webapp.td domains)  to Primary DNS (hosting domains + synced webapp.td domains) and then this one to my secondary DNS server (all domains)...

Does anyone know of a good dns setup (maybe zone transfers or something like that).

To describe my setup:

I have a WEB server wich has it's own DNS server. I want to install another DNS server any sync all domains from WEB server to sec.dns server. But I also have an APP web server which has its own DNS server for 1 domain and it's subdomains.  Now i want to sync this one to the WEB server's DNS which is later synced to my Sec. DNS server.

Thanx for any answers...

---

