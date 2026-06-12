---
title: "slapd.conf mysql_backend"
date: 2006-01-20
forum: Server Platforms
---

### Post by oly on 2006-01-20
hi, 

i am trying to set up a openldap with a mysql_backend, is this possible with breezy with packages from the repositories, or are not all the neccesary parts compiled into those modules ??

anyone had any success and can give me some pointers, i got it running fine with the bdb backend, but mysql would be much better as the data can be access by other software then.

---

### Post by oly on 2006-01-25
i have made a lot of progress, this is working for me to a degree but i have been unable to add data for some reason, if some one figuresw that out perhaps they can post.

myconfig are below

slapd.conf
```

# $OpenLDAP: pkg/ldap/servers/slapd/back-sql/rdbms_depend/ibmdb2/slapd.conf,v 1.2.4.1 2005/01/20 18:04:03 kurt Exp $
#
# See slapd.conf(5) for details on configuration options.
# This file should NOT be world readable.
#
include		/etc/ldap/schema/core.schema
include		/etc/ldap/schema/cosine.schema
include		/etc/ldap/schema/inetorgperson.schema

# Define global ACLs to disable default read access.

# Do not enable referrals until AFTER you have a working directory
# service AND an understanding of referrals.
#referral	ldap://root.openldap.org

pidfile		/usr/local/var/slapd.pid
argsfile	/usr/local/var/slapd.args

# where dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_sql

#######################################################################
# sql database definitions
#######################################################################
loglevel 	-1

database	sql
suffix		"dc=example,dc=com"
rootdn		"cn=ldap,dc=example,dc=com"
rootpw		testpassword
dbname		ldap
dbuser		ldap
dbpasswd	        testpassword

subtree_cond	"upper(ldap_entries.dn) LIKE CONCAT('%',?)"
insentry_query	"insert into ldap_entries (id,dn,oc_map_id,parent,keyval) values ((select max(id)+1 from ldap_entries),?,?,?,?)"
upper_func	"upper"
upper_needs_cast	"yes"
create_needs_select	"yes"
has_ldapinfo_dn_ru	"no"

access to *
	by self write
	by dn="cn=ldap-admin,dc=wild-domain,dc=internal"		write
	by * read

```

odbc.ini
```

[ODBC Data Sources]
ldap = MySQL LDAP DSN

[ldap]
Driver		= /usr/lib/odbc/libmyodbc.so
Description	= OpenLDAP Database
Host		= localhost
ServerType	= MySQL
Port		= 3306
FetchBufferSize	= 99
User		= ldap
Password	= testpassword
Database	= ldap
ReadOnly	= no
#Socket		= /tmp/mysql.sock

[ODBC]
InstallDir	= /usr/lib

```

---

### Post by Soleil-Raid on 2006-01-26
[QUOTE=oly]hi, 
anyone had any success and can give me some pointers, i got it running fine with the bdb backend, but mysql would be much better as the data can be access by other software then.[/QUOTE]

Not to be a prat, given the work you'll have put in to get it this far - but if other applications want access to the information they should be talking to the LDAP server, since that's what it's there for.

Plus, as a general rule, it's not a good idea to make a core service like LDAP rely on anything more than the bare minimum required to do it's job - in this case, file system access to it's data store, and a network interface to bind to, since if you're using it for say user information, and MySQL craps itself for whatever reason, you're going to have a lot of fun trying to get access to the system again.

What applications are going to want access to this data? Chances are they already have LDAP bindings that do a much better job.

---

### Post by oly on 2006-02-09
well my thinking at the time was for using it with php, so values could be read or changed using a php script, so i can open certain levels of access to certain users like for example allowing certain memebers to change passwords of other members, i am using bdb now anyway, i cam accross something saying u can use ldap with php, so will look into that at later date, still having problems setting up LDAP at the moment.

getting an error when running net getlocalsid, about a starttls command.

---

### Post by diablo668 on 2006-03-24
I'm havin the same problem with net getlocalsid

"Failed to issue the StartTLS instruction: Connect error"

someone got any ideas ?

---

