---
title: "Ubuntu 6.06 contacting unusual IPs"
date: 2006-12-19
forum: Server Platforms
---

### Post by HappyClam on 2006-12-19
I noticed the other day that three IPs were being accessed while I am not at the computer.  I performed a traceroute on them.  One looks like it is trying to contact Limelight Networks.  Any one know what application could be using this IP?  I am not a torrent user or any other P2P service user so I am at a loss as to what application could be doing this.  Two of the IPs are 12.120.101.14 and 68.142.121.27.  What was interesting is that one of them goes from San Antonio to Dallas to Los Angeles and then back to Dallas.  It kind of looks like it is trying to either hide itself or it is using another server to jump from.  Unfortunately I am not real savy when it come to reverse hacking (normal hacking either).  Thanks.

---

### Post by ubuntu27 on 2006-12-24
I don't have any idea either...

**2.120.101.14**

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   2.0.0.0 - 2.255.255.255 
CIDR:       2.0.0.0/8 
NetName:    RESERVED-2
NetHandle:  NET-2-0-0-0-1
Parent:    
NetType:    IANA Reserved
Comment:    
RegDate:    1995-07-07
Updated:    2002-09-12

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  [email]abuse@iana.org[/email]

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  [email]abuse@iana.org[/email]

# ARIN WHOIS database, last updated 2006-12-23 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

****************************************

inetnum:         0.0.0.0 - 255.255.255.255
netname:         IANA-BLK
descr:           The whole IPv4 address space
country:         EU # Country is really world wide
org:             ORG-IANA1-RIPE
admin-c:         IANA1-RIPE
tech-c:          IANA1-RIPE
status:          ALLOCATED UNSPECIFIED "status:" definitions
remarks:         The country is really worldwide.
remarks:         This address space is assigned at various other places in
remarks:         the world and might therefore not be in the RIPE database.
mnt-by:          RIPE-NCC-HM-MNT
mnt-lower:       RIPE-NCC-HM-MNT
mnt-routes:      RIPE-NCC-RPSL-MNT
source:          RIPE # Filtered

organisation:    ORG-IANA1-RIPE
org-name:        Internet Assigned Numbers Authority
org-type:        IANA
address:         see [http://www.iana.org](http://www.iana.org)
remarks:         The IANA allocates IP addresses and AS number blocks to RIRs
remarks:         see [http://www.iana.org/ipaddress/ip-addresses.htm](http://www.iana.org/ipaddress/ip-addresses.htm)
remarks:         and [http://www.iana.org/assignments/as-numbers](http://www.iana.org/assignments/as-numbers)
e-mail:          [email]bitbucket@ripe.net[/email]
admin-c:         IANA1-RIPE
tech-c:          IANA1-RIPE
mnt-ref:         RIPE-NCC-HM-MNT
mnt-by:          RIPE-NCC-HM-MNT
source:          RIPE # Filtered

role:            Internet Assigned Numbers Authority
address:         see [http://www.iana.org](http://www.iana.org).
e-mail:          [email]bitbucket@ripe.net[/email]
admin-c:         IANA1-RIPE
tech-c:          IANA1-RIPE
nic-hdl:         IANA1-RIPE
remarks:         For more information on IANA services
remarks:         go to IANA web site at [http://www.iana.org](http://www.iana.org).
mnt-by:          RIPE-NCC-MNT
source:          RIPE # Filtered

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX


**68.142.121.27**

OrgName:    Limelight Networks, Inc. 
OrgID:      LLNW
Address:    2220 W. 14th Street
City:       Tempe
StateProv:  AZ
PostalCode: 85281
Country:    US

ReferralServer: rwhois://rwhois.llnw.net:4321/

NetRange:   68.142.64.0 - 68.142.127.255 
CIDR:       68.142.64.0/18 
NetName:    LLNW-2
NetHandle:  NET-68-142-64-0-1
Parent:     NET-68-0-0-0-0
NetType:    Direct Allocation
NameServer: DNS.LAX.LLNS.NET
NameServer: DNS.LGA.LLNS.NET
NameServer: DNS.SJC.LLNS.NET
NameServer: DNS.IAD.LLNS.NET
Comment:    
RegDate:    2004-03-17
Updated:    2004-11-04

OrgAbuseHandle: LNAD-ARIN
OrgAbuseName:   Limelight Networks Abuse Dept 
OrgAbusePhone:  +1-602-850-5095
OrgAbuseEmail:  [email]ipadmin@limelightnetworks.com[/email]

OrgTechHandle: LNAA-ARIN
OrgTechName:   Limelight Networks ARIN Admin 
OrgTechPhone:  +1-602-850-5095
OrgTechEmail:  [email]arinadmin@limelightnetworks.com[/email]

# ARIN WHOIS database, last updated 2006-12-23 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

*******************************

inetnum:         0.0.0.0 - 255.255.255.255
netname:         IANA-BLK
descr:           The whole IPv4 address space
country:         EU # Country is really world wide
org:             ORG-IANA1-RIPE
admin-c:         IANA1-RIPE
tech-c:          IANA1-RIPE
status:          ALLOCATED UNSPECIFIED "status:" definitions
remarks:         The country is really worldwide.
remarks:         This address space is assigned at various other places in
remarks:         the world and might therefore not be in the RIPE database.
mnt-by:          RIPE-NCC-HM-MNT
mnt-lower:       RIPE-NCC-HM-MNT
mnt-routes:      RIPE-NCC-RPSL-MNT
source:          RIPE # Filtered

organisation:    ORG-IANA1-RIPE
org-name:        Internet Assigned Numbers Authority
org-type:        IANA
address:         see [http://www.iana.org](http://www.iana.org)
remarks:         The IANA allocates IP addresses and AS number blocks to RIRs
remarks:         see [http://www.iana.org/ipaddress/ip-addresses.htm](http://www.iana.org/ipaddress/ip-addresses.htm)
remarks:         and [http://www.iana.org/assignments/as-numbers](http://www.iana.org/assignments/as-numbers)
e-mail:          [email]bitbucket@ripe.net[/email]
admin-c:         IANA1-RIPE
tech-c:          IANA1-RIPE
mnt-ref:         RIPE-NCC-HM-MNT
mnt-by:          RIPE-NCC-HM-MNT
source:          RIPE # Filtered

role:            Internet Assigned Numbers Authority
address:         see [http://www.iana.org](http://www.iana.org).
e-mail:          [email]bitbucket@ripe.net[/email]
admin-c:         IANA1-RIPE
tech-c:          IANA1-RIPE
nic-hdl:         IANA1-RIPE
remarks:         For more information on IANA services
remarks:         go to IANA web site at [http://www.iana.org](http://www.iana.org).
mnt-by:          RIPE-NCC-MNT
source:          RIPE # Filtered

---

### Post by Ride Jib on 2006-12-24
12.120.101.14 is an AT&T address... probably home subscriber DSL access or something. (Methinks this is your IP)
Limelight networks does content hosting for companies like mySpace.com and XBOX live. Do you leave myspace windows open with videos/music playing?

---

