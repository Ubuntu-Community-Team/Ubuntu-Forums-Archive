---
title: "OpenLDAP is driving me nuts!"
date: 2012-09-16
forum: Server Platforms
---

### Post by b0nehead on 2012-09-16
Hi,
  I've been asked to setup a multimaster LDAP environment on Ubuntu 11.04 - instead of a single master server. I cloned the master server and recreated it into two VMs. I am trying to follow the instructions on the OpenLDAP documentation here:

[http://www.openldap.org/doc/admin24/replication.html](http://www.openldap.org/doc/admin24/replication.html)

and it talks about modifying the cn=config tree within LDAP. The subdirectory tree appears to be there at:

/etc/ldap/slapd.d/

and a 

slapcat -b cn=config

drops out a load of config information. When I try to connect using a browser and the admin bind credentials:

ldapsearch -D '<adminDN>' -w <password> -b 'cn=config'

I get:

"# extended LDIF
#
# LDAPv3
# base <> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object"

I don't see the config context when I connect via an LDAP browser either. I'm sure I'm missing something, but I can't see what it is!

TIA

b0nehead

---

