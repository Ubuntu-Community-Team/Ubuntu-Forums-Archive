---
title: "Virtual Hosts and DynDNS"
date: 2010-08-18
forum: Server Platforms
---

### Post by spynappels on 2010-08-18
Is it possible to use Virtual Hosts if you have a DynDNS account due to not having  a static Public IP?

If so, what do I need to put in the NameVirtualHost directive and in the names of the virtualhosts?

---

### Post by Bachstelze on 2010-08-18
If you use the default Ubuntu Apache configuration, you don't need to touch the NameVirtualHosts directive.  Just create VirtualHost blocks just like you would on a "normal" IP.

---

