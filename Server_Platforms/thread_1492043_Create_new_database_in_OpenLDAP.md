---
title: "Create new database in OpenLDAP"
date: 2010-05-24
forum: Server Platforms
---

### Post by slv on 2010-05-24
Hello,

I want to create a new LDAP database.

Part of the new configuration is 
```

dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap-new

```

Which should store the new database in /var/lib/ldap-new

The access rights are as follows:
```

ls -al /var/lib/ldap-new/
total 8
drwxr-x---  2 openldap openldap 4096 2010-05-24 15:21 .
drwxr-xr-x 79 root     root     4096 2010-05-24 15:33 ..

```

They are the same as for /var/lib/ldap.

However, I cannot use the /var/lib/ldap-new folder.
Whenever I try to add the new database, I get the following:

```

adding new entry "olcDatabase={1}hdb,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
	additional info: olcDbDirectory: value #0: invalid path: Permission denied

```
If I change to /var/lib/ldap, it works.

I am using Ubuntu on 64 bits.

Can someone please help me?

Thank you,
  Silviu

---

### Post by Michael960 on 2010-12-08
I can confirm this: /var/lib/ldap works. Another directory (p.e. /example/ldap) doesn't :-(

So I tried to make a symbolic link: ln -s /example/ldap /var/lib/ldap but this also doesn't work :evil: (same error)

I don't think that anyone can help here. For me, it seems to be a bug :p

I am using Ubuntu 10.04 64-bit

---

### Post by cptcoconut on 2010-12-16
I encountered this problem trying to add a new database as well. I'm on 10.10. In my case, I traced the problem to apparmor.

dmesg showed an audit message indicating access was denied creating the directory I specified with olcDbDirectory.

After looking at the apparmor profile for slapd, I saw that it was allowing access to everything under /var/lib/ldap/, and that was good enough for me (I used a subdirectory beneath that path).

I believe if you want to install the LDAP Db to another directory you would need to add that directory to the apparmor profile for slapd. In my case that would have been editing "/etc/apparmor.d/usr.sbin.slapd" and changing

```

  # the databases and logs
  /var/lib/ldap/ r,
  /var/lib/ldap/** rwk,

```

to

```

  # the databases and logs
  /var/lib/ldap/ r,
  /var/lib/ldap/** rwk,

  /your/Db/Path/ r,
  /your/Db/Path** rwk,

```

And then restart/reload apparmor.

---

