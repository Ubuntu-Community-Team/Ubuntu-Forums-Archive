---
title: "ddns + dhcp : update unsuccessful, name already exists"
date: 2016-06-02
forum: Server Platforms
---

### Post by QuimNuss on 2016-06-02
I've set up dhcp + bind9 ddns with allow updates by key

I keep getting this 'update unsuccessful' messages on syslog because the name already exists (from the previous dhcp renew) and I would like to confirm that those are informative and perfectly normal and, therefore, can be ignored by logcheck.

If the dhcp changed the ip of the lease, would the record be correctly updated? If not, how can I allow the replacement a name in use? And from the point of view of security, should I?

```

Jun  1 11:21:10 tutusrv dhcpd: DHCPREQUEST for 192.168.30.130 from 00:08:9b:c2:0b:1a via p4p1
Jun  1 11:21:10 tutusrv dhcpd: DHCPACK on 192.168.30.130 to 00:08:9b:c2:0b:1a via p4p1
Jun  1 11:21:10 tutusrv named[4504]: client 192.168.30.240#3336/key rndc-key: updating zone 'tutu/IN': update unsuccessful: hssrv-bak.tutu: 'name not in use' prerequisite not satisfied (YXDOMAIN)
Jun  1 11:21:10 tutusrv named[4504]: client 192.168.30.240#3336/key rndc-key: signer "rndc-key" approved
Jun  1 11:21:10 tutusrv named[4504]: client 192.168.30.240#3336/key rndc-key: updating zone 'tutu/IN': deleting rrset at 'hssrv-bak.tutu' A
Jun  1 11:21:10 tutusrv named[4504]: client 192.168.30.240#3336/key rndc-key: updating zone 'tutu/IN': adding an RR at 'hssrv-bak.tutu' A
Jun  1 11:21:10 tutusrv dhcpd: Added new forward map from hssrv-bak.tututo 192.168.30.130
Jun  1 11:21:10 tutusrv named[4504]: client 192.168.30.240#3336/key rndc-key: signer "rndc-key" approved
Jun  1 11:21:10 tutusrv named[4504]: client 192.168.30.240#3336/key rndc-key: updating zone '30.168.192.in-addr.arpa/IN': deleting rrset at '130.30.168.192.in-addr.arpa' PTR
Jun  1 11:21:10 tutusrv named[4504]: client 192.168.30.240#3336/key rndc-key: updating zone '30.168.192.in-addr.arpa/IN': adding an RR at '130.30.168.192.in-addr.arpa' PTR
Jun  1 11:21:10 tutusrv dhcpd: Added reverse map from 130.30.168.192.in-addr.arpa. to hssrv-bak.tutu

```

Cheers

---

### Post by boweeb on 2016-06-20
> I would like to confirm that those are informative and perfectly normal

I can confirm for you that the log snippet you posted reflects **normal** behavior.
> There is no logical-OR in dynamic dns updates.  There are only prerequisite
statements.

First we send a packet that looks something like this:

	PREREQ:	[name] NONE A
	ADD:	[name] IN A	a.b.c.d
	ADD:	[name] IN TXT	"magic hashed string here"

IF result is success, you're done.
IF result is YXDOMAIN, you send another packet:

	PREREQ:	[name] IN TXT	"magic hashed string here"
	DELETE:	[name] ANY A
	ADD:	[name] IN A	a.b.c.d
-- David Hankins, [source]("https://lists.isc.org/pipermail/dhcp-users/2006-April/000355.html")


I believe the above link will give enough context to answer your other questions as well.

---

