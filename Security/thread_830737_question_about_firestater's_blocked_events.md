---
title: "question about firestater's blocked events?"
date: 2008-06-16
forum: Security
---

### Post by eerojms5 on 2008-06-16
When i start firestarter then i get so many attacks through different ports like 40044, 40482(most of them), 16323, etc! Should i close them? and if yes then how?
Are those attacks serious or i should just ignore them?

---

### Post by hyper_ch on 2008-06-16
How do you know it's an attack?

---

### Post by eerojms5 on 2008-06-16
Well, it says:
Hit from 72.140.208.208 detected
I assume that it's attack!
Am i wrong?

---

### Post by hyper_ch on 2008-06-16
you might be

---

### Post by eerojms5 on 2008-06-16
should i just ignore them all??

---

### Post by skymera on 2008-06-16
Do a whois from the terminal

```
 whois 82.3.211.68 
``` for example

That'll tell you who IP its blocking.

---

### Post by skymera on 2008-06-17
Not an attack.

```
 
scott@scott-desktop:~$ whois 74.140.208.208

OrgName:    INSIGHT COMMUNICATIONS COMPANY, L.P. 
OrgID:      INSIG-7
Address:    10200 Linn Station Road
Address:    Suite 125
City:       Louisville
StateProv:  KY
PostalCode: 40223
Country:    US

ReferralServer: rwhois://rwhois.insightns.com:4321/

NetRange:   74.128.0.0 - 74.143.255.255 
CIDR:       74.128.0.0/12 
NetName:    INSIGHT-COMMUNCATIONS-CORP
NetHandle:  NET-74-128-0-0-1
Parent:     NET-74-0-0-0-0
NetType:    Direct Allocation
NameServer: NS0.INSIGHTNS.COM
NameServer: NS1.INSIGHTNS.COM
Comment:    
RegDate:    2006-04-07
Updated:    2006-05-17

RNOCHandle: JGS2-ARIN
RNOCName:   Shea, John G
RNOCPhone:  +1-502-410-7140
RNOCEmail:  shea.j@insightcom.com 

RTechHandle: RJW40-ARIN
RTechName:   Walker, Richard James
RTechPhone:  +1-502-410-7180
RTechEmail:  walker.rj@insightcom.com 

OrgNOCHandle: NOC2077-ARIN
OrgNOCName:   Network Operations Center 
OrgNOCPhone:  +1-800-771-9124
OrgNOCEmail:  nocabuse@insightcom.com

OrgTechHandle: JGS2-ARIN
OrgTechName:   Shea, John G
OrgTechPhone:  +1-502-410-7140
OrgTechEmail:  shea.j@insightcom.com

# ARIN WHOIS database, last updated 2008-06-16 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.


Found a referral to rwhois.insightns.com:4321.

%rwhois V-1.5:003fff:00 rwhois.insightns.com (by Network Solutions, Inc. V-1.5.9.5)
network:Class-Name:network
network:ID:NETBLK-INSIGHTBB.74.128.0.0/12
network:Auth-Area:74.128.0.0/12
network:Network-Name:INSIGHTBB-74.140.192.0-19
network:IP-Network:74.140.192.0/19
network:IP-Network-Block:74.140.192.0-74.140.223.255
network:Organization;I:Insight Communications
network:Tech-Contact;I:NOC2077-ARIN
network:Admin-Contact;I:AWH25-ARIN
network:Created:20060512000000000
network:Updated:2007110500
network:Updated-By:sysadmin@insightcom.com

network:Class-Name:network
network:ID:NETBLK-INSIGHTBB.74.128.0.0/12
network:Auth-Area:74.128.0.0/12
network:Network-Name:INSIGHTBB-74.128.0.0-12
network:IP-Network:74.128.0.0/12
network:IP-Network-Block:74.128.0.0-74.143.255.255
network:Organization;I:Insight Communications
network:Tech-Contact;I:NOC2077-ARIN
network:Admin-Contact;I:AWH25-ARIN
network:Created:20060512000000000
network:Updated:2007110500
network:Updated-By:sysadmin@insightcom.com

%ok
scott@scott-desktop:~$ 

```

---

