---
title: "Problems migrating an openldap installation to a new server"
date: 2016-10-25
forum: Server Platforms
---

### Post by fmouse on 2016-10-25
I have a working openldap configuration on an older server which I'd like to migrate to a new one. I've followed the directions at [http://serverfault.com/questions/730088/how-to-migrate-ldap-database-schema-configuration-to-other-machine](http://serverfault.com/questions/730088/how-to-migrate-ldap-database-schema-configuration-to-other-machine) (second answer). On the old machine I've run the following commands:

```
/etc/init.d/slapd stop
slapcat -n 0 -l mitra_slapd_config.ldif
slapcat -n 1 -l mitra_slapd_data.ldif
```

After moving these to the new server, I ran the commands:


```
/etc/init.d/slapd stop
slapadd -n 0 -F /etc/ldap/slapd.d -l mitra_slapd_config.ldif
slapadd -n 1 -l mitra_slapd_data.ldif

```

The config import appears to run successfully, but the response to the data import command is:

```
580faff8 => hdb_tool_entry_put: id2entry_add failed: BDB0067 DB_KEYEXIST: Key/data pair already exists (-30994)
580faff8 => hdb_tool_entry_put: txn_aborted! BDB0067 DB_KEYEXIST: Key/data pair already exists (-30994)
slapadd: could not add entry dn="dc=fmp,dc=com" (line=1): txn_aborted! BDB0067 DB_KEYEXIST: Key/data pair already exists (-30994)
_                       0.08% eta   none elapsed            none spd   1.1 M/s 

```
This error is effectively a show-stopper and after changing config and database ownership and permissions and restarting slapd I'm unable access the database with a query.

What do I need to do/edit to correct this?

---

### Post by fmouse on 2016-10-25
Editing the data LDIF, removing the 1st couple of entries, seems to have solved the problem.

---

