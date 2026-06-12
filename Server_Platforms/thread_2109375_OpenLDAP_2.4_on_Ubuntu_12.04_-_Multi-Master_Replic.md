---
title: "OpenLDAP 2.4 on Ubuntu 12.04 - Multi-Master Replication"
date: 2013-01-27
forum: Server Platforms
---

### Post by lewisdsg on 2013-01-27
Hi,

I have searched over the forums, the Ubuntu help guide and the world of Google am still having issues with trying to get OpenLDAP to replicate using the Multi-Master configuration.

The Ubuntu guide shows how to do replication but only does it as a master/slave mode which is not what I am after.

Most other guides show how to do it in slapd.conf which is not supported in the version of OpenLDAP in Ubuntu 12.04. 

Has anyone got this working and has a guide to help me?

Thanks :D

---

### Post by robinsonaarond on 2013-04-19
I am running into this issue, as well.  It doesn't seem to let me make the same server into both a "provider" and a "consumer," but if you only set two servers up as "consumers" of each other, they don't seem to replicate the data across.

And I have had the same struggle to find any documentation on this.  Someone wrote the software; there isn't even documentation in the manual to cover this kind of use-case?

---

