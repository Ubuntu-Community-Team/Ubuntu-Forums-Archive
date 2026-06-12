---
title: "About domain setup"
date: 2007-01-08
forum: Server Platforms
---

### Post by satimis on 2007-01-08
Hi folks,

ubuntu-6.06.1-LAMP-server-amd64

I have satimis.com registered with goddady.com

Hereunder are the contents of;

$ cat /etc/hosts
```

#127.0.0.1      localhost.localdomain   localhost
127.0.0.1 localhost.satimis.homelinux.com localhost mail.satimis.homelinux.com
#192.168.0.100  sever1.example.com   server1
192.168.0.100 mail.satimis.homelinux.com mail

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

$ cat /etc/hostname
```

mail.satimis.homelinux.com

```

Please advise how to edit these files so that people evokeing "www.satimis.com" can visit the test homepage on this server.  What other files I have to edit as well.

TIA


B.R.
satimis

---

### Post by apjone on 2007-01-08
> **satimis said:**
> Hi folks,

ubuntu-6.06.1-LAMP-server-amd64

I have satimis.com registered with goddady.com

Hereunder are the contents of;

$ cat /etc/hosts
```

#127.0.0.1      localhost.localdomain   localhost
127.0.0.1 localhost.satimis.homelinux.com localhost mail.satimis.homelinux.com
#192.168.0.100  sever1.example.com   server1
192.168.0.100 mail.satimis.homelinux.com mail

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

$ cat /etc/hostname
```

mail.satimis.homelinux.com

```

Please advise how to edit these files so that people evokeing "www.satimis.com" can visit the test homepage on this server.  What other files I have to edit as well.

TIA


B.R.
satimis

Have you forwarded port 80 to your machine within your router/firewall?

---

### Post by MrHorus on 2007-01-08
Those files are only accessable from your own machine.

If you want external people to have access then you will want to run a DNS server such as BIND - this is the most common DNS server in use on the Internet and is how URLs are translated from something like [www.google.com](www.google.com) into a dotted-decimal IP address.

---

### Post by satimis on 2007-01-08
Hi apjone,

> 
Have you forwarded port 80 to your machine within your router/firewall?

I haven't made any change on iptables rules.  The settings were for previously running dynamic IP with subdomain registered with dyndns.org/com.

Now I'm running static IP with domain registered with goddaddy.com and could not figure out which files I have to edit.  OR make editing on goddaddy site?  Tks.

B.R.
satimis

---

### Post by satimis on 2007-01-08
Hi MrHorus,

Tks for your advice.

> 
If you want external people to have access then you will want to run a DNS server such as BIND - this is the most common DNS server in use on the Internet and is how URLs are translated from something like [www.google.com](www.google.com) into a dotted-decimal IP address.

I made following tests

on [www.proxydom.com](www.proxydom.com) site

evoked;
[http://www.satimis.com](http://www.satimis.com)```

www.satimis.com:80
This page is parked free, courtesy of GoDaddy.com
Go to the GoDaddy.com home page!

Not what you're looking for?1)

```


2)
on [www.network-tools.com](www.network-tools.com) site

ping [www.satimis.com](www.satimis.com)```

Ping 68.178.232.100

[satimis.com]

Round trip time to 68.178.232.100: 744 ms
Round trip time to 68.178.232.100: 46 ms
Round trip time to 68.178.232.100: 31 ms
Round trip time to 68.178.232.100: 31 ms
Round trip time to 68.178.232.100: 30 ms
Round trip time to 68.178.232.100: 30 ms
Round trip time to 68.178.232.100: 30 ms
Round trip time to 68.178.232.100: 30 ms
Round trip time to 68.178.232.100: 30 ms
Round trip time to 68.178.232.100: 30 ms

```


$ sudo whois 68.178.232.100
```

OrgName:    Go Daddy Software
OrgID:      GDS-31
Address:    14455 N Hayden Road
Address:    Suite 226
City:       Scottsdale
StateProv:  AZ
PostalCode: 85260
Country:    US

NetRange:   68.178.128.0 - 68.178.255.255
CIDR:       68.178.128.0/17
NetName:    GO-DADDY-SOFTWARE-INC
NetHandle:  NET-68-178-128-0-1
Parent:     NET-68-0-0-0-0
NetType:    Direct Allocation
NameServer: CNS1.SECURESERVER.NET
NameServer: CNS2.SECURESERVER.NET
Comment:
RegDate:    2005-04-12
Updated:    2005-11-11

RAbuseHandle: ABUSE51-ARIN
RAbuseName:   Abuse Department
RAbusePhone:  +1-480-624-2505
RAbuseEmail:  abuse@godaddy.com

RNOCHandle: NOC124-ARIN
RNOCName:   Network Operations Center
RNOCPhone:  +1-480-505-8809
RNOCEmail:  noc@godaddy.com

OrgAbuseHandle: ABUSE51-ARIN
OrgAbuseName:   Abuse Department
OrgAbusePhone:  +1-480-624-2505
OrgAbuseEmail:  abuse@godaddy.com

OrgNOCHandle: NOC124-ARIN
OrgNOCName:   Network Operations Center
OrgNOCPhone:  +1-480-505-8809
OrgNOCEmail:  noc@godaddy.com

OrgTechHandle: NOC124-ARIN
OrgTechName:   Network Operations Center
OrgTechPhone:  +1-480-505-8809
OrgTechEmail:  noc@godaddy.com

# ARIN WHOIS database, last updated 2007-01-08 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

```


B.R.
satimis

---

