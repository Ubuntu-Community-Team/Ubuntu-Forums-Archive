---
title: "Server recommendations"
date: 2009-06-08
forum: Server Platforms
---

### Post by matthewboh on 2009-06-08
I've been doing some volunteer work for the Boys and Girls Club of Frederick and they wanted a File Server put up.  They had also asked for Active Directory - but since this is their one and only server, they agreed it might be better to go with a Linux distro.  I can get a LAMP server up easily enough, but unsure about openLDAP.  They also have a problem with their current router only giving out 5 DHCP leases at a time.  What should I install for them?  Should it be DHCP/DNS/openLDAP and Samba?  Realize of course, that I'm not a network guy.  How hard / easy would this be?  I'll also be install ClamAV, Webmin (or should it be eBox - which Ubuntu seems to be supporting but seems to have problems).

Also - is there a good guide?  Should I go with 8.04 LTS or 9.04?

---

### Post by cariboo on 2009-06-08
I would suggest going with 8.04, as it is supported until 2013. You can set most routers to the number of dhcp ip addresses you need. If yu can't change the setting, I would suggest using dnsmasq, as it is much easier to setup than bind9.

For openLDAP have a look at [this]("https://help.ubuntu.com/community/OpenLDAPServer") howto.

---

### Post by poundjd on 2009-06-08
I would strongly suggest that you take a look at eBox 1.1. This is the latest stable version and has everything you need for a small to medium office.  [WWW.eBox-Platform.com](WWW.eBox-Platform.com) is the link.
-jeff
PS, you may also want to check out what is coming in version 1.2 its pretty cool.

---

