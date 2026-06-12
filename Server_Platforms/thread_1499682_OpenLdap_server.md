---
title: "OpenLdap server"
date: 2010-06-02
forum: Server Platforms
---

### Post by IMadhavan on 2010-06-02
Hi 

I want to Ldapserver with ldapusers and groups like active directory in (Microsoft windows). I follow the below instruction to make Ldap server.
After this document what to do [B]to make Ldap users and groups. 
[/B]
kindly give Ideas soon

I am waiting



LDAP

At-a-Glance
1.Download necessary packages
2.Prepare the System
3.Configure slapd

**Download necessary packages**


Quote:
apt-get --yes install slapd ldap-utils db4.2-util samba-doc 


You can use Synaptic Package Manager if you want, just make sure the following four packages are installed (make sure to accept any dependencies as well)
slapd 
ldap-utils 
db4.2-util 
samba-doc
I chose to use the terminal window because I’ve given you the entire command to just copy and paste. It’s a lot quicker than searching through Synaptic.

**Prepare the System**

Rather than having LDAP store every user we create in the home directory, we’re going to create a separate directory for LDAP to use. This is really more of a house keeping issue than anything else. It make keeping track of things a little easier (in my opinion).
1.Make the directory
Open a new terminal window and as a regular user enter
Quote:
mkdir /ldaphome 
2.Make the directory available to everyone
Quote:
chmod 777 /ldaphome -R 

**Configure slapd**

There is one important thing you should know before following this part of my guide. slapd’s latest build allows you to dynamically make changes to the directory structure without requiring a restart. This is a great feature but there is one small problem: It sucks. I’ve spent HOURS reading the official documentation trying to figure out how to use the stupid thing and it still makes no sense. It’s bulky, complicated, and requires way too much work to make changes. It needs some serious revision (like an easy to use GUI) before I make the transition (Or at least some better documentation, shesh).

However, using the old method is a temporary solution. It’s a known fact that at some point the people who release slapd will remove support for the older way of modifying slapd. So you have two choices.
1.Follow this guide to replace the new method (slapd.d directory structure) with the original method (slapd.conf file) and then be forced to upgrade at some point in the (distant, not so distant?) future.
2.Use this guide as a basis for what to do, but learn how to use the new method yourself.
Okay, with that out of the way...
1.The first step is to completely remove the slapd.d directory. To do so open a terminal window with root privileges and enter the following command.
Quote:
rm -r /etc/ldap/slapd.d 

2.Next we need to edit the main slapd file.
Quote:
gedit /etc/default/slapd 
Around the 6th line you should see
Quote:
SLAPD_CONF= 
We’re going to change the line to
Quote:
SLAPD_CONF=/etc/ldap/slapd.conf 
3.Add the samba schema for ldap

Enter the following two commands in a terminal window with root privileges
Quote:
gunzip /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz
cp -v /usr/share/doc/samba-doc/examples/LDAP/samba.schema /etc/ldap/schema 
4.Decide on a LDAP administrator password and generate a SSHA hash key for it

Quote:
slappasswd -s YOUR-PASSWORD-GOES-HERE 

It will return a line that looks something like this:
Quote:
{SSHA}LQFFfwELK3few56afcsdaDSADS135w 

5.Create an init.lidf file

In just a minute we’re going to use this file to populate our LDAP server. Enter the command
Quote:
gedit /etc/ldap/init.ldif 

Since there is no file by that name yet, gedit will automatically create it for you. Copy and paste the following into your empty init.ldif file. Remember to replace each dc=example, dc=local with your own domain information. Look below the box for a description of the main term in this file.
Code:
dn: dc=example,dc=local
objectClass: dcObject
objectClass: organizationalUnit
dc: example
ou: My Example File 

dn: cn=admin, dc=example,dc=local
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: {SSHA}paste-here-the-results-of-slappaswd

dn: ou=Users, dc=example,dc=local
objectClass: organizationalUnit
ou: Users 

dn: ou=Groups, dc=example,dc=local
objectClass: organizationalUnit
ou: Groups 

dn: ou=Computers, dc=example,dc=local
objectClass: organizationalUnit
ou: Computers 

dn: ou=Idmap, dc=example,dc=local
objectClass: organizationalUnit
ou: Idmap



6.Create the slapd.conf file
Okay so we’ve told slapd to use the old method of configuration, but the slapd.conf file doesn’t actually exist yet.
To create it enter the following command
Quote:
gedit /etc/ldap/slapd.conf 

Copy and paste the following then save and close it. Remember to replace example.local with your actual domain information.
Code:
# Remember to replace suffix "dc=example,dc=local" with your domain name
# Change the rootpw entry with the results from slappaswd (Must match the same you pasted on init.ldif) 

# /etc/ldap/slapd.conf
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

######################################################################## 
#Global Directives: 

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/samba.schema
include         /etc/ldap/schema/misc.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile                      /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile                   /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible valuesloglevel        0
# Where the dynamically loaded modules are stored
modulepath               /usr/lib/ldap
moduleload          back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500 

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1 

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend                   bdb
#checkpoint 512 30 

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other> 

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database              bdb 

# The base of your directory in database #1
suffix                       "dc=example,dc=local" 

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn                       "cn=admin,dc=example,dc=local"
rootpw                      {SSHA}iPFTqrtwr3yT3XGQot2wxCuuljKA9vMU # REMEMBER!  REPLACE THIS WITH THE RESULTS FROM SLAPPASSWD 

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap" 

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0 

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See [http://bugs.debian.org/303057](http://bugs.debian.org/303057)
# for more information. 

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500 

# Indexing options for database #1
#index                  objectClass eq, pres
index ou,cn,sn,mail,givenname                            eq,pres,sub
index uidNumber,gidNumber,memberUid        eq,pres
index loginShell                                       eq,pres
index uniqueMember                                                    eq,pres
index uid                                               pres,sub,eq
index displayName                                   pres,sub,eq
index sambaSID                                      eq
index sambaPrimaryGroupSID                                  eq
index sambaDomainName                                            eq
index default                                                                    sub
#index   uid                                 pres,eq,sub 

# Save the time that the entry gets modified, for database #1
lastmod         on 

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog 

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
    by dn="cn=admin,dc=example,dc=local"  write
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
       by dn="cn=admin,dc=example,dc=local" write        
    by * read 
 
# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#                          by dn="cn=admin,dc=example,dc=ch" write
#                   by dnattr=owner write 

######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other> 

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"



7.Initialize the LDAP database


First stop the slapd service
Quote:
/etc/init.d/slapd stop 
Ensure that the ldap folder is clean
Quote:
rm -rf /var/lib/ldap/* 

Add the .ldif file you created
Quote:
slapadd -v -l /etc/ldap/init.ldif 

If all goes well you should see a final line that looks like this:
Quote:
#################### 100.00% eta none elapsed none fast! 


Make sure that LDAP has the correct privileges to access its own directory
Quote:
chown -R openldap:openldap /var/lib/ldap 
Start the slapd service back up
Quote:
/etc/init.d/slapd start 
If everything was done correctly it will say starting OpenLDAP: slapd 
If you get an error message go back and make sure you’ve done everything correctly
8.Test to see if everything is working
Quote:
ldapsearch -xLLL -b "dc=example,dc=com" 

If it’s working then it should list all the entries that we created in the init.ldif file.

---

