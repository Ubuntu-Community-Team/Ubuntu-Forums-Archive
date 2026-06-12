---
title: "Trouble with ldap, how to know what is wrong"
date: 2009-01-20
forum: Server Platforms
---

### Post by LonelyStar on 2009-01-20
Hi,

I installed openldap on my vserver. I edit the config just a little, and now slapd does not start anymore:
```

root@******:/etc/ldap/slapd.d/cn=config# slapd -g openldap -u openldap -F /etc/ldap/slapd.d/ -d -1
@(#) $OpenLDAP: slapd 2.4.11 (Oct 24 2008 23:44:05) $
	buildd@palmer:/build/buildd/openldap-2.4.11/debian/build/servers/slapd
ldap_pvt_gethostbyname_a: host=********, r=0
daemon_init: <null>
daemon_init: listen on ldap:///
daemon_init: 1 listeners to open...
ldap_url_parse_ext(ldap:///)
daemon: listener initialized ldap:///
daemon_init: 2 listeners opened
ldap_create
slapd init: initiated server.
slap_sasl_init: initialized!
backend_startup_one: starting "cn=config"
=> str2entry: "cn: cn=config
objectClass: olcGlobal
cn: config
olcArgsFile: /var/run/slapd/slapd.args
olcLogLevel: Stats
olcPidFile: /var/run/slapd/slapd.pid
olcReferral: ldap://*********
olcToolThreads: 1
structuralObjectClass: olcGlobal
entryUUID: 71356238-744f-102d-9b10-b5fb67f677b6
creatorsName: cn=config
createTimestamp: 20090111171717Z
entryCSN: 20090111171717.754132Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20090111171717Z
"
str2entry: entry -1 has no dn
=> ldif_enum_tree: failed to read entry for /etc/ldap/slapd.d//cn=config.ldif
send_ldap_result: conn=-1 op=0 p=0
send_ldap_result: err=51 matched="" text=""
slapd destroy: freeing system resources.
slapd stopped.
connections_destroy: nothing to destroy.
```

Something wrong with my config? How can I find out what?

Thanks!
Nathan

---

