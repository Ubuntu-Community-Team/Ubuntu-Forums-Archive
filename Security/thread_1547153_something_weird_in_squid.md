---
title: "something weird in squid"
date: 2010-08-06
forum: Security
---

### Post by 2ndofaug on 2010-08-06
Today i listed the open files with "lsof" and found many strange connections connecting to my squid server

squid    8912    proxy    7r  IPv4 6806316       UDP *:50755
squid    8912    proxy    9w  IPv4 6806319       TCP server.something:2222 (LISTEN)
squid    8912    proxy   10w  IPv4 6806320       UDP *:icpv2
squid    8912    proxy   13u  IPv4 6822211       TCP server.something:48249->208.99.83.44:www (ESTABLISHED)
squid    8912    proxy   14u  IPv4 6821998       TCP server.something:50798->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   16u  IPv4 6822177       TCP server.something:59176->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   20u  IPv4 6821966       TCP server.something:50076->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   21u  IPv4 6821967       TCP server.something:38532->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   22u  IPv4 6821968       TCP server.something:51559->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   23u  IPv4 6822001       TCP server.something:49299->yi-in-f101.1e100.net:www (ESTABLISHED)
squid    8912    proxy   24u  IPv4 6822256       TCP server.something:33461->8.12.130.30:www (ESTABLISHED)
squid    8912    proxy   25u  IPv4 6821976       TCP server.something:44044->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   27u  IPv4 6821979       TCP server.something:57653->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   28u  IPv4 6822127       TCP server.something:34493->a96-17-106-107.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   29u  IPv4 6821987       TCP server.something:48602->208.88.176.118:www (ESTABLISHED)
squid    8912    proxy   30u  IPv4 6822212       TCP server.something:44381->208.99.83.44:www (ESTABLISHED)
squid    8912    proxy   31u  IPv4 6822213       TCP server.something:35419->208.99.83.44:www (ESTABLISHED)
squid    8912    proxy   36u  IPv4 6822012       TCP server.something:51649->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   37u  IPv4 6822095       TCP server.something:41088->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   38u  IPv4 6822251       TCP server.something:43708->208.88.176.118:www (ESTABLISHED)
squid    8912    proxy   39u  IPv4 6822226       TCP server.something:45909->208.99.83.44:www (ESTABLISHED)
squid    8912    proxy   50u  IPv4 6822170       TCP server.something:55075->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)


can someone please explain what r these connections doing ? r they using my proxy server ? although i listened it on 2222 but the ports they r using r weird , and what is the :www at the end of their host means?

---

### Post by cariboo on 2010-08-06
The Akamai connections are mostly from Microsoft, do you have and Windows systems on your network? For the other connections you can do a whois lookup to see who they are. Whois is in the repositories. Once it is installed, open a terminal and type:

```
whois 208.88.176.118
```

I got the following result for one of the ip addresses in your listing:

```
whois  208.88.176.118
#
# Query terms are ambiguous.  The query is assumed to be:
#     "n 208.88.176.118"
#
# Use "?" to get help.
#

#
# The following results may also be obtained via:
# http://whois.arin.net/rest/nets;q=208.88.176.118?showDetails=true&showARIN=false
#

NetRange:       208.88.176.0 - 208.88.183.255
CIDR:           208.88.176.0/21
OriginAS:       AS32527
NetName:        PMGI
NetHandle:      NET-208-88-176-0-1
Parent:         NET-208-0-0-0-0
NetType:        Direct Assignment
NameServer:     DNS2.FRIENDFINDERINC.COM
NameServer:     DNS1.FRIENDFINDERINC.COM
RegDate:        2008-03-24
Updated:        2008-12-22
Ref:            http://whois.arin.net/rest/net/NET-208-88-176-0-1


OrgName:        FriendFinder Networks Inc
OrgId:          FRIEN-11
Address:        220 Humboldt ct
City:           Sunnyvale
StateProv:      CA
PostalCode:     94089
Country:        US
RegDate:        2008-07-18
Updated:        2009-07-07
Ref:            http://whois.arin.net/rest/org/FRIEN-11

OrgTechHandle: CWU4-ARIN
OrgTechName:   WU, CATHERINE 
OrgTechPhone:  +1-408-745-5598 
OrgTechEmail:  cwu@ffn.com
OrgTechRef:    http://whois.arin.net/rest/poc/CWU4-ARIN

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
```

---

### Post by bodhi.zazen on 2010-08-06
> **2ndofaug said:**
> Today i listed the open files with "lsof" and found many strange connections connecting to my squid server

squid    8912    proxy    7r  IPv4 6806316       UDP *:50755
squid    8912    proxy    9w  IPv4 6806319       TCP server.something:2222 (LISTEN)
squid    8912    proxy   10w  IPv4 6806320       UDP *:icpv2
squid    8912    proxy   13u  IPv4 6822211       TCP server.something:48249->208.99.83.44:www (ESTABLISHED)
squid    8912    proxy   14u  IPv4 6821998       TCP server.something:50798->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   16u  IPv4 6822177       TCP server.something:59176->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   20u  IPv4 6821966       TCP server.something:50076->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   21u  IPv4 6821967       TCP server.something:38532->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   22u  IPv4 6821968       TCP server.something:51559->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   23u  IPv4 6822001       TCP server.something:49299->yi-in-f101.1e100.net:www (ESTABLISHED)
squid    8912    proxy   24u  IPv4 6822256       TCP server.something:33461->8.12.130.30:www (ESTABLISHED)
squid    8912    proxy   25u  IPv4 6821976       TCP server.something:44044->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   27u  IPv4 6821979       TCP server.something:57653->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   28u  IPv4 6822127       TCP server.something:34493->a96-17-106-107.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   29u  IPv4 6821987       TCP server.something:48602->208.88.176.118:www (ESTABLISHED)
squid    8912    proxy   30u  IPv4 6822212       TCP server.something:44381->208.99.83.44:www (ESTABLISHED)
squid    8912    proxy   31u  IPv4 6822213       TCP server.something:35419->208.99.83.44:www (ESTABLISHED)
squid    8912    proxy   36u  IPv4 6822012       TCP server.something:51649->a72-246-25-9.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   37u  IPv4 6822095       TCP server.something:41088->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)
squid    8912    proxy   38u  IPv4 6822251       TCP server.something:43708->208.88.176.118:www (ESTABLISHED)
squid    8912    proxy   39u  IPv4 6822226       TCP server.something:45909->208.99.83.44:www (ESTABLISHED)
squid    8912    proxy   50u  IPv4 6822170       TCP server.something:55075->a72-246-25-40.deploy.akamaitechnologies.com:www (ESTABLISHED)


can someone please explain what r these connections doing ? r they using my proxy server ? although i listened it on 2222 but the ports they r using r weird , and what is the :www at the end of their host means?

That all appears to be normal to me.

I think you do not understand how servers and clients work.

In this case you are using squid to connect to a web (http) server. Squid (as a client) uses a pseudo random port > 1024  to connect to port 80 on the server.

So to take a single line:

> squid    8912    proxy   50u  IPv4 6822170       TCP  server.something:55075->a72-246-25-40.deploy.akamaitechnologies.com:www  (ESTABLISHED)

Your squid proxy is using port 55075 (erver.something:55075) to connect to port 80 on a72-246-25-40.deploy.akamaitechnologies.com , here port 80 is listed as "www" rather then the number 80.

See : [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

