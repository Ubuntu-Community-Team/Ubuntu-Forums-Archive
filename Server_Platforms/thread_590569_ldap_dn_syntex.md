---
title: "ldap dn syntex"
date: 2007-10-24
forum: Server Platforms
---

### Post by nanoMU on 2007-10-24
after a many clean installs and about 3 days i finally got open ldap to work on my computer yeah (i fallowed openldap guide (it is very good minus the database set up i just used apt-get cause there way didnt work)) i also installed ldap administration tool to help me work with my new ldap server  it is all up and running i can log into LAT (ldap administration tool) under annyous but when i try Manager i get the fallowing error "error:invalid DN syntax" here is my slapd.conf file


include		/usr/local/etc/openldap/schema/core.schema

pidfile		/usr/local/var/run/slapd.pid
argsfile	/usr/local/var/run/slapd.args
database	bdb
suffix		"dc=test,dc=local"
rootdn		"cn=Manager,dc=test,dc=local"

rootpw	<mypassword>

directory	/usr/local/var/openldap-data
# Indices to maintain
index	objectClass	eq

any ideas below is a link to my log in settings for LAT [http://img457.imageshack.us/img457/3647/screenshotpi3.png](http://img457.imageshack.us/img457/3647/screenshotpi3.png)

---

### Post by nanoMU on 2007-10-25
ok i am able to log into my server now using cn=Manager,dc=test,dc=local with out the quotes but now i can not create users/groups/ou

---

