---
title: "Have I been hacked?"
date: 2009-02-25
forum: Security
---

### Post by oraldlight on 2009-02-25
I decided to troll some log files the other day, and noticed on/about 1/25/2009 my web server is suddenly going bananas trying to contact a certain IP that I can not figure out.

Of course the usual "check the logs more often" apply, so save me from the abuse, please....

So looking to my server I have no clue what is aledged to be "phoning home" on all these ports: (a partial listing of the Banish logs)

> 18:58:45  * forward  eth0  TCP  10.0.0.124 49992  :::::  87.106.95.153 80(HTTP)
18:58:21  * forward  eth0  TCP  10.0.0.124 49992  :::::  87.106.95.153 80(HTTP)
18:58:09  * forward  eth0  TCP  10.0.0.124 49992  :::::  87.106.95.153 80(HTTP)
18:58:03  * forward  eth0  TCP  10.0.0.124 49992  :::::  87.106.95.153 80(HTTP)
18:58:00  * forward  eth0  TCP  10.0.0.124 49992  :::::  87.106.95.153 80(HTTP)
18:53:39  * forward  eth0  TCP  10.0.0.124 33852  :::::  87.106.95.153 80(HTTP)
18:53:15  * forward  eth0  TCP  10.0.0.124 33852  :::::  87.106.95.153 80(HTTP)
18:53:03  * forward  eth0  TCP  10.0.0.124 33852  :::::  87.106.95.153 80(HTTP)


Any ideas on how to discern what is the root of this sending?
[10.0.0.124 is my server.87.106.95.153 is in Germany and unfamiliar to me.]

---

### Post by sgosnell on 2009-02-25
Put the IP address into a Google search and see what you get.

---

### Post by Philo1 on 2009-02-25
Here is what I found:


IP Address: 87.106.95.153

IP Address Details:
Domain Name: s15255494.rootmaster.info
Location: Karlsruhe, 01, Germany Country Flag

Serving HTTP (Port 80): Yes

IP Address Whois:
PE Network Coordination Centre
OrgID: RIPE
Address: P.O. Box 10096
City: Amsterdam
StateProv:
PostalCode: 1001EB
Country: NL

ReferralServer: whois://whois.ripe.net:43

NetRange: 87.0.0.0 - 87.255.255.255
CIDR: 87.0.0.0/8
NetName: 87-RIPE
NetHandle: NET-87-0-0-0-1
Parent:
NetType: Allocated to RIPE NCC
NameServer: NS-PRI.RIPE.NET
NameServer: NS3.NIC.FR
NameServer: SEC1.APNIC.NET
NameServer: SEC3.APNIC.NET
NameServer: SUNIC.SUNET.SE
NameServer: TINNIE.ARIN.NET
NameServer: NS.LACNIC.NET
Comment: These addresses have been further assigned to users in
Comment: the RIPE NCC region. Contact information can be found in
Comment: the RIPE database at [http://www.ripe.net/whois](http://www.ripe.net/whois)
RegDate: 2004-04-01
Updated: 2004-04-06

# ARIN WHOIS database, last updated 2009-02-25 19:10

---

### Post by oraldlight on 2009-02-26
Done that, and reveals nothing of value to me. Other than knowing its in Germany.

---

### Post by wirelessmonkey on 2009-02-26
Well... it resolves to [http://www.fotokasten.de](http://www.fotokasten.de) , which appears to be a german photography business site.

---

