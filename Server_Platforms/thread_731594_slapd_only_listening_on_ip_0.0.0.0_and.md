---
title: "slapd only listening on ip 0.0.0.0 and :::"
date: 2008-03-22
forum: Server Platforms
---

### Post by Hotel on 2008-03-22
hi
i am having allot of trouble getting slapd to listen on the right ip addresses for some reason it is always listening on 0.0.0.0:398 and :::398 could anyone please help me fix this
i need it to listen on 192.168.2.54 and 127.0.0.1 also i would really like to get it to listen on fe00::209:5bff:fe25:d51d
i am using slapd 2.3.35 and ubuntu 7.10

i did a port scan for reference
```
 sudo netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN     4951/slapd          
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4676/cupsd          
tcp6       0      0 :::389                  :::*                    LISTEN     4951/slapd          
udp        0      0 192.168.2.54:137        0.0.0.0:*                          5476/nmbd           
udp        0      0 0.0.0.0:137             0.0.0.0:*                          5476/nmbd           
udp        0      0 192.168.2.54:138        0.0.0.0:*                          5476/nmbd           
udp        0      0 0.0.0.0:138             0.0.0.0:*                          5476/nmbd           
udp        0      0 127.0.0.1:53            0.0.0.0:*                          4691/maradns        
udp        0      0 192.168.2.54:53         0.0.0.0:*                          4691/maradns        
udp        0      0 0.0.0.0:631             0.0.0.0:*                          4676/cupsd             

```
my ldap.conf is
```
# $OpenLDAP: pkg/ldap/libraries/libldap/ldap.conf,v 1.9 2000/09/04 19:57:01 kurt Exp $
#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.
URI ldap://127.0.0.1:389 ldap://192.168.2.54:389 ldap://fe00::209:5bff:fe25:d51d:389 ldap://linux-desktop:389 ldap://linux-desktop.network.home:389

BASE    dc=network,dc=home


#SIZELIMIT	12
#TIMELIMIT	15
#DEREF		never
```
and my slapd.conf is
```
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
allow bind_v2

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
database       bdb

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
 replogfile	/var/lib/ldap/replog

#access to *
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
        by dn="cn=root,dc=network,dc=home" write
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
        by dn="cn=root,dc=network,dc=home" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=root,dc=network,dc=home" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix		"dc=network,dc=home"
```
thank in advance for any help

---

### Post by Hotel on 2008-03-22
please help:confused::confused::confused::cry::|

---

