---
title: "Server Edition 6.06 LTS and 7.04"
date: 2007-09-15
forum: Server Platforms
---

### Post by dc.manage.service on 2007-09-15
Hi all

What is actually the different between 6.06 LTS version and 7.04? Is the 6.06 is a stable version while 7.04 is beta something like that? The download area doesn't tell me in detail what they are except that the 6.06 has longer support than the other.

Also, if I am using 6.06 LTS as a server and 7.04 as a desktop, can the client still talk to the server ?

I am thinking to move to 6.06 LTS from 7.04 cause what I found that the 7.04 is not stable in term of OpenLDAP stuff. Anyway.

I'm looking forward your comment.

Thanks

---

### Post by elvis on 2007-09-15
6.06 and 7.04 are both stable.  The numbering system in Ubuntu refers to the release date - 6.06 was released in the 6th month (June) of 2006.  7.04 was released in the 4th month (April) of 2007.

"LTS" refers to "Long Term Support".  The Ubuntu team pledge security updates for these releases for 5 years for all "server" packages, and 3 years for all "desktop" packages.  Additionally Canonical offer pay-for support for LTS releases.

Comparatively, standard releases are only supported for around 18 months - 2 years, I believe.

LTS releases are a better option for people running servers in production environments, especially so if they are internet-facing devices.  It means not being pressured to upgrade a machine's base software install for 5 years, which can be tied in nicely with hardware lifecycles (ie: a machine gets one release installed on it, which stays there for it's production life).

7.04 is certainly not beta, nor unstable.  I'm currently using 7.04 as a base for a custom OpenLDAP server system to authenticate other Ubuntu 7.04 clients, as well as Windows and Mac machines.  I've had absolutely no problems with it, nor any compatibility issues with the other operating systems.

Whether you use 6.06LTS or 7.04 is entirely up to you.  For myself, I will put LTS releases on all Internet facing devices in production environments where I don't want to upgrade them frequently.  The only exception to that rule is if the 6.06LTS supplied kernel doesn't support the hardware, then instead I will use the latest release.

For all other machines - either short lifecycle machines, desktops, workstations or other non-Internet facing machines, I'll use the latest stable release.

---

### Post by dc.manage.service on 2007-09-15
Hi Elvis

Thanks for that. I am thinking to use 6.06 LTS for server and then all clients are using 7.04.

I am still struggling with the openLDAP at the moment. The others like DHCP, SSH and DNS are working ok.

Thanks

---

### Post by elvis on 2007-09-16
> **dc.manage.service said:**
> I am still struggling with the openLDAP at the moment. 

What sort of problems are you having?  I have some experience with OpenLDAP and might be able to help.

---

