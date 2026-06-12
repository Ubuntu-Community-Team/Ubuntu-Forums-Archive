---
title: "Newbie LDAP Question on 7.04"
date: 2007-08-15
forum: Server Platforms
---

### Post by NewbieNik on 2007-08-15
Hi everyone, I wonder if someone can give me some pointers?
I have been following this guide to server installs [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)
as I want to replace a Windows server. I have cheated a little by using the desktop install as I wanted a GUI (I know, my bad, but I need to make the Win-GNU/linux transition as easy as possible)
I have got to the point of testing OpenLDAP (All is installed and the ldif file was inported a-ok),but I keep getting an ¨unable to connect to LDAP server¨ error. 
Looking at the network tools port scan it turns out that port 389 is NOT open.
What can I do? where do I go from here? Squid IS installed but I have added 389 to the safe-ports ACL. Is there an iptable command I need to run?
Any and all help will be greatly appreciated

Nik


PS keep up the good work, loving Ubuntu and the forums...

---

### Post by NewbieNik on 2007-08-15
Information Update. 

The port scan was run on 127.0.0.1 and other ports are open, http, ssh, ftp and so on.
Slapd is running and is listed in the services.
I´m using Feisty Fawn 7.04, would it be better to come down to Edgy Eft 6.02? Complete re-install is not an issue as its a vanilla system.

---

### Post by NewbieNik on 2007-08-24
OK, latest information. I installed 6.04 server and LDAP seemed to work OK (Although the GUI bolt-ons wouldn let me add another user or amend existing user. said relevant information  was not entered)
So I thought I would install 7.04 server and again port 389 is not open so I cannot connect to the OpenLDAP server. Is this a 7.04 thing? Am I missing something really obvious? Is there anyone else experiencing or experienced the same?
ANY advice, tips or thoughts, no matter how right, wrong or unrelated would be appreciated. I am getting older and my hair is thinning and thats just in the last week!!

---

### Post by cancaseiro on 2007-08-26
I have same darn problem that Can't contact LDAP server. Would be nice if someone could give us some information how to overcome that problem. I try to check ports and stuff and if I work something out will return here and give information what I have done.

---

### Post by zollie on 2007-08-26
what is the ldapsearch you are running?  post that here.

---

### Post by cancaseiro on 2007-08-26
> **zollie said:**
> what is the ldapsearch you are running?  post that here.

I didn't run search I wanted to add ldif file so ran ```
ldapadd -x -D "cn=admin,dc=test,dc=ekool,dc=ee" -W -f init.ldif
``` and it returned that error```
 ldap_bind: Can't contact LDAP server (-1)
``` So what should I do to get over it?

---

### Post by cancaseiro on 2007-08-27
As I can understand there might be some kind of problem with ldap port . Sadly in OpenLDAP site there is nothing about ports in documentation . Can my problem be realated to port or I am on wrong way here?

---

### Post by cancaseiro on 2007-08-27
Here is my slpad.conf file: Is everything ok there?

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
suffix          "dc=test,dc=ekool,dc=ee"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          "cn=admin,dc=test,dc=ekool,dc=ee"

#Juure salakas

rootpw {SSHA}lJg0MN8OPaK+UsLnnLExoZylOqdHPhvt

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
# replogfile	/var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=ekool,dc=ee" write
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
        by dn="cn=admin,dc=test,dc=ekool,dc=ee" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=ekool,dc=ee" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix		"dc=debian,dc=org"
```

---

### Post by cancaseiro on 2007-08-27
Hi again. I am getting closer to my problems. I have to configure database to hold ```
"dc=test,dc=ekool,dc=ee"
``` as at the moment it isn't configured so. How can I do it?

---

### Post by cancaseiro on 2007-08-27
> **cancaseiro said:**
> Hi again. I am getting closer to my problems. I have to configure database to hold ```
"dc=test,dc=ekool,dc=ee"
``` as at the moment it isn't configured so. How can I do it?

Ok got over that problem by modifying slapd.conf file but now I have new error: ```
slapadd: dn="dc=test,dc=ekool,dc=ee" (line=6): (64) value of naming attribute 'dc' is not present in entry
```

:(

---

### Post by cancaseiro on 2007-08-27
> **cancaseiro said:**
> Ok got over that problem by modifying slapd.conf file but now I have new error: ```
slapadd: dn="dc=test,dc=ekool,dc=ee" (line=6): (64) value of naming attribute 'dc' is not present in entry
```

:(

My new slapd.conf:

#
# See slapd.conf(5) for details on configuration options.
# This file should NOT be world readable.
#
include		/usr/local/etc/openldap/schema/core.schema

# Define global ACLs to disable default read access.

# Do not enable referrals until AFTER you have a working directory
# service AND an understanding of referrals.
#referral	ldap://root.openldap.org

pidfile		/usr/local/var/run/slapd.pid
argsfile	/usr/local/var/run/slapd.args

# Load dynamic backend modules:
# modulepath	/usr/local/libexec/openldap
# moduleload	back_bdb.la
# moduleload	back_ldap.la
# moduleload	back_ldbm.la
# moduleload	back_passwd.la
# moduleload	back_shell.la

# Sample security restrictions
#	Require integrity protection (prevent hijacking)
#	Require 112-bit (3DES or better) encryption for updates
#	Require 63-bit encryption for simple bind
# security ssf=1 update_ssf=112 simple_bind=64

# Sample access control policy:
#	Root DSE: allow anyone to read it
#	Subschema (sub)entry DSE: allow anyone to read it
#	Other DSEs:
#		Allow self write access
#		Allow authenticated users read access
#		Allow anonymous users to authenticate
#	Directives needed to implement policy:
# access to dn.base="" by * read
# access to dn.base="cn=Subschema" by * read
# access to *
#	by self write
#	by users read
#	by anonymous auth
#
# if no access controls are present, the default policy
# allows anyone and everyone to read anything but restricts
# updates to rootdn.  (e.g., "access to * by * read")
#
# rootdn can always read and write EVERYTHING!

#######################################################################
# BDB database definitions
#######################################################################

database	bdb
suffix		"dc=test,dc=ekool,dc=ee"
rootdn		"cn=admin,dc=test,dc=ekool,dc=ee"
# Cleartext passwords, especially for the rootdn, should
# be avoid.  See slappasswd(8) and slapd.conf(5) for details.
# Use of strong authentication encouraged.
#rootpw		{SSHA}wSazqIGcA2pdI5/qTKTIswD+sFp66HKV
# The database directory MUST exist prior to running slapd AND 
# should only be accessible by the slapd and slap tools.
# Mode 700 recommended.
directory	/usr/local/var/openldap-data
# Indices to maintain
index	objectClass	eq

and ldif:

dn: dc=test,dc=ekool,dc=ee
objectclass: dcObject
objectclass: organization
o: Koolitoode AS
dc: test.ekool

dn: cn=admin,dc=test,dc=ekool,dc=ee
objectclass: organizationalRole
cn: admin

---

### Post by NewbieNik on 2007-09-01
Cancaseiro,

Sorry to hear you have a problem too, but its nice to know I´m not alone. I don´t know a huge amount on ldap, but could it be the line

dc: test.ekool

in your ldif file?

Have you managed to connect ot the ldap server yet? I have tried new install but still cannot get ldap to open on port 389...getting frustrated due to lack of help on OpenLDAP site and documentation

---

### Post by NewbieNik on 2007-09-20
Aha, A look recently has prompted this information.

OpenLDAP creates the database with root only permissions so on boot LDAP cannot read the db files. When running the initial ldapadd it needs to be run as a user so:-

sudo -u OpenLDAP(or whomever) ldapadd -l init.ldif

otherwise you can only start the service from bash as so:-

sudo slapd (and add -s option if you want it)

Now all I need to do is get it to talk to Samba and I've got a start on replacing my Windumb Server

---

### Post by dendrobates on 2007-09-20
Cancaseiro,

First I would try to add your ldif with the slapd not running using slapadd.

sudo slapadd  -l ldiffile

I think that error is referencing an ldif entry.

You might want to post the ldif and the results of 'sudo slapcat'  if it is not too large.  Without the userPassword attribute of course.

---

### Post by HornedBeast on 2008-01-29
This is an awesome guide on getting LDAP to work. I followed the guide exactly and works for me.

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

I advise reading the whole thread though incase you come against any issues.

---

