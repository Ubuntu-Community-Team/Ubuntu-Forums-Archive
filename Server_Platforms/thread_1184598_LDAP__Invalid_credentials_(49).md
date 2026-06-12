---
title: "LDAP : Invalid credentials (49)"
date: 2009-06-11
forum: Server Platforms
---

### Post by N-t-F on 2009-06-11
Hello everyone.

I'm trying to configure a simple LDAP server in order to replace my old NIS authentication system (was under Slackware 11). I have already installed OpenLDAP and other packages, including libnss-ldap and libpam-ldap, edited configuration files and launched the server. I must have botched something, however, because the use of:

```
ldapadd -x -D "cn=admin,dc=mydomain,dc=mysuffix" -W -f ./export_group_090609.ldif
```
returns the following error after I've typed my admin password in:

```
ldap_bind: Invalid credentials (49)
```

Here is the content of some config files, in case it helps:

/etc/ldap/slapd.conf
```
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
loglevel        296

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
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend		<other>

#######################################################################
# Specific Directives for database #1, of type hdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        hdb

# Indexes to speed up requests, as suggested in "l'administration systeme" - modif 26/05/2009
index cn,uid eq
index uidNumber eq
index gidNumber eq

# The base of your directory in database #1
suffix          "dc=mydomain,dc=mysuffix"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          "cn=admin,dc=mydomain,dc=mysuffix"
rootpw {SSHA}SomethingLookingLikeAnEncryptedPassword

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# Ajout du 04/06/2009 pour la securisation des echanges
TLSCertificateFile	/etc/ssl/certs/slapd.pem
TLSCertificateKeyFile	/etc/ldap/private/slapd.key

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 20097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057 for more
# information.

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

# Checkpoint the BerkeleyDB database periodically in case of system
# failure and to speed slapd shutdown.
checkpoint      512 30

# Where to store the replica logs for database #1
# replogfile	/var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=mydomain,dc=mysuffix" write
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
        by dn="cn=admin,dc=mydomain,dc=mysuffix" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=mydomain,dc=mysuffix" write
#        by dnattr=owner write


```

And here is the /etc/default/slapd:

```
# Default location of the slapd.conf file. If empty, use the compiled-in
# default (/etc/ldap/slapd.conf). If using the cn=config backend to store
# configuration in LDIF, set this variable to the directory containing the
# cn=config data.
SLAPD_CONF=

# System account to run the slapd server under. If empty the server
# will run as root.
SLAPD_USER="openldap"

# System group to run the slapd server under. If empty the server will
# run in the primary group of its user.
SLAPD_GROUP="openldap"

# Path to the pid file of the slapd server. If not set the init.d script
# will try to figure it out from $SLAPD_CONF (/etc/ldap/slapd.conf by
# default)
SLAPD_PIDFILE=

# slapd normally serves ldap only on all TCP-ports 389. slapd can also
# service requests on TCP-port 636 (ldaps) and requests via unix
# sockets.
# Example usage:
# SLAPD_SERVICES="ldap://127.0.0.1:389/ ldaps:/// ldapi:///"
# SLAPD_SERVICES="ldap://pc00:389/ ldaps://pc00:636/"	# modif 03/06/2009
# SLAPD_SERVICES="ldap://192.168.1.1:389 ldaps://192.168.1.1:636"   # modif 08/06/2009
# SLAPD_SERVICES="ldap://pc00/389 ldaps://pc00/636"   # modif 09/06/2009
SLAPD_SERVICES="ldap:/// ldaps:///"

# If SLAPD_NO_START is set, the init script will not start or restart
# slapd (but stop will still work).  Uncomment this if you are
# starting slapd via some other means or if you don't want slapd normally
# started at boot.
#SLAPD_NO_START=1

# If SLAPD_SENTINEL_FILE is set to path to a file and that file exists,
# the init script will not start or restart slapd (but stop will still
# work).  Use this for temporarily disabling startup of slapd (when doing
# maintenance, for example, or through a configuration management system)
# when you don't want to edit a configuration file.
SLAPD_SENTINEL_FILE=/etc/ldap/noslapd

# For Kerberos authentication (via SASL), slapd by default uses the system
# keytab file (/etc/krb5.keytab).  To use a different keytab file,
# uncomment this line and change the path.
#export KRB5_KTNAME=/etc/krb5.keytab

# Additional options to pass to slapd
SLAPD_OPTIONS=""
```

Note that the SLAPD_SERVICES directive is giving me headaches and it may be the source of the problem... Any of the commented versions results in the following error message:

```
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```

But what startles me most with this problem is that editing or adding entries using LDAP Account Manager ([LAM](http://lam.sourceforge.net/)) works like a charm!  :shock:  So, I wonder if I don't have something broken in my ldapadd command line...

Any help appreciated, thank you all.

---

### Post by N-t-F on 2009-06-15
It was merely a misspelling in the distinguished name that I kept retyping the wrong way. I leave my stupid question as a reminder: always double check spelling. :oops:

---

