---
title: "No Tcp connections in listening report GUFW"
date: 2015-10-18
forum: Security
---

### Post by jammydodger2 on 2015-10-18
Hi All 
Curious to why there aren’t any TCP connections listed in GUFW but TCP6 UDP and UDP6 are all listed

When I do netstat listening report it shows TCP connections
Could anyone interpret the results below to advise to  any other security steps that need to be taken as i am a newbie and finding all the information available hard to digest (or a beginners link)

Netstat output below

tcp        0      0 localhost:6543          *:*                     LISTEN      1853/mythbackend
tcp        0      0 localhost:6544          *:*                     LISTEN      1853/mythbackend
tcp        0      0 fred-Presario-:domain *:*                     LISTEN      1470/dnsmasq    
tcp        0      0 localhost:mysql         *:*                     LISTEN      1169/mysqld     
tcp6       0      0 fe80::xxxxxxxxx:6543 [::]:*                  LISTEN      1853/mythbackend
tcp6       0      0 ip6-localhost:6543      [::]:*                  LISTEN      1853/mythbackend
tcp6       0      0 fe80::xxxxxxxxx:6544 [::]:*                  LISTEN      1853/mythbackend
tcp6       0      0 ip6-localhost:6544      [::]:*                  LISTEN      1853/mythbackend
udp        0      0 fred-Presario-:domain *:*                                 1470/dnsmasq    
udp        0      0 *:bootpc                *:*                                 1312/dhclient   
udp        0      0 192.XXX.XXX:ntp         *:*                                 2038/ntpd       
udp        0      0 localhost:ntp           *:*                                 2038/ntpd       
udp        0      0 *:ntp                   *:*                                 2038/ntpd       
udp        0      0 *:6600                  *:*                                 1312/dhclient   
udp6       0      0 fe80::XXXXXXXXX:ntp [::]:*                              2038/ntpd       
udp6       0      0 ip6-localhost:ntp       [::]:*                              2038/ntpd       
udp6       0      0 [::]:ntp                [::]:*                              2038/ntpd       
udp6       0      0 [::]:62037              [::]:*                              1312/dhclient   

JD

---

