---
title: "How often are Apache minor versions updated in Ubuntu?"
date: 2014-05-01
forum: Server Platforms
---

### Post by jonathan.leo.pierc on 2014-05-01
I'm in the process of switching our www infrastructure to use Ubuntu Server because of the Apache 2.4 support. Trusty is currently at v2.4.7, but there's a change in v2.4.9 that I really need (Unix socket support for mod_proxy_fcgi, for the curious). Does anybody know off-hand or from personal experience if minors get updated, and if so, how often?

Yes, I could certainly compile and maintain my own version, but that's a pretty huge reason why I'm trying to switch. (If I had to do that, I'd switch back to CentOS just because of how easy it is to build Apache RPMs to replace the native ones.)

Thanks!

---

### Post by TheFu on 2014-05-02
a) switching distros over a signal program seems crazy to me.
b) To be on the bleeding edge, use a PPA for the packages. Building your own really shouldn't be needed 99.99999% of the time. That's just crazy talk and why PPAs were invented.
c) NEVER install .deb/.rpm packages stand-alone. Doing that will break dependencies - if not now, later and the machine will end up in "RPM Hell" (there is a "DEB Hell" too).

---

