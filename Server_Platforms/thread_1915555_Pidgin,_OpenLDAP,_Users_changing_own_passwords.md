---
title: "Pidgin, OpenLDAP, Users changing own passwords"
date: 2012-01-26
forum: Server Platforms
---

### Post by abetterlie on 2012-01-26
My issue I think boils down to OpenLDAP. I want my users to be able to change their passwords using the Pidgin chat client. At the moment, I have to set their passwords, and it's a pain.
OpenLDAP works fine, my config is below. 

When users try to change password, they get a 403 forbidden from Pidgin. Nothing happens in the OpenLDAP log when they get this error, which makes me think that the request never gets there. This is the log from Pidgin:

```

(14:08:01) jabber: Sending (ssl) (test.account@xx.com/b660f5a6): <iq type='set' id='purple711c2157' to='xx.com'><query xmlns='jabber:iq:register'><username>test.account</username><password>22</password></query></iq>

(14:08:01) jabber: Recv (ssl)(302): <iq type="error" id="purple711c2157" from="xx.com" to="test.account@xx.com/b660f5a6"><query xmlns="jabber:iq:register"><username>test.account</username><password>22</password></query><error code="403" type="auth"><forbidden xmlns="urn:ietf:params:xml:ns:xmpp-stanzas"/></error></iq>
```

This is my slapd.conf:

```

# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

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
loglevel       0

# Where the dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_hdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for hdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend		hdb

#######################################################################
# Specific Directives for database #1, of type hdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        hdb

# The base of your directory in database #1
suffix          "dc=xx,dc=com"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
# rootdn          "cn=admin,dc=vo,dc=srfarm,dc=net"

rootdn	"cn=admin,dc=xx,dc=com"
rootpw	xXxXxXxX

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index default eq,pres
index           objectClass eq
index		uid,cn,member

# Save the time that the entry gets modified, for database #1
lastmod         on

# Checkpoint the BerkeleyDB database periodically in case of system
# failure and to speed slapd shutdown.
checkpoint      512 30

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=xx,dc=com" write
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
	by self write
        by dn="cn=admin,dc=xx,dc=com" write
        by * read


```

Anyone have any ideas?

---

### Post by ruffEdgz on 2012-01-26
I could be wrong about the error message from Pidgin but it looks like it might be trying to look up the account through a secure connection (I see the sending and receiving messages talk about SSL). If that is true, I don't see your LDAP server allowing port 636 through (I don't see anything about SSL/TLS certs, etc...).

I don't know which port its using to send the request to the LDAP server but can you verify which ports PIdgin is using to ask for the password change? 

This is one way I would complete this on the client side (if they are using a linux distro). You will need the package  'tcpdump' for this to work:
```

sudo tcpdump -i eth0 -s0 -w ~/tcpdump.out host xx.com

```
This command will help watch for any network traffic on your client machine and only write out connections being made to/from the host xx.com. 

You will need to run that command, then start the Pidgin application up then try and reset someones password. Once you have done this, you can Ctrl + C the tcpdump command  to stop it can you can see all the results in ~/tcpdump.out.

I hope this helps.

---

