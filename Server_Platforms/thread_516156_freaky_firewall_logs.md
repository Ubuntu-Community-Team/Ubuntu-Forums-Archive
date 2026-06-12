---
title: "freaky firewall logs"
date: 2007-08-02
forum: Server Platforms
---

### Post by dcm1104 on 2007-08-02
I have a belkin router/firewall/wireless ap in front of my ubuntu box, but when I checked to see how many neighbors were leaching on my wireless, I saw pages and pages of this:

hu Aug 2 19:44:59 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:45:00 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:45:04 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:45:04 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:45:30 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:45:33 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:45:37 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:45:41 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:45:55 2007 1 Blocked by DoS protection 10.16.184.1
Thu Aug 2 19:46:21 2007 1 Blocked by DoS protection 10.16.184.1

which didn't upset me much.  usually it's some address from China or somewhere and it quits after a few tries.  But look at this:

gateway:/home/danm# whois 10.16.184.1

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   10.0.0.0 - 10.255.255.255 
CIDR:       10.0.0.0/8 
NetName:    RESERVED-10
NetHandle:  NET-10-0-0-0-1
Parent:     
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    
RegDate:    
Updated:    2002-09-12

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  [email]abuse@iana.org[/email]

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  [email]abuse@iana.org[/email]

# ARIN WHOIS database, last updated 2007-08-02 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

Do they have a zombie?  Shouldn't they know better?  Why me?  any words of wisdom?

---

### Post by Mr. C. on 2007-08-03
The 10.0.0.0/8 network is a private network, used for LANs; this would be coming from your LAN, not the big, bad Internet.

MrC

---

