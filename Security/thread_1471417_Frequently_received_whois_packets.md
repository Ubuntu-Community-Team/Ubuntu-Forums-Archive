---
title: "Frequently received whois packets"
date: 2010-05-03
forum: Security
---

### Post by Crazedpsyc on 2010-05-03
I keep finding packets that appear to be whois on port 44. they appear to originate from me to whois.arin.net (2 packets each time) and 199.212.0.43 (also 2 packets each time)
when I put 199.212.0.43 in the URL box it says "Failure To Connect To Web Server". when I whois it it says:
>  OrgName:    American Registry for Internet Numbers 
 OrgID:      ARIN 
 Address:    3635 Concorde Parkway 
 Address:    Suite 200 
 City:       Chantilly 
 StateProv:  VA 
 PostalCode: 20151 
 Country:    US 
 NetRange:   [199.212.0.0]("http://samspade.org/whois?query=199.212.0.0;server=auto") - [199.212.0.255]("http://samspade.org/whois?query=199.212.0.255;server=auto") 
 CIDR:       199.212.0.0/24 
 OriginAS:   AS2914 
 NetName:     [ARIN-SERVICES]("http://samspade.org/whois?query=ARIN-SERVICES;server=whois.arin.net") 
 NetHandle:   [NET-199-212-0-0-1]("http://samspade.org/whois?query=NET-199-212-0-0-1;server=whois.arin.net") 
 Parent:     NET-199-0-0-0-0 
 NetType:    Direct Assignment 
 NameServer: [NS1.ARIN.NET]("http://samspade.org/whois?query=NS1.ARIN.NET;server=auto") 
 NameServer: [NS2.ARIN.NET]("http://samspade.org/whois?query=NS2.ARIN.NET;server=auto") 
 Comment: 
 RegDate:    2008-06-10 
 Updated:    2009-05-20 
 OrgNOCHandle: [ARINN-ARIN]("http://samspade.org/whois?query=ARINN-ARIN;server=whois.arin.net") 
 OrgNOCName:   ARIN NOC 
 OrgNOCPhone:  1-703-227-9840 
 OrgNOCEmail:  [EMAIL="noc@arin.net"]noc@arin.net[/EMAIL]
 
 OrgTechHandle: [ARIN-HOSTMASTER]("http://samspade.org/whois?query=ARIN-HOSTMASTER;server=whois.arin.net") 
 OrgTechName:   Registration Services Department 
 OrgTechPhone:  1-703-227-0660 
 OrgTechEmail:  [EMAIL="hostmaster@arin.net"]hostmaster@arin.net[/EMAIL]
 
  ARIN WHOIS database  last updated 2010-05-02 20: 00 
  Enter ? for additional hints on searching ARIN's WHOIS database. 
  ARIN WHOIS data and services are subject to the Terms of Use 
  available at https: //www.arin.net/whois_tou.html 
And yes, I did get the same packets when I used whois.
Why is my computer randomly whoising stuff?!?

---

### Post by cdenley on 2010-05-03
Are you using any security software like fail2ban? I know fail2ban can perform a whois when someone gets banned, then includes the results in an e-mail. I'm sure plenty of security tools such as intrusion detection software does something similar. What did you use to detect the whois requests? Do you know what IP's were being lookup up?

---

### Post by Crazedpsyc on 2010-05-07
I used Firestarter to detect them, as well as netcat once I saw them, none of those send whois requests without me telling them to, or at least they never have before. No I don't use anything like fail2ban, I just have my own thing that I know *cant* whois at all. no, I  do not know what they were looking up, although I keep trying to catch it with wireshark

---

### Post by Crazedpsyc on 2010-06-01
for some strange reason it was ClamTK doing this

---

