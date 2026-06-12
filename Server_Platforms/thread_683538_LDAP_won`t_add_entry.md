---
title: "LDAP won`t add entry"
date: 2008-01-31
forum: Server Platforms
---

### Post by Hotel on 2008-01-31
hi
I am trying to add my 1st set of ldap entry's to my ldap server following a tutorial in apc magazine however when it gets to the point of adding the entrys to the database using an ldif file it get this error
```
sudo ldapadd -x -D "cn=root,dc=network,dc=home" -W -f ~/ldap.ldif
[sudo] password for hotel:
Enter LDAP Password: 
ldap_bind: Can't contact LDAP server (-1)

```
could anyone tell me how to fix this error please

---

### Post by rickyjones on 2008-01-31
It sounds like the ldap service is not running. Can you verify that it is running via a portscan?

-Richard

---

### Post by Hotel on 2008-01-31
it is running according to port scan but i still get that error:(

---

### Post by rickyjones on 2008-01-31
Everything correct in the ldif file you are trying to add?

---

### Post by Hotel on 2008-01-31
yes it exactly the same as the one it the tutorial

---

### Post by rickyjones on 2008-01-31
When you installed and configured your LDAP server what username was assigned as the "admin" user? Admin or Root?

-Richard

---

### Post by Hotel on 2008-01-31
root

---

### Post by rickyjones on 2008-01-31
Found this thread somewhere else regarding that error message:

[http://www.openldap.org/lists/openldap-software/200504/msg00042.html](http://www.openldap.org/lists/openldap-software/200504/msg00042.html)

Apparently OpenLDAP was only listening on the eth0 port. Maybe check into that?

-Richard

---

### Post by Hotel on 2008-01-31
that is not the case here 
```
hotel@Linux-desktop:~$ sudo netstat -ltnp | grep :389
[sudo] password for hotel:
tcp        0      0 0.0.0.0:389             0.0.0.0:*          LISTEN     
5536/slapd          
tcp6       0      0 :::389                  :::*                    LISTEN     
5536/slapd                    

```

---

### Post by rickyjones on 2008-01-31
Well, I'm running out of ideas.

Maybe posting the slapd.conf and the ldif file. Maybe something is amis between the two?

-Richard

---

### Post by Hotel on 2008-01-31
```
slapd.conf
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/samba.schema
include         /etc/ldap/schema/openldap.schema 

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

# Where the dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend		bdb
checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend		<other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix		"dc=network,dc=home"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
 rootdn          "cn=root,dc=network,dc=home"
 rootpw {SSHA}h0uqs+/ZtIcos57nN9skRLiEkrmw0dxF

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 3097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057
# for more information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile	/var/lib/ldap/replog

access to *
by dn="cn=Harry J.E Day,ou=users,dc=network,dc=home" write
by dn="cn=samba,ou=services,dc=network,dc=home" write
by * read

access to attrs=sambaLMPassword,sambaNTPassword
by dn="cn=samba,ou=services,dc=network,dc=home" write
by * none
# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=nodomain" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work 
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=nodomain" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=nodomain" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix		"dc=network,dc=home"
```
ldap.ldif```
# set up the organisation container
dn: dc=network,dc=home
objectclass: dcObject
objectclass: organization
o: my home network
dc: network

#Set up a users container
dn: ou=users,dc=network,dc=home
objectclass: organizationalUnit
ou: Users

#set up a group container
dn: ou=groups,dc=network,dc=home
objectclass: organizationalUnit
ou: Groups

#create a new user
dn: cn=Harry J.E Day,ou=users,dc=network,dc=home
objectclass: top
objectclass: posizAccount
objectclass: shadowAccount
objectclass: InetOrgPerson
cn: Harry J.E Day
sn: Day
#the unix login-name
uid: HJED
gidnumber: 1000
uidnumber: 1000
homedirectory: /home/hjed
userpassword: {SSHA}kRb2I579pShtG0jua1ih9SPpUbAJN9BM

#admin u group
dn: cn=admins,ou=groups,dc=network,dc=home
objectclass: top
objectclass: posixGroup
cn: admins
gidnumber: 1000
memberuid: HJED

#idmap
dn: ou=idmap,dc=network,dc=home
objectclass: organizationalUnit
ou: IDmap

#computers
dn: ou=computers,dc=network,dc=home
objectclass: organizationalUnit
ou: Computers

#samba user
dn: cn=samba,ou=services,dc=network,dc=home
objectClass: top
objectclass: account
objectclass: posixAccount
cn: Samba Server
uid: samba
uidNumber: 3000
gidNumber: 300
homeDirectory: /tmp
userpassword: {SSHA}vlgBlfgCsEtSkm+DolQezhU31vEh5NKZ

```

---

### Post by rickyjones on 2008-01-31
```

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=nodomain" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work 
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=nodomain" write
        by * read

```

Try replacing "cn=admin" with "cn=root" in the various instances and restart OpenLDAP.

-Richard

---

### Post by Hotel on 2008-02-01
that dosn`t appear to fix the problem
i also changed all the dc=nodomain
to dc=network,dc=home (which is what most of them where set to)

---

### Post by rickyjones on 2008-02-01
> **Hotel said:**
> that dosn`t appear to fix the problem
i also changed all the dc=nodomain
to dc=network,dc=home (which is what most of them where set to)

Man, I'm not sure what else to try here! I am out of ideas, at the end of my limited knowledge with OpenLDAP.

I wish you good luck though! I wish I could have been more help with this.

Sincerely,

-Richard

---

### Post by Hotel on 2008-02-01
i tried following the instruction on the in the Ubuntu comuntiy docs to add my entries and got a completely different error
```
 sudo /etc/init.d/slapd stop
Stopping OpenLDAP: slapd.
hotel@Linux-desktop:~$ sudo rm -rf /var/lib/ldap/*
hotel@Linux-desktop:~$ sudo slapadd -l ldap.ldif 
=> bdb_tool_entry_put: id2entry_add failed: DB_KEYEXIST: Key/data pair already exists (-30996)
=> bdb_tool_entry_put: txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30996)
slapadd: could not add entry dn="dc=network,dc=home" (line=7): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30996)

```
also i found an error in my ldif file which i have now fixed: one of the block to add a user had
```
objectclass: posizAccount
```
instead of
```
objectclass: posixAccount
```

---

### Post by Hotel on 2008-02-01
> **rickyjones said:**
> Man, I'm not sure what else to try here! I am out of ideas, at the end of my limited knowledge with OpenLDAP.

I wish you good luck though! I wish I could have been more help with this.

Sincerely,

-Richard
thanks for your help

---

### Post by Hotel on 2008-02-02
could anyone else tell me how to fix this problem please

---

### Post by xavirp on 2008-02-03
did you try disabling the firewall?

---

### Post by Hotel on 2008-02-04
yes i have tried that :(

---

