---
title: "problem with openldap, lat, e evolution"
date: 2008-08-27
forum: Server Platforms
---

### Post by richardsith on 2008-08-27
Hello everyone,
Yesterday I tried to use openldap to have a shared address book in my lan, but I found difficulties, even following the guides found on the Internet.
briefly try to explain all the steps that I made. First I installed slapd and ldap-utils entering the pwd administrator, then I found the client lat (from repositories) for the management of ldap. ah but first I edited the file slapt.conf and in the following way:
# This is the main slapd configuration files. See slapd.conf (5) for more
# Info on the configuration options.

################################################## #####################
# Global Directives:

# Features to permit
# allow bind_v2

# Scheme and definitions objectClass
include / etc / ldap / schema / core.schema
include / etc / ldap / schema / cosine.schema
include / etc / ldap / schema / nis.schema
include / etc / ldap / schema / inetorgperson.schema

# Pid Where the file is put. The init.d script
# Will not stop the server if you change this.
pidfile / var / run / slapd / slapd.pid

# List of arguments that were passed to the server
argsfile / var / run / slapd / slapd.args

# Read slapd.conf (5) for possible values
loglevel ninth

# Where the dynamically loaded modules are stored
modulepath / usr / lib / ldap
moduleload back_hdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# For indexing.
tool-1 threads

################################################## #####################
# Specific Backend Directives for hdb:
# Backend specific directives apply to this backend until another
# 'Backend' directive occurs
backend hdb

################################################## #####################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'Backend' directive occurs
# backend <other>

################################################## #####################
# Specific Directives for database # 1, of type hdb:
# Database specific directives apply to this databasse until another
# 'Database' directive occurs
database hdb

# The base of your directory database # 1
suffix "dc = nodomain"

# Rootdn directive for specifying a superuser on the database. This is needed
# For syncrepl.
rootdn "cn = admin, dc = nodomain"
rootpw SSHA) (Key
# Where the database files are physically stored for database # 1
directory "/ var / lib / ldap"

# The dbconfig settings are used to generate a DB_CONFIG file the first
# Time slapd starts. They do NOT override existing an existing DB_CONFIG
# File. You should therefore change these settings in DB_CONFIG directly
# Or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# Value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this incredibly high value
# To get slapd running at all. See [http://bugs.debian.org/303057](http://bugs.debian.org/303057) for more
# Information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database # 1
Index objectClass eq

# Save the time that the entry gets modified, for database # 1
lastmod on

# Checkpoint the BerkeleyDB database periodically in case of system
# Failure and to speed slapd shutdown.
checkpoint 512 30

# Where to store the replication logs for database # 1
# Replogfile / var / lib / ldap / replog

# The userPassword by default can be changed
# By the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# Admin entry below
# These access lines apply to database only # 1
access to attrs = userPassword, shadowLastChange
         by dn = "cn = admin, dc = nodomain" write
         by anonymous auth
         by self write
         by * ninth

# Ensure read access to the base for things like
# SupportedSASLMechanisms. Without this you may
# Have problems with not knowing what SASL
# Mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# Are wont to do you'll still need this if you
# Want SASL (and possible other things) to work
# Happily.
access to dn.base = "" by * read

# The admin dn has full write access, everyone else
# Can read everything.
Access to *
         by dn = "cn = admin, dc = nodomain" write
         Read by *

# For Netscape Roaming support, each user gets a roaming
# Profile for which they have write access to
# access to dn =".*, ou = Roaming, o = morsnet "
# By dn = "cn = admin, dc = nodomain" write
# By dnattr = owner write

################################################## #####################
# Specific Directives for database # 2, of type 'other' (can be hdb too):
# Database specific directives apply to this databasse until another
# 'Database' directive occurs
# database <other>

# The base of your directory for database # 2
# suffix "dc = debian, dc = org"

then I opened lat and I set the parameters for IP connection server, the base DN (dc = nodomain), username (cn = admin, dc = nodomian), password and I have logged. From here I went to voice browser and opening the various sections I added the folder addressbook (ou = addressbook). After that I came back to the section view and I added a Contacts selezionanto addressbook as the destination, and until this point everything ok! Undecided Undecided me the problem arises from evolution because trying to incorporate as login ou = addressbook, dc = nodomain or dc = domain, or cn = admin, dc = domain I can not see any contact created previously. My question is where mistake?if someone could help me .....
Thank you in advance

---

