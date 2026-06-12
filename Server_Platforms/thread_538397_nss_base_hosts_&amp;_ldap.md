---
title: "nss_base_hosts &amp; ldap"
date: 2007-08-29
forum: Server Platforms
---

### Post by dbodner on 2007-08-29
I end up working on about 5-6 different desktops regularly.  I shorthand most of my servers in /etc/hosts so rather than typing www13.domain.com I shorthand it to www13.  So rather than try to maintain each of these 5-6 hosts db's (and rather than setting up something more elaborate), I decided to take one of my personal ldap servers, added ou=Hosts,dc=domain,dc=com, and set it up as an ipHost  objectclass (with the machine name being the cn, and the IP being ipHostNumber).  I then installed libnss-ldap and the ldap client on my machine, editing /etc/ldap.conf by adding the base and uri, /etc/libnss-ldap.conf adding the base, ldap_version, uri, and setting nss_base_hosts to ou=Hosts,dc=domain,dc=com.  I then edited /etc/nsswitch.conf and set my hosts: record to include ldap at the end.

When I do getent hosts, the hosts are listed as they should be (ip machinename).  However, when I try to ping or resolve any of the machine names, it fails.  Anybody have any ideas on what I missed?

---

### Post by dbodner on 2007-08-30
To kinda post what I mean.

getent hosts|grep testldap
24.62.234.23    testldap
ping testldap
ping: unknown host testldap

---

