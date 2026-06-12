---
title: "Can't join xp to Samba PDC"
date: 2009-11-04
forum: Server Platforms
---

### Post by wiz561 on 2009-11-04
Hi,

I've been pulling my hair out for the past day on this.  I've followed the document here.

[https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix](https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix)

to an absolute T.  I've tried this on Ubuntu 9.10 and 8.04.3 and I get the same exact results.  Everything works good; I can do the ldapsearching and auth to ldap from ssh on other ubuntu workstations.  However, the problem exists whenever I try to join a windows xp workstation to the domain.  I've tried two workstations and I get the same exact message.  On the workstations, it says "The user name could not be found".  However, on the samba server, it creates the computer account in the directory tree.

I have a funny feeling that it might be related to a dns problem, since I'm not running a DNS server (locally).  The community docs don't mention it.

If anybody can help me with this, that would be great!!

Thanks!

---

### Post by ixe on 2009-12-17
I'm not sure if this will help you or not, but this is a problem that I ran into when trying to join a WinXP client to a domain controlled by my OS X 10.6 server (Samba 3.0.28a-apple running inside). 

I was trying to use a domain name like "mydomain.local" but this caused the XP machine to attempt to use the normal DNS-based locator instead of the old NetBIOS method (which samba seems to deal with much better). It would try to lookup a SRV record in DNS for the LDAP server, but even when I set that it would fail at the next step when it tried to connect on udp/389 for an "AD ping". When I took out the dot and suffix it used SMB/WINS methods instead (tcp/445) and worked. I'd like to be able to use the better methods, but it seems to be either unsupported at this time or I'm just missing a key piece somewhere.

--Jay

See also:
[http://support.microsoft.com/kb/247811](http://support.microsoft.com/kb/247811)

---

### Post by oneloveamaru on 2009-12-17
Your local DNS server needs to have a zone for the domain you are trying to join AND the XP machine needs to be pointed at this DNS server. The Samba server also needs to use using the same DNS server. Is this how everything is set up? If so, send a full output of ipconfig /all from the XP machine and the entries in your DNS zone for the domain AND the relavent IP addresses for each server and we'll go from there.

---

