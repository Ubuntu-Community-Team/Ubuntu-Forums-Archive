---
title: "OpenLDAP ACL to restrict automount entry"
date: 2012-08-09
forum: Server Platforms
---

### Post by mamnmamn on 2012-08-09
Hi,

We have an OpenLDAP server running on Ubuntu 9.10 (I know but it is there now and can't easily be changed!). I want to add a new automount entry with an ACL that only alows users to mount the share if they are a member of a certain group.

I have a VM running 10.04 with OpenLDAP setup and running with the directory matching my live system. I have tried a couple of different ACLs but can not make it work. Without the extra ACL(s) the user gets the automount but withit enabled, even if they are in the group they do not get the automount.

I tested with the Ldapadmin.exe app on windows and logged in as the user who is in the group and they can read all the ldap entries the acl is protecting.

ACL entries in  /etc/ldap/slapd.d/cn\=config/olcDatabase\=\{1\}hdb.ldif

```
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=comp,dc=unix" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="ou=auto.test,ou=automount,dc=comp,dc=unix" by dn="cn=admin,dc=comp,dc=unix" write by group/groupOfNames/member.exact="cn=data1,ou=groups,dc=comp,dc=unix" read by * none
olcAccess: {2}to dn.base="" by * read
olcAccess: {3}to * by dn="cn=admin,dc=comp,dc=unix" write by * read
```

I have also tried the following syntax for rule 2:
```
olcAccess: {1}to dn.base="ou=auto.test,ou=automount,dc=comp,dc=unix" by dn="cn=admin,dc=comp,dc=unix" write by group.exact="cn=data1,ou=groups,dc=comp,dc=unix" read by * none 
```

In the logs I get this information when trying to access the automount directory on the client;
```

 => dn: [2] ou=auto.test,ou=automount,dc=comp,dc=unix
Aug  9 11:50:45 mhubuntu2 slapd[7035]: => acl_get: [2] matched
Aug  9 11:50:45 mhubuntu2 slapd[7035]: => acl_get: [2] attr entry
Aug  9 11:50:45 mhubuntu2 slapd[7035]: => acl_mask: access to entry "ou=auto.test,ou=automount,dc=comp,dc=unix", attr "entry" requested
Aug  9 11:50:45 mhubuntu2 slapd[7035]: => acl_mask: to all values by "", (=0)
Aug  9 11:50:45 mhubuntu2 slapd[7035]: <= check a_dn_pat: cn=admin,dc=comp,dc=unix
Aug  9 11:50:45 mhubuntu2 slapd[7035]: <= check a_dn_pat: *
Aug  9 11:50:45 mhubuntu2 slapd[7035]: <= acl_mask: [3] applying none(=0) (stop)
Aug  9 11:50:45 mhubuntu2 slapd[7035]: <= acl_mask: [3] mask: none(=0)
Aug  9 11:50:45 mhubuntu2 slapd[7035]: => slap_access_allowed: search access denied by none(=0)

```

And I get this when access the ldap automount entries via ldapadmin.exe.
```

slapd[7035]: => dn: [2] ou=auto.test,ou=automount,dc=comp,dc=unix
slapd[7035]: => acl_get: [2] matched
slapd[7035]: => acl_get: [2] attr entry
slapd[7035]: => acl_mask: access to entry "ou=auto.test,ou=automount,dc=comp,dc=unix", attr "entry" requested
slapd[7035]: => acl_mask: to all values by "uid=user1,ou=people,dc=comp,dc=unix", (=0)
slapd[7035]: <= check a_dn_pat: cn=admin,dc=comp,dc=unix
slapd[7035]: <= check a_group_pat: cn=data1,ou=groups,dc=comp,dc=unix
slapd[7035]: => bdb_entry_get: found entry: "cn=data1,ou=groups,dc=comp,dc=unix"
slapd[7035]: <= acl_mask: [2] applying read(=rscxd) (stop)
slapd[7035]: <= acl_mask: [2] mask: read(=rscxd)
slapd[7035]: => slap_access_allowed: search access granted by read(=rscxd)
slapd[7035]: => access_allowed: search access granted by read(=rscxd)

```

As you can see from the Linux client the acl_mask is set to "" where as when using ldapadmin.exe the acl_mask is set the user logged in. This is a bit out of my depth but looks like it could be part of the cause.

Can anyone give me any clues or point me in the right direction? 

ldap export for automount is below;
```

dn: ou=automount,dc=comp,dc=unix
objectClass: organizationalUnit
objectClass: top
ou: automount

dn: ou=auto.master,ou=automount,dc=comp,dc=unix
objectClass: top
objectClass: automountMap
ou: auto.master

dn: cn=/autotest,ou=auto.master,ou=automount,dc=comp,dc=unix
objectClass: top
objectClass: automount
automountInformation: ldap:ou=auto.test,ou=automount,dc=comp,dc=unix
  --timeout=120,vers=3
cn: /autotest

dn: ou=auto.test,ou=automount,dc=comp,dc=unix
objectClass: automountMap
objectClass: top
ou: auto.test

dn: cn=mount1,ou=auto.test,ou=automount,dc=comp,dc=unix
objectClass: top
objectClass: automount
cn: mount1
automountInformation: -fstype=nfs,rw,hard,intr,nodev,exec,nosuid,rsize=8192,
 wsize=8192,acregmin=10 server1.comp.org:/meta/mount1

```
Thanks,
mamnmamn

---

