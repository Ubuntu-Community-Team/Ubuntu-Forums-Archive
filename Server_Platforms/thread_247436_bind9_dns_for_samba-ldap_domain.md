---
title: "bind9 dns for samba-ldap domain"
date: 2006-08-30
forum: Server Platforms
---

### Post by gertmul on 2006-08-30
How would you setup the DNS (bind9) (on a seperate machine) to serve a network where the domain controller is done with SAMBA and LDAP?

the domain is XYZCOM  (no dot) done by smb.conf: workgroup = XYZCOM
the netbios name from smb.conf: netbios name = XYZCOM-PDC
the hostname from /etc/hostname: sidney.xyz.com
and /etc/hosts: 192.168.11.12   sidney.xyz.com     sidney   
(plus the usual 127....localhost line above it)

Is it a problem that the domain is not XYZ.COM and how would the zonefiles look if not?

Any help is appreciated!

---

### Post by dazedandconfused on 2006-08-31
As far as I know, the fact that the domain name on the DNS server differs from the network name shouldn't be problem as the DNS server's zone of authority is set in the SOA (start Of Authority) entry in the lookup tables as well as the zones entry in named.conf.

I have a DNS server using bind9 set up for Redhat/CentOS and I run Bind9 at home on Ubuntu but as I'm at work I'll have to temporarily point you to this:

[http://foss4all.co.uk/html/server-stuff/centos/centos-dns.html](http://foss4all.co.uk/html/server-stuff/centos/centos-dns.html)

which is the CentOS version. I'm currently building a set of howto's for Ubuntu but haven't quite got there yet.

The example above should be close enough but if you get stuck post back by which time I should be at home with my Ubuntu box.

Cheers,

Jools

---

### Post by dazedandconfused on 2006-08-31
BTW, I wouldn't worry about DNS on your Windows domain too much as adding:

wins support = yes 

to smb.conf will allow your Windows boxes to resolve address through Wins/Netbios

Cheers,

Jools

---

### Post by gertmul on 2006-08-31
Thank you.

I have the 
  wins support = yes

but new Windows computers (XP) still don't want to join the domain due to some DNS error: "DNS name does not exist" and "the query was for the SRV record for _ldap._tcp.dc._msdcs.xyzcom"

So the first thought was to add this to the bind9 server, but I can't get any info on how to add that specific SRV record, plus it looks for something .xyzcom, (I am trying to join the xyzcom domain) but the bind9 server and everything else is xyz.com DNS wise?!? Could/should I add something for _ldap._tcp.dc._msdcs.xyzcom.xyz.com?

---

### Post by dtbaker on 2007-08-05
Hey I know this is thread is old but was having the same issue. Trying to join a Windows box to a Samba domain controller. 

This is the error you receive: 


```

The following error occurred when DNS was queried for the service location
(SRV) resource record used to locate a domain controller for domain
davejacoby.com:

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.<domainname>

Common causes of this error include the following:

- The DNS SRV record is not registered in DNS.

- One or more of the following zones do not include delegation to its child 

```

To fix it follow these steps:
1 - make sure nmbd is running on your linux box 
2 - if that still doesn't work make sure there are no firewalls on ur win box
3 - if that doesn't work you may still need to add these records to your bind configuration for your local domain:

```

_ldap._tcp.<domainname>. SRV 0 0 389 dc.<domainname>.
_kerberos._tcp.<domainname>. SRV 0 0 88 dc.<domainname>.
_ldap._tcp.dc._msdcs.<domainname>. SRV 0 0 389 dc.<domainname>.
_kerberos._tcp.dc._msdcs.<domainname>. SRV 0 0 88 dc.<domainname>.

```

Hope that helps someone.

---

### Post by HermanAB on 2007-08-05
Hmm, underscores are illegal in DNS names.  Thanks Bill!
;)

---

### Post by sangamc on 2008-06-15
i am also looking for solid examples of how to setup the _ldap directives for bind9. i would like to setup a fedora ds server with bind9 dns configured to allow windows workstations to join the samba domain. if anyone can ellaborate more it would help alot!


> **dtbaker said:**
> 
3 - if that doesn't work you may still need to add these records to your bind configuration for your local domain:

```

_ldap._tcp.<domainname>. SRV 0 0 389 dc.<domainname>.
_kerberos._tcp.<domainname>. SRV 0 0 88 dc.<domainname>.
_ldap._tcp.dc._msdcs.<domainname>. SRV 0 0 389 dc.<domainname>.
_kerberos._tcp.dc._msdcs.<domainname>. SRV 0 0 88 dc.<domainname>.

```

Hope that helps someone.

---

