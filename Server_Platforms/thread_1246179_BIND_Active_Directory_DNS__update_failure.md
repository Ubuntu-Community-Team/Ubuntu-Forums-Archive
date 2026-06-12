---
title: "BIND Active Directory DNS  update failure"
date: 2009-08-21
forum: Server Platforms
---

### Post by comandrei on 2009-08-21
I have a Windows 2003 Server with AD on it, and I want to use my
Ubuntu server with BIND9 as the DNS for the setup.
When I install AD, it says that I have some problems with the DNS update system.
 
On the w2003 server netdiag /fix says (among other things):
```

DNS test . . . . . . . . . . . . . : Failed
          [WARNING] Cannot find a primary authoritative DNS server for the name
            'DC1.lab.mydomain.'. [RCODE_SERVER_FAILURE]
            The name 'DC1.lab.mydomain.' may not be registered in DNS.
    [FATAL] Failed to fix: DC DNS entry lab.mydomain. re-registeration on DNS serv
er '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _ldap._tcp.lab.mydomain. re-registeration
on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _ldap._tcp.pdc._msdcs.lab.mydomain. re-reg
isteration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _ldap._tcp.gc._msdcs.lab.mydomain. re-regi
steration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _ldap._tcp.c9e9f1ca-a26f-452f-9895-89905
647e4f4.domains._msdcs.lab.mydomain. re-registeration on DNS server '192.168.1.130
' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry gc._msdcs.lab.mydomain. re-registeration o
n DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry e04414cc-8dce-4256-86c3-04ae1930adbc._ms
dcs.lab.mydomain. re-registeration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _kerberos._tcp.dc._msdcs.lab.mydomain. re-
registeration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _ldap._tcp.dc._msdcs.lab.mydomain. re-regi
steration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _kerberos._tcp.lab.mydomain. re-registerat
ion on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _gc._tcp.lab.mydomain. re-registeration on
 DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _kerberos._udp.lab.mydomain. re-registerat
ion on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _kpasswd._tcp.lab.mydomain. re-registerati
on on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _kpasswd._udp.lab.mydomain. re-registerati
on on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _ldap._tcp.mydomain._sites.lab.mydomain. re-
registeration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _ldap._tcp.mydomain._sites.gc._msdcs.lab.m
oisil. re-registeration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _kerberos._tcp.mydomain._sites.dc._msdcs.l
ab.mydomain. re-registeration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _ldap._tcp.mydomain._sites.dc._msdcs.lab.m
oisil. re-registeration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _kerberos._tcp.mydomain._sites.lab.mydomain.
 re-registeration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Failed to fix: DC DNS entry _gc._tcp.mydomain._sites.lab.mydomain. re-re
gisteration on DNS server '192.168.1.130' failed.
DNS Error code: DNS_ERROR_RCODE_SERVER_FAILURE
    [FATAL] Fix Failed: netdiag failed to re-register missing DNS entries for th
is DC on DNS server '192.168.1.130'.
    [FATAL] No DNS servers have the DNS records for this DC registered.

```

My zone file:

```

$TTL    86400
@                       IN      SOA     mydomain. postmaster.mydomain. (
                                        2009042102      ; serial
                                        86400           ; refresh: once per day
                                        3600            ; retry: one hour
                                        3600000         ; expire: 42 days
                                        86400 )         ; minimum: one day
                        IN      NS      mydomain.

dc1.lab.mydomain.         IN      A       192.168.1.4
_ldap._tcp.lab.mydomain.                  SRV     0       0       389     dc1.lab.mydomain.
_kerberos._tcp.lab.mydomain.              SRV     0       0       88      dc1.lab.mydomain.
_ldap._tcp.dc._msdcs.lab.mydomain.        SRV     0       0       389     dc1.lab.mydomain.
_kerberos._tcp.dc._msdcs.lab.mydomain.    SRV     0       0       88      dc1.lab.mydomain.
gc._msdcs.lab.mydomain.                   SRV     0       0       3268    dc1.lab.mydomain.


```
named.conf.local
```

        zone "lab.mydomain" IN {
                type master;
                file "lab";
                allow-update {192.168.1.4;}; //AD Server
        };


```
I'm guessing that bind somehow dosen't accept the dynamic updates it gets from the domain controller.
And addionally, when i try to a XP workstation to the domain it says something about a remote procedure call failed. I think that's related to DNS too.

---

### Post by HermanAB on 2009-08-21
Howdy,

As far as I can figure, one can't use a modern BIND with ADS.  MS uses names with underscores for some things and those are illegal according to the RFCs. You probably need to patch BIND to allow that.

Dynamic updates is a security hole, so you should not use it.  You should create the machine accounts and DNS entries before doing the client domain join.

---

