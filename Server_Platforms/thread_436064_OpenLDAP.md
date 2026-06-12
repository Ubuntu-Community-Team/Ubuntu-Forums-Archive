---
title: "OpenLDAP"
date: 2007-05-07
forum: Server Platforms
---

### Post by coolcalt on 2007-05-07
Syslog Error
```
May  7 15:05:30 calvin-feisty slapd[14606]: backend_startup_one: starting "dc=calvin-feisty,dc=com"
May  7 15:05:30 calvin-feisty slapd[14606]: bdb_db_open: dc=calvin-feisty,dc=com
May  7 15:05:30 calvin-feisty slapd[14606]: bdb_db_open: alock package is unstable
May  7 15:05:30 calvin-feisty slapd[14606]: backend_startup_one: bi_db_open failed! (-1)
May  7 15:05:30 calvin-feisty slapd[14606]: slapd shutdown: initiated
M
```

I'm a green unix user.  And even greener sysadmin.  

is there any way to access BDB directly?  any ideas how to debug this?

/etc/ldap/slapd.conf
```
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"
calvin@calvin-feisty:~/downloads/test$ sudo tail -n 1000 /etc/ldap/slapd.conf
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

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        -1

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         bdb
checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=calvin-feisty,dc=com"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          "cn=calvin,dc=calvin-feisty,dc=com"

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

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
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=calvin,dc=calvin-feisty,dc=com" write
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
        by dn="cn=calvin,dc=calvin-feisty,dc=com" write
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
#suffix         "dc=debian,dc=org"
```

---

### Post by mlind on 2007-05-07
You can raise the loglevel in /etc/ldap/slapd.conf and get slapd to generate more verbose output in to /var/log/syslog. *man slapd.conf* should give you the log levels. (I guess 3 was what I used last time to solve my issue).

You may want to try reconfigure slapd to solve this issue
```

sudo dpkg-reconfigure slapd

```

---

### Post by lee_connell on 2007-10-22
make sure /var/lib/ldap and everything underneath it have the proper permissons.

sudo chown -R openldap:openldap /var/lib/ldap

---

