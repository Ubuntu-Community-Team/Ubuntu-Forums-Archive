---
title: "Error adding additional schema to OpenLDAP"
date: 2009-09-18
forum: Server Platforms
---

### Post by Essque on 2009-09-18
Hi everybody,

I'm trying to migrate an OpenLDAP / Courier-MTA/IMAP setup from an old server to the latest Ubuntu server.
I'm following the documentation that can be found here: [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

My schema_convert.conf looks like this:

```
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/collective.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/duaconf.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/java.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/openldap.schema
include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/pureftpd.schema
include /etc/ldap/schema/authldap.schema
```

I'm running slaptest -f schema_convert.conf -F /tmp/ldif_output
and I get the following error:

```
/etc/ldap/schema/authldap.schema: line 81 attributetype: Inconsistent duplicate attributeType: "mailhost"
slaptest: bad configuration directory!
```

Inspecting the file, the entry that causes the error is the following:

```
attributetype ( 1.3.6.1.4.1.10018.1.1.14 NAME 'mailhost'
        DESC 'Host to which incoming POP/IMAP connections should be proxied'
        EQUALITY caseIgnoreIA5Match
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} )
```

...and the one it conflicts with is apparently this one:

```
attributetype ( 1.3.6.1.4.1.10018.1.1.4 NAME 'maildrop'
        DESC 'RFC822 Mailbox - mail alias'
        EQUALITY caseIgnoreIA5Match
        SUBSTR caseIgnoreIA5SubstringsMatch
        SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} )
```


I'm well aware that authldap.schema wasn't updated in over 4 years and much has changed in OpenLDAP ever since. My question would be if anyone could think of a quick workaround/hack to get my LDAP server running?

TIA

Ess

---

### Post by Essque on 2009-09-21
I was wrong. The duplicate entry is *not* in the authldap.schema but in the misc.schema. So basically, it seems you can't have both loaded in the same LDAP server.

To delete misc.schema one could probably use ldapmodify, but that doesn't work for me - it hangs doing nothing after I type the password. 

The following worked for me though:

- delete /etc/ldap/slapd.d/cn\=config/cn={x}misc.ldif (replace 'x' with whatever number you have in there)
- restart slapd
- add authldap.schema to the server. Done.

Posting here in the hope it will help someone.

---

### Post by florenc on 2012-05-25
hi i everyone
i want to add new schema for user informatiom like:
firstName:
lastName:
birthday:
Reg_year:
but i can not adding 
can you help plesse?

---

