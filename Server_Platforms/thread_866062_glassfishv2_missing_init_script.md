---
title: "glassfishv2 missing init script"
date: 2008-07-21
forum: Server Platforms
---

### Post by rogier.de.groot on 2008-07-21
Hi all,

I've just installed GlassFish V2UR1 from the repositories. During installation it created a domain in /var/lib/glassfishv2/domains. After I rebooted the server, glassfish was no longer running, and there was no init script to start it. When I try to get it running with "asadmin start-domain domain1" it creates a new domain directory in /home/user/glassfishv2.
How do I get glassfish to start with the original directory?
Preferably running as a seperate user?

TIA

---

