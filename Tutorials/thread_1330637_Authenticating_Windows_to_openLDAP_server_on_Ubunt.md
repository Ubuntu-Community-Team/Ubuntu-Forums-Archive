---
title: "Authenticating Windows to openLDAP server on Ubuntu 9.10"
date: 2009-11-18
forum: Tutorials
---

### Post by abishur on 2009-11-18
[FONT=Verdana][SIZE=2]This is a quick guide to setting up LDAP on your server so that Linux/Windows users can join your domain.  This was written specifically because I saw several people complaining that it could not be done on Ubuntu 9.10 and I figured, "Hey I've worked it out, so why not share it?"[/SIZE][/FONT][FONT=Verdana]

I have used the guide at least 4 times on a clean install of Ubuntu 9.10.  It has worked 100% without so much as a hiccup.  It *should *work for you too ;)

Edit: I forgot to mention, but this is based on [this thread]("http://ubuntuforums.org/showthread.php?t=1184288") and is simply updated for 9.10 and fixed up a little in a few random areas.

[/FONT]        [CENTER][FONT=Verdana][SIZE=3][COLOR=RoyalBlue]**LDAP**[/COLOR][/SIZE][/FONT][FONT=Verdana]
[/FONT] [/CENTER]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=2][COLOR=RoyalBlue]**At-a-Glance**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
  1.Download necessary packages
  2.Prepare the System
  3.Configure slapd
  4.Prepare LDAP for use with Samba

[/SIZE][/FONT]    [FONT=Verdana][SIZE=2][COLOR=RoyalBlue]**Download necessary packages**[/COLOR][/SIZE][/FONT][FONT=Verdana]



          [/FONT]>      [FONT=Verdana][SIZE=2]apt-get   --yes install slapd ldap-utils db4.2-util samba-doc[/SIZE][/FONT][FONT=Verdana][SIZE=2]  

You can use Synaptic Package Manager if you want, just make sure the following four packages are installed (make sure to accept any dependencies as well)
[/SIZE][/FONT]   
[LIST]
[*][FONT=Verdana][SIZE=2]slapd[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]ldap-utils[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]db4.2-util[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]samba-doc
[/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2]   I chose to use the terminal window because I&#8217;ve given you the entire command to just copy and paste.  It&#8217;s a lot quicker than searching through Synaptic.

[COLOR=RoyalBlue]**Prepare the System**[/COLOR]

  Rather than having LDAP store every user we create in the home directory, we&#8217;re going to create a separate directory for LDAP to use.  This is really more of a house keeping issue than anything else.  It make keeping track of things a little easier (in my opinion).

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   1.Make the directory[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]Open a new terminal window and as a regular user enter[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][/INDENT][INDENT]> [FONT=Verdana][SIZE=2]mkdir /ldaphome      [/SIZE][/FONT][FONT=Verdana][SIZE=2]   2.Make the directory available to everyone[/SIZE][/FONT][INDENT]> [FONT=Verdana][SIZE=2]chmod 777 /ldaphome -R[/SIZE][/FONT][/INDENT][/INDENT][FONT=Verdana][SIZE=2]
[COLOR=RoyalBlue]**Configure slapd**[/COLOR]

    There is one important thing you should know before following this part of my guide.  slapd&#8217;s latest build allows you to dynamically make changes to the directory structure without requiring a restart.  This is a great feature but there is one small problem: It sucks.  I&#8217;ve spent HOURS reading the official documentation trying to figure out how to use the stupid thing and it still makes no sense.  It&#8217;s bulky, complicated, and requires way too much work to make changes.  It needs some serious revision (like an easy to use GUI) before I make the transition (Or at least some better documentation, shesh).

  However, using the old method is a temporary solution.  It&#8217;s a known fact that at some point the people who release slapd ***_will_*** remove support for the older way of modifying slapd.  So you have two choices.

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   1.Follow this guide to replace the new method (slapd.d directory structure) with the original method (slapd.conf file) and then be forced to upgrade at some point in the (distant, not so distant?) future.[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]   2.Use this guide as a basis for what to do, but learn how to use the new method yourself.[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]   Okay, with that out of the way...

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   1.The first step is to completely remove the slapd.d directory.  To do so open a terminal window with root privileges and enter the following command.[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][INDENT][FONT=Verdana]> rm -r /etc/ldap/slapd.d[/FONT][/INDENT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   2.Next we need to edit the main slapd file.[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][INDENT]> [FONT=Verdana][SIZE=2]gedit   /etc/default/slapd[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Around the 6th line you should see[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]SLAPD_CONF=[/SIZE][/FONT][FONT=Verdana][SIZE=2]   We&#8217;re going to change the line to[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]SLAPD_CONF=/etc/ldap/slapd.conf[/SIZE][/FONT][FONT=Verdana][SIZE=2]   3.Add the samba schema for ldap[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   Enter the following two commands in a terminal window with root privileges[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]gunzip   /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz[/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]cp -v   /usr/share/doc/samba-doc/examples/LDAP/samba.schema /etc/ldap/schema[/SIZE][/FONT][FONT=Verdana][SIZE=2]   4.Decide on a LDAP administrator password and generate a SSHA hash key for it[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Verdana]> slappasswd   -s YOUR-PASSWORD-GOES-HERE[/FONT][/INDENT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   It will return a line that looks something like this:[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]{SSHA}LQFFfwELK3few56afcsdaDSADS135w[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   5.Create an init.lidf file[/SIZE][/FONT][FONT=Verdana]

[/FONT]  [FONT=Verdana][SIZE=2]   In just a minute we&#8217;re going to use this file to populate our LDAP server.  Enter the command[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]gedit   /etc/ldap/init.ldif[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2]
  Since there is no file by that name yet, gedit will automatically create it for you.  Copy and paste the following into your empty init.ldif file.  Remember to replace each dc=example, dc=local with your own domain information.  Look below the box for a description of the main term in this file.

          [/SIZE][/FONT]```
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
```[FONT=Verdana][SIZE=2]



[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]    6.Create the slapd.conf file[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]   Okay so we&#8217;ve told slapd to use the old method of configuration, but the slapd.conf file doesn&#8217;t actually exist yet.

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   To create it enter the following command[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]gedit   /etc/ldap/slapd.conf[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
  Copy and paste the following then save and close it.   Remember to replace example.local with your actual domain information.

[/SIZE][/FONT]```
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
rootpw                      {SSHA}iPFTqrtwr3yT3XGQot2wxCuuljKA9vMU **# REMEMBER!  REPLACE THIS WITH THE RESULTS FROM SLAPPASSWD **

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap" 

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0 

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See [http://bugs.debian.org/303057]("http://bugs.debian.org/303057#")
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
```[FONT=Verdana][SIZE=2]



[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   7.Initialize the LDAP database[/SIZE][/FONT][FONT=Verdana]


[/FONT]   [FONT=Verdana][SIZE=2]   First stop the slapd service[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]/etc/init.d/slapd   stop[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Ensure that the ldap folder is clean[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]rm -rf   /var/lib/ldap/*[/SIZE][/FONT][FONT=Verdana][SIZE=2] 
Add the .ldif file you created[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]slapadd -v -l /etc/ldap/init.ldif[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
  If all goes well you should see a final line that looks like this:

[/SIZE][/FONT]> [FONT=Verdana][SIZE=2]#################### 100.00% eta   none elapsed            none fast![/SIZE][/FONT][FONT=Verdana][SIZE=2]


[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   Make sure that LDAP has the correct privileges to access its own directory[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]chown -R openldap:openldap /var/lib/ldap[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Start the slapd service back up[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]/etc/init.d/slapd start[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2]   If everything was done correctly it will say starting OpenLDAP: slapd 
  If you get an error message go back and make sure you&#8217;ve done everything correctly

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   8.Test to see if everything is working[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]ldapsearch   -xLLL -b "dc=example,dc=com"[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
  If it&#8217;s working then it should list all the entries that we created in the init.ldif file.

[/SIZE][/FONT][CENTER][FONT=Verdana][SIZE=2][SIZE=3][COLOR=RoyalBlue]**Samba**[/COLOR][/SIZE][/SIZE][/FONT][FONT=Verdana]
[/FONT] [/CENTER]
[FONT=Verdana][SIZE=2] 

**At-a-Glance**
  1.Install Samba
  2.Configure Samba
  3.Configure smbldap-tools
[COLOR=RoyalBlue]
**Install Samba**[/COLOR] 

  Again, we have two options of installing Samba.  For those who want to use a bash prompt:
[/SIZE][/FONT][INDENT][FONT=Verdana]> apt-get --yes install samba   libpam-smbpass smbldap-tools[/FONT][/INDENT][FONT=Verdana][SIZE=2] 
  For the Synaptic fans make sure you install the following packages
[/SIZE][/FONT]                                                       
[LIST]
[*][FONT=Verdana][SIZE=2]samba (not samba 4!  I've discovered at the time of this writing Samba 3.4 is one of two versions (the other is 3.3.4) of samba that can allow Windows 7 machines to join the domain!  samba 4 ***might*** work, but use it at your own risk!  So PLEASE use 3.4!)[/SIZE][/FONT]
[*][FONT=Verdana]libpam-smppass[/FONT]
[*][FONT=Verdana]smbldap-tools[/FONT]
[/LIST]
[FONT=Verdana][SIZE=2] [COLOR=RoyalBlue]**Configure Samba for use with LDAP**[/COLOR]

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   1.Create Samba folders that have not been automatically created ..[/SIZE][/FONT][FONT=Verdana]


[/FONT]>   [FONT=Verdana][SIZE=2]mkdir -v   /var/lib/samba/profiles[/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]chmod 777   /var/lib/samba/profiles[/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]mkdir -v -p   /var/lib/samba/netlogon[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   2.Edit the smb.conf file[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]gedit   /etc/samba/smb.conf[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
  Delete EVERYTHING that is there and replace it with the following.  Be sure to replace EXAMPLE with your information.

          [/SIZE][/FONT]```
[FONT=Verdana][SIZE=2]
[global]
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2] # Domain name ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]workgroup = EXAMPLE        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# Server name - as seen by Windows PCs ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]netbios name = SERVERNAME        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# Be a PDC ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]domain logons = Yes        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]domain master = Yes        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# Be a WINS server ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]wins support = true         [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]obey pam restrictions = Yes        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]dns proxy = No        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]os level = 35        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]log file = /var/log/samba/log.%m        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]max log size = 1000        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]syslog = 0        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]panic action = /usr/share/samba/panic-action %d        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]pam password change = Yes         [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# Allows users on WinXP PCs to change their password when they press Ctrl-Alt-Del[/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]unix password sync = no        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]ldap passwd sync = yes         [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# Printing from PCs will go via CUPS ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]load printers = yes        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]printing = cups        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]printcap name = cups         [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# Use LDAP for Samba user accounts and groups ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]passdb backend = ldapsam:ldap://localhost         [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# This must match init.ldif ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]ldap suffix = dc=example,dc=com        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# The password for cn=admin MUST be stored in /etc/samba/secrets.tdb        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# This is done by running 'sudo smbpasswd -w'.        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]ldap admin dn = cn=admin,dc=example,dc=com         [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# 4 OUs that Samba uses when creating user accounts, computer accounts, etc.        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# (Because we are using smbldap-tools, call them 'Users', 'Computers', etc.)        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]ldap machine suffix = ou=Computers        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]ldap user suffix = ou=Users        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]ldap group suffix = ou=Groups        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]ldap idmap suffix = ou=Idmap        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# Samba and LDAP server are on the same server in this example.        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]ldap ssl = no         [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# Scripts for Samba to use if it creates users, groups, etc.        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]add user script = /usr/sbin/smbldap-useradd -m '%u'        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]delete user script = /usr/sbin/smbldap-userdel %u        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]add group script = /usr/sbin/smbldap-groupadd -p '%g'        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]delete group script = /usr/sbin/smbldap-groupdel '%g'        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'         [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# Script that Samba users when a PC joins the domain .. [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]       # (when changing 'Computer Properties' on the PC)
add machine [/SIZE][/FONT][FONT=Verdana][SIZE=2]script = /usr/sbin/smbldap-useradd -w '%u' [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# Values used when a new user is created ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)    [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]logon drive =        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]logon home =        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]logon path = [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]       logon script =          [/SIZE]

[/FONT]  [FONT=Verdana][SIZE=2]# This is required for Windows XP client .. [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]       server signing = auto        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]server schannel = Auto [/SIZE]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]
[homes]        
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]comment = Home Directories        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]valid users = %S [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]       read only = No        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]browseable = No [/SIZE]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2][netlogon]        
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]comment = Network Logon Service [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]path = /var/lib/samba/netlogon        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]admin users = root        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]guest ok = Yes        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]browseable = No [/SIZE]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]
[Profiles]        
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]comment = Roaming Profile Share        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]# would probably change this to elsewhere in a production system ..        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]path = /var/lib/samba/profiles        
r[/SIZE][/FONT][FONT=Verdana][SIZE=2]ead only = No        profile [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]acls = Yes [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]       browsable = No [/SIZE]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]
[printers] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]       comment = All Printers [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]       path = /var/spool/samba        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]use client driver = Yes        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]create mask = 0600        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]guest ok = Yes        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]printable = Yes        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]browseable = No        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]public = yes [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]writable = yes [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]       admin users = root [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]       write list = root [/SIZE]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]
[print$] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]       comment = Printer Drivers [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]Share        path = /var/lib/samba/printers        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]write list = root        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]create mask = 0664        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]directory mask = 0775        [/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]admin users = root[/SIZE][/FONT] [/INDENT]
```[FONT=Verdana][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   3.Store LDAP password for Samba use[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]smbpasswd -W[/SIZE][/FONT][FONT=Verdana][SIZE=2]   It will display the following[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]Setting stored password for   "cn=admin,dc=example,dc=com" in secrets.tdb[/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]   New SMB password:[/SIZE]
[/FONT] [FONT=Verdana][SIZE=2]   Retype new SMB password:[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Make sure that the password you type in is the same one you created with slappasswd -s[/SIZE][/FONT][FONT=Verdana]


[/FONT]   [FONT=Verdana][SIZE=2]   4.Restart Samba[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]/etc/init.d/samba restart[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] [COLOR=RoyalBlue]
**Configure smbldap-tools**[/COLOR] 

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   1.Getting smbldap-tools ready[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][INDENT]> [FONT=Verdana][SIZE=2]cd /usr/share/doc/smbldap-tools/examples/[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Then execute the following commands[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]cp smbldap_bind.conf /etc/smbldap-tools/
[/SIZE][/FONT][FONT=Verdana][SIZE=2]cp smbldap.conf.gz /etc/smbldap-tools/[/SIZE][/FONT][FONT=Verdana][SIZE=2]
gzip -d /etc/smbldap-tools/smbldap.conf.gz[/SIZE][/FONT][FONT=Verdana][SIZE=2]Open up the smbldap-tools directory:[/SIZE]

[/FONT]>  [FONT=Verdana][SIZE=2]cd /etc/smbldap-tools/[/SIZE][/FONT][FONT=Verdana][SIZE=2]   2.Get your netSID for your domain[/SIZE][/FONT][FONT=Verdana]


[/FONT]>   [FONT=Verdana][SIZE=2]net getlocalsid[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2] It will return something like:[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]SID for domain SERVERNAME is:   S-1-5-21-2899629268-4176875250-2352135513[/SIZE][/FONT][FONT=Verdana][SIZE=2]   

Copy this number[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   3.Edit your smbldap.conf file[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]gedit   /etc/smbldap-tools/smbldap.conf[/SIZE][/FONT][FONT=Verdana][SIZE=2]   

We need to make the following changes, but you cannot just copy and paste them into the file.  You need to search for them and make the adjustments.[/SIZE][/FONT][FONT=Verdana]

[/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]```
SID="S-1-5-21-949328747-3404738746-3052206637" ## This line must have the same SID as when you ran "net getlocalsid"
sambaDomain="EXAMPLE"
ldapTLS="0"
suffix="dc=example,dc=local"
sambaUnixIdPooldn="sambaDomainName=EXAMPLE,${suffix}" ## Be careful with this section!!
userHome="/ldaphome/%U" ## This is found in the UNIX section.
userSmbHome=
userProfile=
userHomeDrive=
userScript=
mailDomain="example.local" 
```[/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]4.[/SIZE][/FONT][FONT=Verdana][SIZE=2]Open the file /etc/smbldap-tools/smbldap_bind.conf file for editing:[/SIZE]

[/FONT]>  [FONT=Verdana][SIZE=2]gedit   /etc/smbldap-tools/smbldap_bind.conf[/SIZE][/FONT][FONT=Verdana][SIZE=2]

Edit the file so the following is correct according to your setup[/SIZE]
[/FONT]```
[FONT=Verdana]
slaveDN="cn=admin,dc=example,dc=local"
slavePw="12345"
masterDN="cn=admin,dc=example,dc=local"
masterPw="12345" [/FONT]
```[FONT=Verdana][SIZE=2]

5.Set the correct permission for the above two files[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]chmod 0644 /etc/smbldap-tools/smbldap.conf       
chmod 0600 /etc/smbldap-tools/smbldap_bind.conf      [/SIZE][/FONT][FONT=Verdana][SIZE=2]   

6.Populate the LDAP database with essential Samba entries. 
This includes the creation of standard groups, such as Administrators and Domain Users.[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]smbldap-populate[/SIZE][/FONT][FONT=Verdana][SIZE=2]   

You will see an output like[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][INDENT]> [FONT=Verdana][SIZE=2]           Populating   LDAP directory for domain EXAMPLE(S-1-5-21-2899629268-4176875250-2352135513)[/SIZE][/FONT][FONT=Verdana]
[/FONT][/INDENT][FONT=Verdana][SIZE=2] At the very end it will ask you to enter a password for samba.  Go ahead and enter the same password you used when you used the command slappasswd &#8211;s

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   7.Stop the LDAP server, run slapindex, and restart the LDAP server.[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2]  
[/SIZE][/FONT][INDENT]> [FONT=Verdana][SIZE=2]/etc/init.d/slapd   stop[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              slapindex 
[/SIZE][/FONT][FONT=Verdana][SIZE=2]              chown openldap:openldap   /var/lib/ldap/*[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              /etc/init.d/slapd start[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
  Slapd should start with no problem.  If it doesn&#8217;t retrace your steps in the config files and check for the following.  Especially check smbladp_bind.conf and make sure you didn&#8217;t misspell your password.  Otherwise check your smbldap.conf file and make sure you made all the appropriate changes. 

  You shouldn&#8217;t need to look anywhere else but those two files.  The reason being that slapd was already running successfully up to this point.  Any reason for its failure should be isolated to the changes you just made.
[B]
[COLOR=RoyalBlue]OpenLDAP[/COLOR][/B]

  **At-a-Glance**
  1.Add a User
  2.Add LDAP authentication
  3.Add a Windows computer to the domain

[COLOR=RoyalBlue]**Add a User**[/COLOR]

  Your directory is almost ready for use, but so far no one is in it!  Let&#8217;s add a user.  I&#8217;ll use the example of matthew, but you might as well change it to be whatever user name you plan on using yourself (we&#8217;ll be giving it root privileges).  I suggest on making the name different from user name you set up during installation just to keep things clean.

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   1.Add the user[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana]>            smbldap-useradd   -a -m -M matthewb -c &#8220;Matthew B&#8221; matthewb[/FONT][/INDENT][INDENT][FONT=Verdana]> 
  The -a sets up a Samba (and UNIX) account
  The -m will create a home directory for the user if one does not yet exist
  The -M sets their username as part of their e-mail
  The -c sets their fully name
  matthewb is the name of the user[/FONT][/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   Before we&#8217;re done setting up this user account, we need to add a password.[/SIZE][/FONT][FONT=Verdana]

> smbldap-passwd matthewb      [/FONT] [FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]   It will prompt you for a password.[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   2.Give it administrator privileges [/SIZE][/FONT][FONT=Verdana]


[/FONT]>   [FONT=Verdana][SIZE=2]/usr/sbin/smbldap-groupmod   -m 'matthewb' 'Administrators'[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              /usr/sbin/smbldap-groupmod   -m 'root' 'Administrators'[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
[COLOR=RoyalBlue]**Configure Authentication**[/COLOR]

[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   1.Add LDAP Authentication on the Server[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]apt-get   --yes install ldap-auth-client[/SIZE][/FONT][FONT=Verdana][SIZE=2]   It will ask you a series of questions, here&#8217;s how to answer them.[/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][INDENT]> [FONT=Verdana][SIZE=2]             LDAP   server Uniform Resource Identifier:ldap://127.0.0.1[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              Distinguished   name of the search base:dc=example,dc=com[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              LDAP   version to use: 3[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              Make   local root Database admin:Yes[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              Does   the LDAP database require login?No[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              LDAP   account for root:cn=admin,dc=example,dc=com[/SIZE][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][SIZE=2]              LDAP   root account password:<   enter the LDAP admin password>>[/SIZE][/FONT][/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   2.Edit your ldap.conf file[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]gedit   /etc/ldap.conf[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Find the following referenced lines and make the changes indicated (Make sure to uncomment them if they are commented out)[/SIZE][/FONT][FONT=Verdana]

[/FONT]```
host 127.0.0.1
base dc=example,dc=loca
luri ldap://127.0.0.1/
rootbinddn cn=admin,dc=example,dc=local
bind_policy soft
```[FONT=Verdana][SIZE=2]

 3.Copy your ldap.conf into the correct folder[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]cp /etc/ldap.conf /etc/ldap/ldap.conf      [/SIZE][/FONT][FONT=Verdana][SIZE=2]   4.Configure the authentication[/SIZE][/FONT][FONT=Verdana]

[/FONT]  [FONT=Verdana][SIZE=2]   Create a new file by running[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]gedit /etc/auth-client-config/profile.d/open_ldap      [/SIZE][/FONT][FONT=Verdana][SIZE=2]   Copy and paste the following into the new file

[/SIZE][/FONT]```
[open_ldap]
nss_passwd=passwd: compat ldap
nss_group=group: compat ldap
nss_shadow=shadow: compat ldap
nss_netgroup=netgroup: nis
pam_auth=auth          required                   pam_env.so 
        auth                sufficient               pam_unix.so likeauth nullok 
        auth                sufficient               pam_ldap.so use_first_pass 
        auth                required                    pam_deny.so
pam_account=account      sufficient            pam_unix.so 
       account                sufficient               pam_ldap.so 
       account                 required                   pam_deny.so
pam_password=password           sufficient          pam_unix.so nullok md5 shadow use_authtok 
        password                     sufficient            pam_ldap.so use_first_pass 
        password                          required                   pam_deny.so
pam_session=session      required                     pam_limits.so 
        session                   required                  pam_mkhomedir.so skel=/etc/skel/ umask=0077 
        session                  required               pam_unix.so 
        session                  optional                pam_ldap.so
```[FONT=Verdana][SIZE=2]

5.Enable the new profile[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]auth-client-config -a -p open_ldap      [/SIZE][/FONT][FONT=Verdana][SIZE=2]   If you receive the following error:[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]Error in updating the file: 'nss_netgroup'   not found[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Then open your open_ldap file[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]gedit   /etc/auth-client-config/profile.d/open_ldap[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Delete the line that says[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]nss_netgroup=netgroup: nis      [/SIZE][/FONT][FONT=Verdana][SIZE=2]   And replace it with[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]nss_netgroup=netgroup:   compat ldap[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Finally, run the[/SIZE][/FONT][FONT=Verdana]

[/FONT]>  [FONT=Verdana][SIZE=2]auth-client-config   -a -p open_ldap[/SIZE][/FONT][FONT=Verdana][SIZE=2]   Command again, you&#8217;ll get server error messages about how a certain command already exists. As long as you do not see[/SIZE][/FONT][FONT=Verdana]

> Error in updating the file: 'nss_netgroup'   not found[/FONT] [FONT=Verdana][SIZE=2]   Then everything installed correctly and you&#8217;re good to go![/SIZE][/FONT][FONT=Verdana]
[/FONT] [/INDENT][FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]   6.Enable Samba in Firewall[/SIZE][/FONT][FONT=Verdana]

All that's left to do is to allow Samba services through your firewall [/FONT](Ports 137-139 and 445)[FONT=Verdana].  This is necessary because we are using Samba as a stop-gap between LDAP and the windows machines.


[/FONT]    [FONT=Verdana][SIZE=2]   7.Restart the server
[/SIZE][/FONT][/INDENT][FONT=Verdana]You can now join a computer to your domain like normal (If you are using XP, Vista and 7 have some more steps on the client's end).  When it prompts you for a user name with administrative passwords, **don't use root**.  Use the one you made.  The reason is that Ubuntu disables root, so I don't think that username will work if you try to use it.

I really hope this guide helps you.  Windows and openLDAP certainly aren't the easiest thing to get to work together (A direct authentication via Kerberos would be awesome), but it CAN be done!  Good luck guys (and gals too I guess:P)!

[/FONT]   [FONT=Verdana][COLOR=RoyalBlue]**[SIZE=2]Getting Vista and Windows 7 to Join Domain[/SIZE]**[/COLOR][/FONT][FONT=Verdana]
[B]
THIS IS _NOT_ NECESSARY FOR XP MACHINES!
[/B] [/FONT]  [FONT=Verdana][COLOR=Black]
While getting one of my machines to join the domain I learned two very nasty little tidbits.  The first is that [/COLOR][/FONT][FONT=Verdana]Vista and 7 have about 3 too many versions (stupid Microsoft) and for some reason only professional and up have the ability to actually join a domain.  The second thing I learned was that they both require some... convincing to join a Samba domain.  I don't have Vista so I couldn't test if the second part was needed or not, if you use vista please let me know if it worked and if it didn't what did work for you in the end.


Steps for both Windows 7 and Vista on a Samba Domain.
[/FONT][INDENT][FONT=Verdana]1. Click on the Windows button (It used to be the Start button)

2. In the "Search programs and files" box type in "secpol.msc"

3. Go to:[/FONT][INDENT][FONT=Verdana]Local Policies -> Security Options
[/FONT] [/INDENT][FONT=Verdana]4. Find the Policy named "Network Security: LAN Manager authentication level.

5. Change it to "Send LM & NTLM - use NTLMv2 session security if negotiated"

6. Click okay and close the secpol.msc window.

[/FONT]    [/INDENT][FONT=Verdana]At this point, I am unaware of anything else Vista needs to get onto the domain.  Windows 7, however needs some more work.
[/FONT][INDENT][FONT=Verdana]1. Samba 3.4 **MUST** be installed.  I mentioned this earlier but there are some known issues with samba and windows 7.  Samba 3.4 does not have those problems (3.4 is, at the time of this writing, the most recent version of the "samba" package)

2. You need to make the following registry edits

Go to: [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\LanmanWorkstation\Parameters]

And add two new dword values:

&#8220;DomainCompatibilityMode&#8221; (set to 1)
&#8220;DNSNameResolutionRequired&#8221; (set to 0)

 The above need to be added to allow the join to work.

Then go to: [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Netlogon\Parameters]

And make sure the following two values are set to 1 (they should already exist)

&#8220;RequireSignOrSeal&#8221;
&#8220;RequireStrongKey&#8221;

[/FONT]           [/INDENT][FONT=Verdana]Okay, Windows 7 should now join the domain!  Good luck to all![/FONT]

---

### Post by evayroberto on 2009-12-01
Hi. Thanks for this tutorial. I'm trying to install it in Ubuntu 9.04 server.
I have a problem when 
slapadd -v -l /etc/ldap/init.ldif
It shows an error

/etc/ldap/slapd.conf: line 10: unknown directive <Global> outside backend info and database definitions.
slapadd: bad configuration file!

If I add a #, like in your other thread about ldap, a new error is showed, and now I dont know how to solve it.


root@linuxserver:/etc/ldap# slapadd -v -l /etc/ldap/init.ldif
/etc/ldap/slapd.conf: line 112: warning: no by clause(s) specified in access line.
<access clause> ::= access to <what> [ by <who> [ <access> ] [ <control> ] ]+ 
<what> ::= * | dn[.<dnstyle>=<DN>] [filter=<filter>] [attrs=<attrspec>]
<attrspec> ::= <attrname> [val[/<matchingRule>][.<attrstyle>]=<value>] | <attrlist>
<attrlist> ::= <attr> [ , <attrlist> ]
<attr> ::= <attrname> | @<objectClass> | !<objectClass> | entry | children
<who> ::= [ * | anonymous | users | self | dn[.<dnstyle>]=<DN> ]
	[ realanonymous | realusers | realself | realdn[.<dnstyle>]=<DN> ]
	[dnattr=<attrname>]
	[realdnattr=<attrname>]
	[group[/<objectclass>[/<attrname>]][.<style>]=<group>]
	[peername[.<peernamestyle>]=<peer>] [sockname[.<style>]=<name>]
	[domain[.<domainstyle>]=<domain>] [sockurl[.<style>]=<url>]
	[dynacl/<name>[/<options>][.<dynstyle>][=<pattern>]]
	[ssf=<n>] [transport_ssf=<n>] [tls_ssf=<n>] [sasl_ssf=<n>]
<style> ::= exact | regex | base(Object)
<dnstyle> ::= base(Object) | one(level) | sub(tree) | children | exact | regex
<attrstyle> ::= exact | regex | base(Object) | one(level) | sub(tree) | children
<peernamestyle> ::= exact | regex | ip | ipv6 | path
<domainstyle> ::= exact | regex | base(Object) | sub(tree)
<access> ::= [[real]self]{<level>|<priv>}
<level> ::= none|disclose|auth|compare|search|read|{write|add|delete}|manage
<priv> ::= {=|+|-}{0|d|x|c|s|r|{w|a|z}|m}+
<control> ::= [ stop | continue | break ]
dynacl:
	<name>=ACI	<pattern>=<attrname>

slapadd: bad configuration file!

Do you know any solution??
Thanks

---

### Post by abishur on 2009-12-01
> **evayroberto said:**
> Hi. Thanks for this tutorial. I'm trying to install it in Ubuntu 9.04 server.
I have a problem when 
slapadd -v -l /etc/ldap/init.ldif
It shows an error
 
/etc/ldap/slapd.conf: line 10: unknown directive <Global> outside backend info and database definitions.
slapadd: bad configuration file!
 
If I add a #, like in your other thread about ldap, a new error is showed, and now I dont know how to solve it.
 
 
 
Are you using slapd.conf file or the slapd.d directory structure?  If you're using the slapd.d directory structure than I'm afraid I don't know how to help you.  I got fed up trying to figure that garbage out, an update that makes the software 10 times more difficult to use is... well Windows Vista is the best analogy I can think of.
 
Well, my little soapbox aside, if you are using the slapd.conf like I did, make sure you updated the information in [SIZE=2]/etc/default/slapd.  It's not enough to just add a slapd.conf file, you have to make certain slapd knows to use it.[/SIZE]
 
It's also possible that there's a problem with the ldif file.  There are 6 places where you need to change "dc=example,dc=local" to your network's information.
 
Would you mind posting your ldif file?  Maybe with two pairs of eyes we can spot what's going on.

---

### Post by AlexanderDGreat on 2009-12-01
Hi, I really appreciate the time and effort you put in this tutorial. The reason I haven't done this tutorial or this one for 9.04: 

[http://ubuntuforums.org/showthread.php?t=1184288]("http://ubuntuforums.org/showthread.php?t=1184288")

is because of this command:

> rm -r /etc/ldap/slapd.d 

How would this affect future versions of OpenLDAP? But I found this great guide in YouTube explaining how to install OpenLDAP in 8.04 LTS. He's the only one with a VIDEO on how to do it in the entire universe! If I'm wrong, pls. tell me otherwise.

[http://www.youtube.com/watch?v=DM_UQVVVtoY]("http://www.youtube.com/watch?v=DM_UQVVVtoY")

[http://www.youtube.com/watch?v=kSCx3tzC0cA]("http://www.youtube.com/watch?v=kSCx3tzC0cA")


So I emailed the guy about the 9.04 guide, and assumes this is quite similar to it and asked for his opinion. I think he looked at the guide, but he told me that he would only recommend an Hardy Heron LTS Server because a server is critical to a production environment.

Now, what do you think? Also, would you agree that an LTS is better because it's critical to a production environment?

Waiting for your kind response. :)

---

### Post by abishur on 2009-12-01
> **AlexanderDGreat said:**
> 

How would this affect future versions of OpenLDAP? 

As I mentioned in the post itself, it is a known fact that the designers of slapd already plan to remove slapd.conf support at some unknown future time.  However, I, and many others besides, are reluctant to upgrade because it is such a cumbersome change.  The features the new slapd offers are nice, but in my opinion not too big a deal.  The main selling point of the new slapd structure is dynamic updating.  This means that you no longer need to restart slapd when you modify it.   Okay, that's nice, but once I get slapd set up, how often do I really mess with it? (so far the answer is seldom to never).  On the negative side of the update, is the fact that the makers decided to make every single little change so MASSIVE to enact.  I literally wasted DAYS trying to work out their new system before just going back to the old slapd.conf system.

**SO** to answer you question.  How will it affect the future?  Well best case scenario, the makers realize that it would be folly to isolate such a large group of its users and continue supporting slapd.conf.  Worst case scenario, some time down the line you run a simple conversion script which takes the slapd.conf file and turns it into a slapd.d directory, not a big deal at all.

> 

But I found this great guide in YouTube explaining how to install OpenLDAP in 8.04 LTS. He's the only one with a VIDEO on how to do it in the entire universe! If I'm wrong, pls. tell me otherwise.

[http://www.youtube.com/watch?v=DM_UQVVVtoY](http://www.youtube.com/watch?v=DM_UQVVVtoY)

[http://www.youtube.com/watch?v=kSCx3tzC0cA](http://www.youtube.com/watch?v=kSCx3tzC0cA)


So I emailed the guy about the 9.04 guide, and assumes this is quite similar to it and asked for his opinion. I think he looked at the guide, but he told me that he would only recommend an Hardy Heron LTS Server because a server is critical to a production environment.

Now, what do you think? Also, would you agree that an LTS is better because it's critical to a production environment?

Waiting for your kind response. :)

When trying to set up my own ldap server, I also ran into his video.  It is a very well made video but, in my humble opinion, not very useful.  It gave me a very good understanding of what LDAP was and phpldapadmin, but it wasn't so useful for setting up slapd (at least for me).

Everyone has their own "this = best" version of Linux.  Having used 8.04 I can honestly say that you would actually be crippling yourself if you limited yourself to that.  9.10 is completely stable, but if you're really worried about it, at least use 9.04 (which this guide also works for by the way).

To go one step further, let me give you this piece of advice:  Linux is a great free choice for small business/ home set ups.  If you truly want the best server, the most dependable server with the best documentation for help, go windows server 2003 or 2008.  I know, that's heresy on a Linux forum, but the simple truth is Windows computers have no problem connecting to a windows server :(

That said, if you have the time to learn Linux or lack the budget for Windows then Linux is a WONDERFUL tool to learn, and Ubuntu is the best version I used by far.

---

### Post by evayroberto on 2009-12-02
Hi Abishur
Here is my init.ldif file

dn: dc=ibertestint,dc=local
objectClass: dcObject
objectClass: organizationalUnit
dc: ibertestint
ou: Ibertestint

dn: cn=admin,dc=ibertestint,dc=local
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: {SSHA}rKSjdNNqC3jhKgFslXLrShe/stIRxhOG

dn: ou=Users,dc=ibertestint,dc=local
objectClass: organizationalUnit
ou: Users

dn: ou=Groups,dc=ibertestint,dc=local
objectClass: organizationalUnit
ou: Groups

dn: ou=Computers, dc=ibertestint,dc=local
objectClass: organizationalUnit
ou: Computers

dn: ou=Idmap,dc=ibertestint,dc=local
objectClass: organizationalUnit
ou: Idmap

The error seems to be in the slapd.conf file, about line 112, after lastmod on line, but I dont find any error :confused
So, I post the slapd.conf too

# Remember to replace suffix "dc=example,dc=local" with your domain name
# Change the rootpw entry with the results from slappaswd (Must match the same you pasted on init.ldif)

# /etc/ldap/slapd.conf
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

################################################## ######################

# Global Directives:
# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/samba.schema
include /etc/ldap/schema/misc.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible valuesloglevel 0
# Where the dynamically loaded modules are stored
modulepath /usr/lib/ldap
moduleload back_bdb

# The maximum number of entries that is returned for a search
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

################################################## #####################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend bdb
#checkpoint 512 30

################################################## #####################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend <other>

################################################## #####################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database bdb

# The base of your directory in database #1
suffix "dc=ibertestint,dc=local"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn "cn=admin,dc=ibertestint,dc=local"
rootpw {SSHA}rKSjdNNqC3jhKgFslXLrShe/stIRxhOG

# Where the database file are physically stored for database #1
directory "/var/lib/ldap"

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
#index objectClass eq, pres
index ou,cn,sn,mail,givenname eq,pres,sub
index uidNumber,gidNumber,memberUid eq,pres
index loginShell eq,pres
index uniqueMember eq,pres
index uid pres,sub,eq
index displayName pres,sub,eq
index sambaSID eq
index sambaPrimaryGroupSID eq
index sambaDomainName eq
index default sub
# index uid pres,eq,sub

# Save the time that the entry gets modified, for database #1
lastmod         on


# Where to store the replica logs for database #1
# replogfile /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
by dn="cn=admin,dc=ibertestint,dc=local" write
by anonymous auth
by self write
by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms. Without this you may
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
by dn="cn=admin,dc=ibertestint,dc=local" write
by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
# by dn="cn=admin,dc=example,dc=ch" write
# by dnattr=owner write

################################################## ####################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database <other>

# The base of your directory for database #2
#suffix "dc=debian,dc=org"

Again, thanks for help me

---

### Post by evayroberto on 2009-12-02
This problem...SOLVED!!!
I had to write all "by" in the same line of "access", not in different lines. 
The configuration continues..:p

---

### Post by abishur on 2009-12-02
> **evayroberto said:**
> This problem...SOLVED!!!
I had to write all "by" in the same line of "access", not in different lines. 
The configuration continues..:p

Good catch!  I was just looking over my own slapd.conf file and I noticed that for some reason when I posted it in the thread above it took out all my spaces at the beginning of the lines!  I'm going to try to fix that so no one else has the same problem you had.  Slapd takes every line with a space at the beginning and goes "Oh, that's part of the previous line".  So the fact that my spaces were removed when I posted it could really cause problems!  Fortunately, I don't believe samba is the same way.

Edit:  Okay, I got the indentation problem fixed, sorry for not catching that when I posted it originally!  Also, I caught a typo in my smb.conf file.  In the [Profiles] section, there was a line that said "ead only = no" it was supposed to say "read only = no" but the r is on the line above it.  When I originally pasted my file in there, it was just a single mess on one big line (For some reason posting it took away all my nice little edits).  Oh, well.  I checked over the rest of my post for typos and couldn't find any so there shouldn't be any more problems for you.  Also, just went through a TON of problems getting a Windows 7 machine to join, so I'll be posting my solution to that in case you're using Vista or 7 too (I'll edit the main post for that and put it at the end of it)

Edit 2: Instructions for Vista and 7 have been added!

---

### Post by evayroberto on 2009-12-02
I have seen your new Windows 7 guide to join samba domain..and, only with Samba 3.4?? I have installed 3.3.2, two weeks ago. Are you sure it will not works with my Samba versión?

---

### Post by abishur on 2009-12-02
From my understanding of what I've read [here]("http://www.1stbyte.com/2009/05/31/join-windows-7-to-samba-pdc/") it requires either 3.3.4 or 3.4 but will not work on 3.3.2.  That said, the page in question also incorrectly lists a registry value to add, so he could be wrong about the version:confused:.  I'd say give it a shot with the version you're using.  It's not like you're really going to loose anything by trying.  You still have to make the registry changes, so if you find it doesn't work after you've made them it's not like you wasted your time.  But if it does work, well then you've saved yourself the hassle of the samba upgrade!

Let me know if it works out for you!

---

### Post by evayroberto on 2009-12-02
Well, I have tried, and its not working neither xp or 7. In XP the error showed is "network path not found", but xp workstation can ping samba server to ip and to name. From windows 7 workstation, the error is different: cant contact with an Active Directory in the domain Ibertestint...????
Maybe I am wrong, but...its necessary to join the domain from the server itself with net rpc command? Maybe its a /etc/hosts wrong setup??

---

### Post by AlexanderDGreat on 2009-12-02
Thank you Abishur! Now at least I'm confident to try it.

---

### Post by abishur on 2009-12-02
> **evayroberto said:**
> Well, I have tried, and its not working neither xp or 7. In XP the error showed is "network path not found", but xp workstation can ping samba server to ip and to name. From windows 7 workstation, the error is different: cant contact with an Active Directory in the domain Ibertestint...????


hmm.... first off, just to be sure, you didn't do the reg edit to the XP machines right?  The XP machines *should* be able to connect without any additional changes.

Second are you using a firewall on the Linux computer ?  If you are, make sure to have the ports open for Samba (Ports 137-139 and 445).

Finally, if those don't work, go ahead and update to Samba 3.4.  It was worth a shot to see if you could get it to work with the samba you already had installed, but no sense in beating a dead horse when you have a nice living one right next to you ;)

> **AlexanderDGreat said:**
> Thank you Abishur! Now at least I'm confident to try it.

Good luck Alex!  I hope my guide works well for you!

---

### Post by evayroberto on 2009-12-02
I'm very confused, because the message is always like Samba is not reachable through the network, but I can ping it with success. No logon window is showed when i try to change the domain in Windows workstation..As far as I know, a window logon must be showed :-(
The server has not firewall activated.
Same issues happens when I setup the server as Active Directory member...if problems continues, I think my boss will force us to change to windows environment.:-(

---

### Post by abishur on 2009-12-02
> **evayroberto said:**
> I'm very confused, because the message is always like Samba is not reachable through the network, but I can ping it with success. No logon window is showed when i try to change the domain in Windows workstation..As far as I know, a window logon must be showed :-(
The server has not firewall activated.
Same issues happens when I setup the server as Active Directory member...if problems continues, I think my boss will force us to change to windows environment.:-(

Yes,  when you change to a new domian it should pop up a dialog window asking for authentication to prove you're allowed to join said domain.  The problem isn't that the samba server can't be pinged, the problem lies somewhere in the communication between windows and Samba.  Basically samba acts as a translator between Linux Networking and Windows Networking, and the older versions of Samba don't quite translate it correctly. Beyond that, I'm afraid my knowledge of the exact details are incomplete other than the fact that I know Version 3.4 does not have this problem while other versions of it do.

This means that while TCP/IP is working and therefore the server is pingable, the actual communication between the two... gets lost in translation.

---

### Post by evayroberto on 2009-12-02
Solved again!! The problem was the f...k UFW, I think it was disabled but no. 
From XP it works like a charm!!
Tomorrow I'll try with windows 7.
Thanks for all Abishur.

---

### Post by detrate on 2009-12-08
> **abishur said:**
> I have used the guide at least 4 times on a clean install of Ubuntu 9.10. It has worked 100% without so much as a hiccup. It should work for you too ;)

I'm sorry but I do not believe you.  At least 3 of your code blocks have formatting errors you have not fixed... amongst other problems I've run into.

While I appreciate the update, I think the predecessor of this article is more bug free.

---

### Post by abishur on 2009-12-08
> **detrate said:**
> I'm sorry but I do not believe you.  At least 3 of your code blocks have formatting errors you have not fixed... amongst other problems I've run into.

While I appreciate the update, I think the predecessor of this article is more bug free.

This article was created from a word file I *_**have**_* used over 4 times on my own computer without so much as a pause.  Furthermore, evayroberto, was able to use this guide to get up and running, so we know for a fact that it works for me and at least one other person.  There was an error in my slapd that was created when I copied it into the ubuntu forums (apparently they remove leading spaces).  I've done my best to catch these mistakes that the post process created, but if you've noticed one that I've missed, I would appreciate the feedback.  However, it helps no one to complain about general "errors" without listing them so I can get them cleaned up.  

And with all respect, the reason I made this post in the first place was because of how incomplete the previous post was in relation to 9.10 and even 9.04.  It was simply outdated and did not cooperate with the updated software.

So, as I said, if you noticed an error in a code block, please list it so I can get it back to the way its supposed to work.  And go ahead and list these "other problems" I mean, it makes no sense not to get help if you hit a unique problem, right?

---

### Post by cbhr4u on 2009-12-10
> **evayroberto said:**
> This problem...SOLVED!!!
I had to write all "by" in the same line of "access", not in different lines. 
The configuration continues..:p
  Hey abishur, first just wanted to thank you for taking the time to make this guide! I am having the same problem evayroberto was having but I am not understanding the solution, can you give a little bit more explanation? I tried to put all the by lines on the same as access but i am getting the same error? Any help would be greatly appreciated!

---

### Post by abishur on 2009-12-10
> **cbhr4u said:**
> Hey abishur, first just wanted to thank you for taking the time to make this guide! I am having the same problem evayroberto was having but I am not understanding the solution, can you give a little bit more explanation? I tried to put all the by lines on the same as access but i am getting the same error? Any help would be greatly appreciated!

I'm really sorry about this error, the problem lies in the way the forum removes the beginning space from the line.  I've made a note about it in the original post so hopefully new people won't hit this problem :(

OKAY!  I  finally figured out how to make the file look the way I want it to on these forums!  I am REALLY sorry it took so long.  Go back and look at the original post to get the correct formatting to make slapd work (smaba is fine)[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

---

### Post by kwadman on 2009-12-11
I'm getting stuck at the end of LDAP. config file
any idea's please...



root@server02:/home/user# slapadd -v -l /etc/ldap/init.ldif
/etc/ldap/slapd.conf: line 8: unknown directive <########################################################################> outside backend info and database definitions.
slapadd: bad configuration file!

---

### Post by abishur on 2009-12-11
> **kwadman said:**
> I'm getting stuck at the end of LDAP. config file
any idea's please...



root@server02:/home/user# slapadd -v -l /etc/ldap/init.ldif
/etc/ldap/slapd.conf: line 8: unknown directive <########################################################################> outside backend info and database definitions.
slapadd: bad configuration file!

If you saw my original post, ignore it!  The problem is on line 8 of your slapd.conf file.  At the very beginning of the ######## line is a space.  Remove that space and save it.  (Also I fixed that mistake in the original post!)

---

### Post by cbhr4u on 2009-12-11
> **abishur said:**
> I'm really sorry about this error, the problem lies in the way the forum removes the beginning space from the line.  I've made a note about it in the original post so hopefully new people won't hit this problem :(

OKAY!  I  finally figured out how to make the file look the way I want it to on these forums!  I am REALLY sorry it took so long.  Go back and look at the original post to get the correct formatting to make slapd work (smaba is fine)[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
 

Hey abishur,
I am still getting that same error, when you have a minute do you mind looking over my slapd.conf? I'm sure I am making some rookie mistake somewhere lol! Thanks again for all your help I really appreciate it!


# Remember to replace suffix "dc=example,dc=local" with your domain name
# Change the rootpw entry with the results from slappaswd (Must match the same you pasted on init.ldif) 

# /etc/ldap/slapd.conf
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

######################################################################## 

Global Directives: 
# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/samba.schema
include /etc/ldap/schema/misc.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible valuesloglevel        0
# Where the dynamically loaded modules are stored
modulepath /usr/lib/ldap
moduleload back_bdb

# The maximum number of entries that is returned for a search
operationsizelimit 500 

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1 

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend bdb
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
database bdb 

# The base of your directory in database #1
suffix "dc=BEAVER,dc=local" 

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn "cn=admin,dc=BEAVER,dc=local"
rootpw {SSHA}8F5/srwaQhHwFlN0+nzfg6kYtCDJy8xo 

# Where the database file are physically stored for database #1
directory "/var/lib/ldap" 

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
#index     objectClass eq, pres
index ou,cn,sn,mail,givenname eq,pres,sub
index uidNumber,gidNumber,memberUid eq,pres
index loginShell eq,pres
index uniqueMember eq,pres
index uid pres,sub,eq
index displayName pres,sub,eq
index sambaSID eq
index sambaPrimaryGroupSID eq
index sambaDomainName eq
index default sub
#index   uid pres,eq,sub 

# Save the time that the entry gets modified, for database #1
lastmod on 

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog 

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
 by dn="cn=admin,dc=BEAVER,dc=local"  write
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
 by dn="cn=admin,dc=BEAVER,dc=local" write        
 by * read 
 
# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#                          by dn="cn=admin,dc=BEAVER,dc=ch" write
#                   by dnattr=owner write 

######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other> 

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"

---

### Post by abishur on 2009-12-11
Hey cbhr4u, the problem is found in these two blocks of code
 
```
access to attrs=userPassword,shadowLastChange,sambaNTPasswor d,sambaLMPassword
by dn="cn=admin,dc=BEAVER,dc=local" write
by anonymous auth
by self write
by * none 

```
 
```
access to *
by dn="cn=admin,dc=BEAVER,dc=local" write 
by * read 

```
 
the lines that say "by" are supposed to have a space in the front of them also it looks like the "sambaNTPassword" has a space between the r and the d. The correct code should look like this:
 
```
access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
    by dn="cn=admin,dc=BEAVER,dc=local" write
    by anonymous auth
    by self write
    by * none 
```
 
```
access to *
    by dn="cn=admin,dc=BEAVER,dc=local" write 
    by * read 
```
 
Like I was saying, until recently I did not know how to make this forum let me put extra spaces at the beginning of the line, so it was messing up the slapd file.  You should be good to go after fixing those two blocks.

---

### Post by cbhr4u on 2009-12-11
> **abishur said:**
> Hey cbhr4u, the problem is found in these two blocks of code
 
```
access to attrs=userPassword,shadowLastChange,sambaNTPasswor d,sambaLMPassword
by dn="cn=admin,dc=BEAVER,dc=local" write
by anonymous auth
by self write
by * none 

``````
access to *
by dn="cn=admin,dc=BEAVER,dc=local" write 
by * read 

```the lines that say "by" are supposed to have a space in the front of them also it looks like the "sambaNTPassword" has a space between the r and the d. The correct code should look like this:
 
```
access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
    by dn="cn=admin,dc=BEAVER,dc=local" write
    by anonymous auth
    by self write
    by * none 
``````
access to *
    by dn="cn=admin,dc=BEAVER,dc=local" write 
    by * read 
```Like I was saying, until recently I did not know how to make this forum let me put extra spaces at the beginning of the line, so it was messing up the slapd file.  You should be good to go after fixing those two blocks.

Hey Abishur,
Thanks again for all your help i made those corrections but no go, I took a screen shot of that code block from my terminal window, when you have a moment will you take a look at it? Thanks again!!

---

### Post by abishur on 2009-12-11
I don't see anything wrong with that block of code... can you post your actual errror message?  I know the first time I set up my domain I had a TON of problems.  It's easy to miss one part and have the whole fail.  It's even easier to look in the wrong place for a solution not realize it's not where you made your mistake.  Go ahead and go over the guide from the beginning.  It might help to just earse the slapd file and copy and paste the code fresh?

---

### Post by cbhr4u on 2009-12-11
> **abishur said:**
> I don't see anything wrong with that block of code... can you post your actual errror message?  I know the first time I set up my domain I had a TON of problems.  It's easy to miss one part and have the whole fail.  It's even easier to look in the wrong place for a solution not realize it's not where you made your mistake.  Go ahead and go over the guide from the beginning.  It might help to just earse the slapd file and copy and paste the code fresh?

Thanks for taking the time to look at this for me! Here is the actual error message.
/etc/ldap/slapd.conf: line 10: unknown directive <Global> outside backend info and database definitions.
slapadd: bad configuration file!

I have redone it earlier but i will give it another shot. Probably a stupid question but it doesnt matter that i am using vi instead of gedit does it? Thanks again.

---

### Post by abishur on 2009-12-11
hmm... it's trying to say that there is something wrong on line 10 of your slapd.conf file (the line that says Global Directives: ) but I'm just not seeing a problem there.  Do you have a space at the beginning of that line (if so delete it).  It doesn't matter if you use vi, nano, or gedit.  I use gedit because I personally find it easier to work with and catch mistakes.  Some people use vi either out of a sense of "Linux Purity" or because the purists tell them to use it :P Use whatever you're comfortable with using.

If all else fails start at the beginning and take it slow.  I literally do not remember how many times I had to start over from scratch while learning how to do this.  Keep it up!  Sometimes just having someone to talk about what's going on helps you find the real problem!

---

### Post by AlexanderDGreat on 2009-12-13
Hi abishur, I've a question, can Ubuntu pass policies to Windows clients authenticating to Ubuntu? Or what are the benefits of authentication using LDAP over just adding users on the Ubuntu Server? Thanks.

---

### Post by abishur on 2009-12-13
> **AlexanderDGreat said:**
> Hi abishur, I've a question, can Ubuntu pass policies to Windows clients authenticating to Ubuntu? Or what are the benefits of authentication using LDAP over just adding users on the Ubuntu Server? Thanks.

The following is my understanding, but someone with more expertise might now some better answer.


**Can Ubuntu pass Poclies?  **Well.... yesno from what I've read Samba 4 will actually have built in Windows client authoring (and therefore completely replace the need for this guide) as well as the ability to apply group policies.  I've also seen [some software]("http://www.nitrobit.com/grouppolicy.html") that claims to be able to do the job, but it costs money.

But remember!  LDAP is a protocol of authentication.  Active Directory and OpenLDAP are merely software that makes use of the LDAP protocol.  NEITHER AD or OpenLDAP have the ability to assign group policies.  Windows uses a special piece of software that interacts with AD (using the LDAP authentication protocol) to apply group policies.

**Benefits of Authenticating with LDAP?** My understanding is that Windows computers cannot authenticate to native Linux accounts.  The whole point of using OpenLDAP is to provide a means of windows authentication (well... there are other benefits such as a security flexibility, centralized management, etc.).  That said, just because LDAP is the only means I could find for windows authentication, doesn't mean it's the only one out there, and if you're dealing with a pure Linux environment, then  using the Linux accounts would work fine for you (of course, since you're looking at this guide I think I can assume that you have windows computers to authenticate ;) )

---

### Post by cbhr4u on 2009-12-14
> **abishur said:**
> hmm... it's trying to say that there is something wrong on line 10 of your slapd.conf file (the line that says Global Directives: ) but I'm just not seeing a problem there.  Do you have a space at the beginning of that line (if so delete it).  It doesn't matter if you use vi, nano, or gedit.  I use gedit because I personally find it easier to work with and catch mistakes.  Some people use vi either out of a sense of "Linux Purity" or because the purists tell them to use it :P Use whatever you're comfortable with using.

If all else fails start at the beginning and take it slow.  I literally do not remember how many times I had to start over from scratch while learning how to do this.  Keep it up!  Sometimes just having someone to talk about what's going on helps you find the real problem!

Hey abishur,
Got the line 10 problem licked but when i run the slapadd I am getting this error,

/etc/ldap/slapd.conf: line 116: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 133: rootdn is always granted unlimited privileges.
added: "dc=BEAVER,dc=local" (00000001)
<= str2entry: str2ad(Password): attribute type undefined
slapadd: could not parse entry (line=7)
_#########             49.35% eta   none elapsed            none spd  49.6 k/s
Closing DB...

I know its referencing line 7 just not sure if its on the init.ldif or the slapd.conf 
Let me know your thoughts when you get a chance I really appreciate all the help my friend.

---

### Post by abishur on 2009-12-14
> **cbhr4u said:**
> Hey abishur,
Got the line 10 problem licked but when i run the slapadd I am getting this error,

/etc/ldap/slapd.conf: line 116: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 133: rootdn is always granted unlimited privileges.
added: "dc=BEAVER,dc=local" (00000001)
<= str2entry: str2ad(Password): attribute type undefined
slapadd: could not parse entry (line=7)
_#########             49.35% eta   none elapsed            none spd  49.6 k/s
Closing DB...

I know its referencing line 7 just not sure if its on the init.ldif or the slapd.conf 
Let me know your thoughts when you get a chance I really appreciate all the help my friend.

It is reference the init.ldif file.  There are 6 places where you need to replace the dc=example,dc=local with your dc=BEAVER,dc=local.  Plus on the 12th line you need to copy and paste in your hashed password from slapd.conf.

Out of curiosity, what ended up being the solution to the previous problem?

---

### Post by cbhr4u on 2009-12-14
> **abishur said:**
> It is reference the init.ldif file.  There are 6 places where you need to replace the dc=example,dc=local with your dc=BEAVER,dc=local.  Plus on the 12th line you need to copy and paste in your hashed password from slapd.conf.

Out of curiosity, what ended up being the solution to the previous problem?

Doh, I forgot you should always say what it is you did to solve your problems!!! Rookie mistakes. From re-reading the [evayroberto]("http://ubuntuforums.org/member.php?u=365626") message, the   Global Directives: needed a # in front of it, once i added that it showed me the new error. From looking at your code block for the slapd.conf, you dont have a # in fron of the Global, so i'm not sure which one is correct??

---

### Post by abishur on 2009-12-14
> **cbhr4u said:**
> Doh, I forgot you should always say what it is you did to solve your problems!!! Rookie mistakes. From re-reading the [evayroberto]("http://ubuntuforums.org/member.php?u=365626") message, the   Global Directives: needed a # in front of it, once i added that it showed me the new error. From looking at your code block for the slapd.conf, you dont have a # in fron of the Global, so i'm not sure which one is correct??

How embarrassing.  When I copied this from the file I made, it removed all my editing and made the very nicely formatted Word file into one giant line.  Though I got it back to roughly the same look now, at that spot I thought the # that was supposed to go in front of Global Directives was a part of the long #### line.

Long story short, YES there is supposed to be a pound in front of Global Directives (I've updated my original post to show this).  Thanks for pointing it out!

---

### Post by cbhr4u on 2009-12-14
> **abishur said:**
> How embarrassing.  When I copied this from the file I made, it removed all my editing and made the very nicely formatted Word file into one giant line.  Though I got it back to roughly the same look now, at that spot I thought the # that was supposed to go in front of Global Directives was a part of the long #### line.

Long story short, YES there is supposed to be a pound in front of Global Directives (I've updated my original post to show this).  Thanks for pointing it out!

No problem, now I am getting a different error when running slapadd, with no changes made to the init.ldif. 

/etc/ldap/slapd.conf: line 116: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 133: rootdn is always granted unlimited privileges.
=> bdb_tool_entry_put: id2entry_add failed: DB_KEYEXIST: Key/data pair already exists (-30995)
=> bdb_tool_entry_put: txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
slapadd: could not add entry dn="dc=BEAVER,dc=local" (line=1): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
_###                   17.80% eta   none elapsed            none spd 357.9 k/s
Closing DB...

Did slapadd work partially is that why its a different error? Is there a way to remove what was done? Sorry for any stupid questions! Thanks again for your help!

---

### Post by cbhr4u on 2009-12-14
Hey abishur,
Think I found 2 more errors in the code block, for the init.ldif, you have
dn: ou=Idmap, dc=example,dc=localobject
Class: organizationalUnit
And I think it should be 
dn: ou=Idmap, dc=example,dc=local
objectClass: organizationalUnit

Also for the slapd.conf you have 

# The maximum number of entries that is returned for a search
operationsizelimit 500 
And I think it should be 
# The maximum number of entries that is returned for a search operation
sizelimit 500 

I will let you know if i see anything else, thanks again for all your help!

---

### Post by abishur on 2009-12-14
> **cbhr4u said:**
> Hey abishur,
Think I found 2 more errors in the code block, for the init.ldif, you have
dn: ou=Idmap, dc=example,dc=localobject
Class: organizationalUnit
And I think it should be 
dn: ou=Idmap, dc=example,dc=local
objectClass: organizationalUnit

Also for the slapd.conf you have 

# The maximum number of entries that is returned for a search
operationsizelimit 500 
And I think it should be 
# The maximum number of entries that is returned for a search operation
sizelimit 500 

I will let you know if i see anything else, thanks again for all your help!

Right you are!  Thanks for the catch!  I've updated the original post.  Thanks for telling me about the typos.  Like I said, I tried to get it all looking the way I had it, but man, after a while my eyes went cross!  I'll try and go through tonight really slowly and line by line recheck all this.

I'm guessing by the way that once you caught that error that the slapadd starting working?

---

### Post by cbhr4u on 2009-12-14
> **abishur said:**
> Right you are!  Thanks for the catch!  I've updated the original post.  Thanks for telling me about the typos.  Like I said, I tried to get it all looking the way I had it, but man, after a while my eyes went cross!  I'll try and go through tonight really slowly and line by line recheck all this.

I'm guessing by the way that once you caught that error that the slapadd starting working?

Nope, still getting this error
/etc/ldap/slapd.conf: line 116: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 133: rootdn is always granted unlimited privileges.
=> bdb_tool_entry_put: id2entry_add failed: DB_KEYEXIST: Key/data pair already exists (-30995)
=> bdb_tool_entry_put: txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
slapadd: could not add entry dn="dc=BEAVER,dc=local" (line=1): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
_###                   16.58% eta   none elapsed            none spd 293.4 k/s
Closing DB...

Going to play around with it some more and see what i can come up with. If you have any ideas let me know and I will post if i come up with something

---

### Post by AlexanderDGreat on 2009-12-14
Thank you for a well-thought out answer to my question abishur. More power to your tutorials. :)

---

### Post by evlist on 2009-12-19
[QUOTE=cbhr4u]Got the line 10 problem licked but when i run the slapadd I am getting this error,

/etc/ldap/slapd.conf: line 116: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 133: rootdn is always granted unlimited privileges.
added: "dc=BEAVER,dc=local" (00000001)
<= str2entry: str2ad(Password): attribute type undefined
slapadd: could not parse entry (line=7)
_######### 49.35% eta none elapsed none spd 49.6 k/s
Closing DB...[/QUOTE]
cbhr4u, abishur,

I had the same issue (str2entry: str2ad(Password): attribute type undefined) and a quick look in the schemas seems to show that the password property of the simpleSecurityObject should be spelled userPassword...

And to answer to your question: yes, slapadd does partial imports and the database needs to be cleared before a new trial.

Hope this helps,

Eric

---

### Post by cbhr4u on 2009-12-22
> **evlist said:**
> cbhr4u, abishur,

I had the same issue (str2entry: str2ad(Password): attribute type undefined) and a quick look in the schemas seems to show that the password property of the simpleSecurityObject should be spelled userPassword...

And to answer to your question: yes, slapadd does partial imports and the database needs to be cleared before a new trial.

Hope this helps,

Eric

Hey Eric, 
Thank you so much for the help, I am a linux novice so any help is always appreciated! I will give it a try today and report back if i have any issues! Thanks again for your help!! I hope you have a great holiday season!

---

### Post by esavelson on 2009-12-22
Hi,

Thanks for the effort. I have tried twice from scratch and end with similar (if not identical) errors"
> 
esavelson@ubuntu:/$ sudo slapadd -v -l /etc/ldap/init.ldif
/etc/ldap/slapd.conf: line 117: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 134: rootdn is always granted unlimited privileges.
slapadd: dn="dc=notexample,dc=local" (line=1): (64) value of single-valued naming attribute 'dc' conflicts with value present in entry
_###                   17.85% eta   none elapsed            none spd  11.7 k/s 
[LIST=1]
[*]Can you confirm how many changes of 'example' are required in the slapd.conf file? (I suggest you include the count in the remarks of the snippets)
[*]Could you point me to where to decipher the output above? eg "line 117" "line 134" 'line=1:(64)' - so that I can better trouble shoot in the future?
[*]What does the error message actually mean?
[*]what does the output (XX% eta ,,,,) actually mean?
[*]Is there a restriction for a LAN on the number of domain components? eg would 
dc=notexample work (without the ,dc=local)...or would dc=sales,dc=notexample,dc=local as well
[/LIST]
Thank you so much.

Evan

---

### Post by mickiewisz on 2009-12-24
Hello,
I have similiar problem:

/etc/ldap/slapd.conf: line 114: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 130: rootdn is always granted unlimited privileges.
=> bdb_tool_entry_put: id2entry_add failed: DB_KEYEXIST: Key/data pair already exists (-30995)
=> bdb_tool_entry_put: txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
slapadd: could not add entry dn="dc=example,dc=local" (line=1): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
_###                   16.77% eta   none elapsed            none spd 220.7 k/s
Closing DB...

My domain is: example.local too.
I did all like in the tutorial, but it don't work for me.

Help, please...

---

### Post by tanshu on 2009-12-26
Firstly thanks abishur for the excellent guide.
Hi, I ran into all the problems listed here and finally found a solution.
1. The 17% error is because in the init.ldir first entry, the dc in the second last line also has to be changed.
2. As evlist pointed out, for admin, the 
```
Password: {SSHA}paste-here-the-results-of-slappaswd
```
should be
```
userPassword: {SSHA}paste-here-the-results-of-slappaswd
```
3. For the DB_KEYEXIST error, just
```
rm -rf /var/lib/ldap/*
```
again.  I guess when processing earlier, some entries are already put in before the error(s) and they conflict with new entrie.

Hope somebody finds these tips helpful :)

---

### Post by abishur on 2009-12-28
> **tanshu said:**
> Firstly thanks abishur for the excellent guide.
Hi, I ran into all the problems listed here and finally found a solution.
1. The 17% error is because in the init.ldir first entry, the dc in the second last line also has to be changed.
2. As evlist pointed out, for admin, the 
```
Password: {SSHA}paste-here-the-results-of-slappaswd
```should be
```
userPassword: {SSHA}paste-here-the-results-of-slappaswd
```3. For the DB_KEYEXIST error, just
```
rm -rf /var/lib/ldap/*
```again.  I guess when processing earlier, some entries are already put in before the error(s) and they conflict with new entrie.

Hope somebody finds these tips helpful :)

I'm glad you like my guide :P.  Sorry I haven't been answering problems, I've been out of town for the holidays.  Good catch on the userPassword!  I looked and sure enough, I had "user" at the end of the line above.  I have fixed the typo in the original post to ensure no one else has that problem!

---

### Post by allan_nogueira on 2010-01-10
[SIZE=1]Hello people![/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]First, I would like to thank you for the time to write this good tutorial![/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I did the configuration how it's described here and I have a problem![/SIZE]
[SIZE=1]When I try to join in the domain with a XP, the Windows show me an error like this:[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]"Multiple connections to a server by same user, using more ..." What could be wrong?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I'm using Ubuntu 9.10 and Samba 3.3.2.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Thank's[/SIZE]

---

### Post by idorulabs on 2010-01-19
I am a novice to this setup.

Installed Ubuntu 9.10 server and Kubuntu (for GUI).

Can someone please suggest the basic/sample configuration before I start implementing this tutorial-

eth - ip address
domain name
host name

Got confused with dc and dn

-

I have two ethernet cards-

one for the internet, which will power the server
one for the router which will connect local machines/clients

Thanks!

---

### Post by RomanJr on 2010-01-20
Hi..First off thanks for this great tutorial.  

Ubuntu Server 9.10 

I was working through your instructions and got all the way to samba populate section..I type in:

 sudo smbldab-populate 

and I get back this:

[QUOTE]rromanjr@ubuntu-svr:/usr/sbin$ sudo smbldap-populate
Populating LDAP directory for domain RTECH (S-1-5-21-2673721247-2330088800-401481966)
(using builtin directory structure)

entry dc=RTECH,dc=local already exist.
entry ou=Users,dc=RTECH,dc=local already exist.
entry ou=Groups,dc=RTECH,dc=local already exist.
entry ou=Computers,dc=RTECH,dc=local already exist.
entry ou=Idmap,dc=RTECH,dc=local already exist.
adding new entry: uid=root,ou=Users,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 55.
adding new entry: uid=nobody,ou=Users,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 83.
adding new entry: cn=Domain Admins,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 95.
adding new entry: cn=Domain Users,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 106.
adding new entry: cn=Domain Guests,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 117.
adding new entry: cn=Domain Computers,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 128.
adding new entry: cn=Administrators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 173.
adding new entry: cn=Account Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 195.
adding new entry: cn=Print Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 206.
adding new entry: cn=Backup Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 217.
adding new entry: cn=Replicators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 228.
entry sambaDomainName=RTECH,dc=RTECH,dc=local already exist. Updating it...
failed to modify entry: modifications require authentication at /usr/sbin/smbldap-populate line 492, <GEN1> line 236.

Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist
rromanjr@ubuntu-svr:/usr/sbin$
/QUOTE]


not sure where to go from here...I did not have any errors up till now and I am not sure how to fix the root doesn't exist.

---

### Post by cbhr4u on 2010-01-20
> **RomanJr said:**
> Hi..First off thanks for this great tutorial.  

Ubuntu Server 9.10 

I was working through your instructions and got all the way to samba populate section..I type in:

 sudo smbldab-populate 

and I get back this:

[QUOTE]rromanjr@ubuntu-svr:/usr/sbin$ sudo smbldap-populate
Populating LDAP directory for domain RTECH (S-1-5-21-2673721247-2330088800-401481966)
(using builtin directory structure)

entry dc=RTECH,dc=local already exist.
entry ou=Users,dc=RTECH,dc=local already exist.
entry ou=Groups,dc=RTECH,dc=local already exist.
entry ou=Computers,dc=RTECH,dc=local already exist.
entry ou=Idmap,dc=RTECH,dc=local already exist.
adding new entry: uid=root,ou=Users,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 55.
adding new entry: uid=nobody,ou=Users,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 83.
adding new entry: cn=Domain Admins,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 95.
adding new entry: cn=Domain Users,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 106.
adding new entry: cn=Domain Guests,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 117.
adding new entry: cn=Domain Computers,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 128.
adding new entry: cn=Administrators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 173.
adding new entry: cn=Account Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 195.
adding new entry: cn=Print Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 206.
adding new entry: cn=Backup Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 217.
adding new entry: cn=Replicators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 228.
entry sambaDomainName=RTECH,dc=RTECH,dc=local already exist. Updating it...
failed to modify entry: modifications require authentication at /usr/sbin/smbldap-populate line 492, <GEN1> line 236.

Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist
rromanjr@ubuntu-svr:/usr/sbin$
/QUOTE]


not sure where to go from here...I did not have any errors up till now and I am not sure how to fix the root doesn't exist.


I am by no means an expert when it comes to this but I had a similiar issue, make sure that when you edit the smbldap_bind.conf that you are typing in the correct password. Hope that helps.

---

### Post by RomanJr on 2010-01-20
cbhr4u-->

Thanks for the insight....That was exactly the problem... just change the slave and master pw to the one I set earlier.

---

### Post by suck-kay on 2010-01-24
> **RomanJr said:**
> Hi..First off thanks for this great tutorial.  

Ubuntu Server 9.10 

I was working through your instructions and got all the way to samba populate section..I type in:

 sudo smbldab-populate 

and I get back this:

[QUOTE]rromanjr@ubuntu-svr:/usr/sbin$ sudo smbldap-populate
Populating LDAP directory for domain RTECH (S-1-5-21-2673721247-2330088800-401481966)
(using builtin directory structure)

entry dc=RTECH,dc=local already exist.
entry ou=Users,dc=RTECH,dc=local already exist.
entry ou=Groups,dc=RTECH,dc=local already exist.
entry ou=Computers,dc=RTECH,dc=local already exist.
entry ou=Idmap,dc=RTECH,dc=local already exist.
adding new entry: uid=root,ou=Users,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 55.
adding new entry: uid=nobody,ou=Users,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 83.
adding new entry: cn=Domain Admins,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 95.
adding new entry: cn=Domain Users,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 106.
adding new entry: cn=Domain Guests,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 117.
adding new entry: cn=Domain Computers,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 128.
adding new entry: cn=Administrators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 173.
adding new entry: cn=Account Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 195.
adding new entry: cn=Print Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 206.
adding new entry: cn=Backup Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 217.
adding new entry: cn=Replicators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 228.
entry sambaDomainName=RTECH,dc=RTECH,dc=local already exist. Updating it...
failed to modify entry: modifications require authentication at /usr/sbin/smbldap-populate line 492, <GEN1> line 236.

Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist
rromanjr@ubuntu-svr:/usr/sbin$
/QUOTE]


not sure where to go from here...I did not have any errors up till now and I am not sure how to fix the root doesn't exist.

i still have this problem ..  
i had edit may smbldap_bind.conf 

and all are the same password i used from the begining . . 

i have problem when use this command 
net getlocalsid 
it result 
can`t fetch domain sid for dc01-ubuntu 

but i force it by using net setlocalsid 

its wrong or not ?

pliss help me.

---

### Post by makak06 on 2010-01-26
Hi everyone, 

First of all, will you excuse my english because I'm french
So I have read this "howto" and I have some questions :

When I execute 
> 
[FONT=Verdana][SIZE=2]slapadd -v -l /etc/ldap/init.ldif
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
I have this :
> agnes@old:~$ sudo slapadd -v -l /etc/ldap/init.ldif
/etc/ldap/slapd.conf: line 116: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 133: rootdn is always granted unlimited privileges.
added: "dc=example,dc=local" (00000001)
added: "cn=admin,dc=example,dc=local" (00000002)
added: "ou=Users,dc=example,dc=local" (00000003)
added: "ou=Groups,dc=example,dc=local" (00000004)
added: "ou=Computers,dc=example,dc=local" (00000005)
added: "ou=Idmap,dc=example,dc=local" (00000006)
_#################### 100.00% eta   none elapsed            none fast!         
Closing DB...
I would like to know if the two first line are an errors ? or just an information ?

And my second question :
In the smb.conf, i don't know what to put in this ligne : 
> [global]

    # Domain name ..        
    workgroup = ???
I can use "example" or i have to put "domaine.local" (because I keep this name) ? I don't care the name, I just would like to know if everything is ok, and then I could choose a good name for my LDAP server

And there :
> # This must match init.ldif ..        
    ldap suffix = dc=example,dc=com
Does I have to put ?
> # This must match init.ldif ..        
    ldap suffix = dc=example,dc=**local**I don't understand the difference between [/SIZE][/FONT][FONT=Verdana][SIZE=2]c=example,dc=local and [/SIZE][/FONT][FONT=Verdana][SIZE=2]c=example,dc=com[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
Thanks a lot for your help !
[/SIZE][/FONT]

---

### Post by suck-kay on 2010-01-26
> **makak06 said:**
> Hi everyone, 

First of all, will you excuse my english because I'm french
So I have read this "howto" and I have some questions :

When I execute 
[FONT=Verdana][SIZE=2]
I have this :
I would like to know if the two first line are an errors ? or just an information ?

And my second question :
In the smb.conf, i don't know what to put in this ligne : 
I can use "example" or i have to put "domaine.local" (because I keep this name) ? I don't care the name, I just would like to know if everything is ok, and then I could choose a good name for my LDAP server

And there :
Does I have to put ?
I don't understand the difference between [/SIZE][/FONT][FONT=Verdana][SIZE=2]c=example,dc=local and [/SIZE][/FONT][FONT=Verdana][SIZE=2]c=example,dc=com[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
Thanks a lot for your help !
[/SIZE][/FONT]

i think you are gonna answer my question 

its ok 

my i explain this ? 

first i have terible english too 
couse i`m from indonesia 

when you using commnand 

slapadd 

this command wil initial your ldap configure init.ldif


like a ldap dn, dc, object, and else 

next ini smb.conf 

domain name

its belong to your domain name. 
if you use example form the begining 
and make it example to the end 

take a look at whole configuration 
when you change it change it 
change it all such as example to domaine ( domain name )


last..


com or local ... 

i dont about this . 


but for make it sure 

i never see a domain using local 

[http://example.local](http://example.local)




if you know how to resolve my problem

i`ll say thanks a lot 

thank you

---

### Post by makak06 on 2010-01-28
Hi, 

In fact, i have change the "com" in "local" and it's works better ! Everything is okay now
It's not important if it's "local" or "com" it's just a name !

---

### Post by fbifido on 2010-01-29
Updated script to install samba pdc with ldap backend on ubuntu 9.10

#!/bin/bash         
# verion 2.1a
# from [http://ubuntuforums.org/showpost.php?p=7921519&postcount=24](http://ubuntuforums.org/showpost.php?p=7921519&postcount=24)

clear
echo " "
echo "Must enter: sudo su before running this script"
echo "continue?:"
read continue
if [ $continue != "y" ]
     then exit 0
fi

clear

export LdapHome="/ldaphome"
export BackupDIR="/root/.ldapsamba"
export ServerIP="10.0.2.2"
export ServerDNS="10.0.2.1"
export IPmask="255.255.255.0"
export IPwork="10.0.2.0"
export IPcast="10.0.2.255"
export IPway="10.0.2.1"

export MachineName="sambapc"
export DomainName="DCOA2"
export LdapDomain="dc=dcoa2,dc=com"
export ServerName="sambapc"
export Ldappasswd="dc0001"
export MailDomain="dcoa2.com"

# make a backup of all the files that will be modify
mkdir $BackupDIR
cp /etc/hosts $BackupDIR
cp /etc/resolv.conf $BackupDIR
cp /etc/network/interfaces $BackupDIR

echo " "
echo "#0---------------------------------------------------------"
echo " Configuring System"
echo " "

apt-get --yes install ssh openssh-server

echo " "
echo "#1------------------------------"
echo " Installing OpenLDAP          "
echo " "

apt-get --yes install slapd ldap-utils db4.2-util samba-doc

mkdir $LdapHome
chmod -R 777 $LdapHome

cp -ab /etc/ldap/slapd.d $BackupDIR
cp /etc/default/slapd $BackupDIR

rm -r /etc/ldap/slapd.d/
mv /etc/default/slapd /etc/default/slapd.bk

echo "
# Location of the slapd configuration to use.  If using the cn=config          
# backend to store configuration in LDIF, set this variable to the             
# directory containing the cn=config data; otherwise set it to the location    
# of your slapd.conf file.  If empty, use the compiled-in default              
# (/etc/ldap/slapd.d). 
SLAPD_CONF=/etc/ldap/slapd.conf

# System account to run the slapd server under. If empty the server
# will run as root.
SLAPD_USER=\"openldap\"

# System group to run the slapd server under. If empty the server will
# run in the primary group of its user.
SLAPD_GROUP=\"openldap\"

# Path to the pid file of the slapd server. If not set the init.d script
# will try to figure it out from $SLAPD_CONF (/etc/ldap/slapd.d by
# default)
SLAPD_PIDFILE=

# slapd normally serves ldap only on all TCP-ports 389. slapd can also
# service requests on TCP-port 636 (ldaps) and requests via unix
# sockets.
# Example usage:
# SLAPD_SERVICES=\"ldap://127.0.0.1:389/ ldaps:/// ldapi:///\"
SLAPD_SERVICES=\"ldap:/// ldapi:///\"

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
SLAPD_OPTIONS=\"\"
" > /etc/default/slapd

echo " "
echo "#2-----------------------------------------"
echo " Installing Samba documentation containing the Samba schema. Extract samba.schema and copy to the required system area for OpenLDAP."
echo " "

gunzip /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz
cp -v /usr/share/doc/samba-doc/examples/LDAP/samba.schema /etc/ldap/schema

echo " "
echo "#3-----------------------------------------"
echo " Decide on an LDAP admin password and generate a SSHA hash key for it."
echo " "

export slappass=`slappasswd -s $Ldappasswd`

echo " "
echo "#4-------------------------------------------"
echo " Create an init.ldif file. Name the 4 OUs Users, Groups, Computers and Idmap for use with smbldap-tools. "
echo " "

echo "
dn: $LdapDomain
objectClass: dcObject
objectClass: organizationalUnit
dc: $DomainName
ou: $DomainName

dn: cn=admin,$LdapDomain
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: $slappass 

dn: ou=Users,$LdapDomain
objectClass: organizationalUnit
ou: Users

dn: ou=Groups,$LdapDomain
objectClass: organizationalUnit
ou: Groups

dn: ou=Computers,$LdapDomain
objectClass: organizationalUnit
ou: Computers

dn: ou=Idmap,$LdapDomain
objectClass: organizationalUnit
ou: Idmap
" > /etc/ldap/init.ldif

echo "
# Remember to replace suffix \"$LdapDomain\" with your domain name
# Change the rootpw entry with the results from slappaswd (Must match the same you pasted on init.ldif)

# /etc/ldap/slapd.conf
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
include         /etc/ldap/schema/misc.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

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
database        bdb

# The base of your directory in database #1
suffix          \"$LdapDomain\"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          \"cn=admin,$LdapDomain\"
rootpw $slappass

# Where the database file are physically stored for database #1
directory       \"/var/lib/ldap\"

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
#index           objectClass eq, pres
index ou,cn,sn,mail,givenname           eq,pres,sub
index uidNumber,gidNumber,memberUid     eq,pres
index loginShell                        eq,pres
index uniqueMember                      eq,pres
index uid                               pres,sub,eq
index displayName                       pres,sub,eq
index sambaSID                          eq
index sambaPrimaryGroupSID              eq
index sambaDomainName                   eq
index default                           sub
#index   uid         pres,eq,sub

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
        by dn=\"cn=admin,$LdapDomain\" write
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
access to dn.base=\"\" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn=\"cn=admin,$LdapDomain\" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=\".*,ou=Roaming,o=morsnet\"
#        by dn=\"cn=admin,$LdapDomain\" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         \"dc=debian,dc=org\"
" > /etc/ldap/slapd.conf

echo " "
echo "#5---------------------------------"
echo " Initialising OpenLDAP database .. "
echo " "

/etc/init.d/slapd stop
rm -rf /var/lib/ldap/*
slapadd -v -l /etc/ldap/init.ldif
chown -R openldap:openldap /var/lib/ldap
/etc/init.d/slapd start

ldapsearch -xLLL -b "$LdapDomain"


echo " "
echo "#6---------------------------"
echo " Install and Configure Samba"
echo " "

apt-get --yes install samba libpam-smbpass smbldap-tools 

cp /etc/samba/smb.conf $BackupDIR

echo " "
echo "#7-----------------------------------------------"
echo " Create Samba folders that have not been automatically created .."
echo " "

mkdir -v /var/lib/samba/profiles
chmod 777 /var/lib/samba/profiles
mkdir -v -p /var/lib/samba/netlogon

echo " "
echo "#8------------------------------------------------"
echo " Editing /etc/samba/smb.conf "
echo " "

mv /etc/samba/smb.conf /etc/samba/smb.conf.bk

echo "
[global]
        dos charset = 850
        unix charset = UTF8
        workgroup = $DomainName
        server string = $DomainName Samba Server
        netbios name = $ServerName
        domain logons = Yes
        domain master = Yes
        local master = yes
        preferred master = yes
        wins support = true

        obey pam restrictions = Yes
        dns proxy = No
        os level = 35
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        pam password change = Yes

        # Allows users on WinXP PCs to change their password when they press Ctrl-Alt-Del
        unix password sync = no
        ldap passwd sync = yes

        # Printing from PCs will go via CUPS ..
        load printers = yes
        printing = cups
        printcap name = cups

        # Use LDAP for Samba user accounts and groups ..
        passdb backend = ldapsam:ldap://localhost

        # This must match init.ldif ..
        ldap suffix = $LdapDomain
        ldap admin dn = cn=admin,$LdapDomain

        ldap machine suffix = ou=Computers
        ldap user suffix = ou=Users
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap

        ldap ssl = no

        # Scripts for Samba to use if it creates users, groups, etc.
        add user script = /usr/sbin/smbldap-useradd -m '%u'
        delete user script = /usr/sbin/smbldap-userdel %u
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

        # Script that Samba users when a PC joins the domain ..
        # (when changing 'Computer Properties' on the PC)
        add machine script = /usr/sbin/smbldap-useradd -w '%u'

        # Values used when a new user is created ..
        # (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)
        logon drive = h:
        logon home = \\\\$ServerName\\PROFILES\\%U
        logon path = \\\\$ServerName\\PROFILES\\%U
        logon script = login.bat

        winbind use default domain = Yes
        inherit permissions = Yes
        inherit acls = Yes
        inherit owner = Yes
        case sensitive = No
        hide files = /desktop.ini/ntuser.ini/NTUSER.*/
        msdfs root = Yes

        # This is required for Windows XP client ..
        server signing = auto
        server schannel = Auto

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No
        create mask = 0776
        directory mask = 0776

[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        public = No
        writeable = No
        admin users = root
        guest ok = Yes
        browseable = No

[Profiles]
        comment = Roaming Profile Share
        # would probably change this to elsewhere in a production system ..
        path = /var/lib/samba/profiles
        read only = No
        writable = yes
        profile acls = Yes
        browsable = No
        create mask = 0600
        directory mask = 0700
        inherit permissions = No
        inherit acls = No
        inherit owner = No
        csc policy = disable

[printers]
        comment = All Printers
        path = /var/spool/samba
        use client driver = Yes
        create mask = 0600
        guest ok = Yes
        printable = Yes
        browseable = No
        public = yes
        writable = yes
        admin users = root
        write list = root

[print$]
        comment = Printer Drivers Share
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        admin users = root
" > /etc/samba/smb.conf


echo " "
echo "#9----------------------------------------------"
echo " Write password for the LDAP admin account (eg. cn=admin,$LdapDomain) into /etc/samba/secrets.tdb"
echo " "

smbpasswd -w $Ldappasswd

echo " "
echo "#10---------------------------------------------"
echo "  Restart Samba .."
echo " "

/etc/init.d/samba restart

echo " "
echo "#11----------------------------------------------"
echo "  Use the SMB client to check that the Samba server is responding correctly."
echo " "
 
# smbclient -L localhost -U anonymous%


echo " "
echo "#12----------------------------------------------"
echo " Installing and extract the configure.pl script."
echo " "

#gunzip /usr/share/doc/smbldap-tools/configure.pl.gz
#chmod +x /usr/share/doc/smbldap-tools/configure.pl

echo " "
echo "#13---------------------------------------------"
echo " Before configuring smbldap-tools, check that Samba is running and the Windows domain SID can be retrieved."
echo " "


#ps -e | grep -i "smb"
#net getlocalsid


echo " "
echo "#---------------------------------------------"
echo " Getting smbldap-tools ready"
echo " "

cd /usr/share/doc/smbldap-tools/examples/

cp smbldap_bind.conf /etc/smbldap-tools/
cp smbldap.conf.gz /etc/smbldap-tools/
gzip -d /etc/smbldap-tools/smbldap.conf.gz

cd /etc/smbldap-tools/

cp /etc/smbldap-tools/smbldap.conf $BackupDIR
mv smbldap.conf smbldap.conf.bk

export LocalSID=`net getlocalsid | awk '{print $6}'`

echo "
# \$Source: $
# \$Id: smbldap.conf,v 1.18 2005/05/27 14:28:47 jtournier Exp $
#
# smbldap-tools.conf : Q & D configuration file for smbldap-tools

#  This code was developped by IDEALX ([http://IDEALX.org/](http://IDEALX.org/)) and
#  contributors (their names can be found in the CONTRIBUTORS file).
#
#                 Copyright (C) 2001-2002 IDEALX
#
#  This program is free software; you can redistribute it and/or
#  modify it under the terms of the GNU General Public License
#  as published by the Free Software Foundation; either version 2
#  of the License, or (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program; if not, write to the Free Software
#  Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307,
#  USA.

#  Purpose :
#       . be the configuration file for all smbldap-tools scripts

##############################################################################
#
# General Configuration
#
##############################################################################

# Put your own SID. To obtain this number do: \"net getlocalsid\".
# If not defined, parameter is taking from "net getlocalsid" return
SID=\"$LocalSID\"

# Domain name the Samba server is in charged.
# If not defined, parameter is taking from smb.conf configuration file
# Ex: sambaDomain=\"IDEALX-NT\"
sambaDomain=\"$DomainName\"

##############################################################################
#
# LDAP Configuration
#
##############################################################################

# Notes: to use to dual ldap servers backend for Samba, you must patch
# Samba with the dual-head patch from IDEALX. If not using this patch
# just use the same server for slaveLDAP and masterLDAP.
# Those two servers declarations can also be used when you have 
# . one master LDAP server where all writing operations must be done
# . one slave LDAP server where all reading operations must be done
#   (typically a replication directory)

# Slave LDAP server
# Ex: slaveLDAP=127.0.0.1
# If not defined, parameter is set to \"127.0.0.1\"
slaveLDAP=\"127.0.0.1\"

# Slave LDAP port
# If not defined, parameter is set to \"389\"
slavePort=\"389\"

# Master LDAP server: needed for write operations
# Ex: masterLDAP=127.0.0.1
# If not defined, parameter is set to \"127.0.0.1\"
masterLDAP=\"127.0.0.1\"

# Master LDAP port
# If not defined, parameter is set to \"389\"
masterPort=\"389\"

# Use TLS for LDAP
# If set to 1, this option will use start_tls for connection
# (you should also used the port 389)
# If not defined, parameter is set to \"1\"
ldapTLS=\"0\"

# How to verify the server's certificate (none, optional or require)
# see \"man Net::LDAP\" in start_tls section for more details
verify=\"require\"

# CA certificate
# see \"man Net::LDAP\" in start_tls section for more details
cafile=\"/etc/smbldap-tools/ca.pem\"

# certificate to use to connect to the ldap server
# see \"man Net::LDAP\" in start_tls section for more details
clientcert=\"/etc/smbldap-tools/smbldap-tools.pem\"

# key certificate to use to connect to the ldap server
# see \"man Net::LDAP\" in start_tls section for more details
clientkey=\"/etc/smbldap-tools/smbldap-tools.key\"

# LDAP Suffix
# Ex: suffix=dc=IDEALX,dc=ORG
suffix=\"$LdapDomain\"

# Where are stored Users
# Ex: usersdn=\"ou=Users,dc=IDEALX,dc=ORG\"
# Warning: if 'suffix' is not set here, you must set the full dn for usersdn
usersdn=\"ou=Users,\${suffix}\"

# Where are stored Computers
# Ex: computersdn=\"ou=Computers,dc=IDEALX,dc=ORG\"
# Warning: if 'suffix' is not set here, you must set the full dn for computersdn
computersdn=\"ou=Computers,\${suffix}\"

# Where are stored Groups
# Ex: groupsdn="ou=Groups,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for groupsdn
groupsdn=\"ou=Groups,\${suffix}\"

# Where are stored Idmap entries (used if samba is a domain member server)
# Ex: groupsdn="ou=Idmap,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for idmapdn
idmapdn=\"ou=Idmap,\${suffix}\"

# Where to store next uidNumber and gidNumber available for new users and groups
# If not defined, entries are stored in sambaDomainName object.
# Ex: sambaUnixIdPooldn=\"sambaDomainName=\${sambaDomain},\${suffix}\"
# Ex: sambaUnixIdPooldn=\"cn=NextFreeUnixId,\${suffix}\"
sambaUnixIdPooldn=\"sambaDomainName=$DomainName,\${suffix}\"

# Default scope Used
scope=\"sub\"

# Unix password encryption (CRYPT, MD5, SMD5, SSHA, SHA, CLEARTEXT)
hash_encrypt=\"SSHA\"

# if hash_encrypt is set to CRYPT, you may set a salt format.
# default is \"%s\", but many systems will generate MD5 hashed
# passwords if you use \"$1$%.8s\". This parameter is optional!
crypt_salt_format=\"%s\"

##############################################################################
# 
# Unix Accounts Configuration
# 
##############################################################################

# Login defs
# Default Login Shell
# Ex: userLoginShell=\"/bin/bash\"
userLoginShell=\"/bin/bash\"

# Home directory
# Ex: userHome=\"/home/%U\"
userHome=\"$LdapHome/%U\"

# Default mode used for user homeDirectory
userHomeDirectoryMode=\"700\"

# Gecos
userGecos=\"System User\"

# Default User (POSIX and Samba) GID
defaultUserGid=\"513\"

# Default Computer (Samba) GID
defaultComputerGid=\"515\"

# Skel dir
skeletonDir=\"/etc/skel\"

# Default password validation time (time in days) Comment the next line if
# you don't want password to be enable for defaultMaxPasswordAge days (be
# careful to the sambaPwdMustChange attribute's value)
defaultMaxPasswordAge=\"45\"

##############################################################################
#
# SAMBA Configuration
#
##############################################################################

# The UNC path to home drives location (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon home'
# directive and/or disable roaming profiles
# Ex: userSmbHome=\"\\$ServerName\%U\"
userSmbHome=

# The UNC path to profiles locations (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon path'
# directive and/or disable roaming profiles
# Ex: userProfile=\"\\$ServerName\profiles\%U\"
userProfile=

# The default Home Drive Letter mapping
# (will be automatically mapped at logon time if home directory exist)
# Ex: userHomeDrive=\"H:\"
userHomeDrive=

# The default user netlogon script name (%U username substitution)
# if not used, will be automatically username.cmd
# make sure script file is edited under dos
# Ex: userScript=\"startup.cmd\" # make sure script file is edited under dos
userScript=

# Domain appended to the users \"mail\"-attribute
# when smbldap-useradd -M is used
# Ex: mailDomain=\"idealx.com\"
mailDomain=\"$MailDomain\"

##############################################################################
#
# SMBLDAP-TOOLS Configuration (default are ok for a RedHat)
#
##############################################################################

# Allows not to use smbpasswd (if with_smbpasswd == 0 in smbldap_conf.pm) but
# prefer Crypt::SmbHash library
with_smbpasswd=\"0\"
smbpasswd=\"/usr/bin/smbpasswd\"

# Allows not to use slappasswd (if with_slappasswd == 0 in smbldap_conf.pm)
# but prefer Crypt:: libraries
with_slappasswd=\"0\"
slappasswd=\"/usr/sbin/slappasswd\"

# comment out the following line to get rid of the default banner
# no_banner=\"1\"
" > /etc/smbldap-tools/smbldap.conf

cp /etc/smbldap-tools/smbldap_bind.conf $BackupDIR
mv smbldap_bind.conf smbldap_bind.conf.bk

echo "
############################
# Credential Configuration #
############################
# Notes: you can specify two differents configuration if you use a
# master ldap for writing access and a slave ldap server for reading access
# By default, we will use the same DN (so it will work for standard Samba
# release)
slaveDN=\"cn=admin,$LdapDomain\"
slavePw=\"$Ldappasswd\"
masterDN=\"cn=admin,$LdapDomain\"
masterPw=\"$Ldappasswd\"
" > /etc/smbldap-tools/smbldap_bind.conf

chmod 0644 /etc/smbldap-tools/smbldap.conf
chmod 0600 /etc/smbldap-tools/smbldap_bind.conf 

echo " "
echo "#14-----------------------------------------------------"
echo "  Populate the LDAP database with essential Samba entries. This includes the creation of standard groups, such as Administrators and Domain Users."
echo " "

# /usr/share/doc/smbldap-tools/configure.pl


smbldap-populate

echo " "
echo "#15------------------------------------------------------"
echo " Following this, stop the LDAP server, run slapindex, and restart the LDAP server."
echo " "

/etc/init.d/slapd stop
slapindex
chown openldap:openldap /var/lib/ldap/* 
/etc/init.d/slapd start

echo " "
echo "#16----------------------------------------------------"
echo "    Add Test Account"
echo " "

echo "Adding user ryan"
smbldap-useradd -a -m -P ryan

echo " "
echo "#17--------------------------------------------------"
echo " Adding ryan and root as Administrators"
echo " "

/usr/sbin/smbldap-groupmod -m 'ryan' 'Administrators'
/usr/sbin/smbldap-groupmod -m 'root' 'Administrators'

echo " "
echo "#18--------------------------------------------------"
echo "  Check to see the Administrators account"
echo " "

smbldap-groupshow Administrators
sleep 10
clear

echo " "
echo "#19-------------------------------------------------"
echo "    Add LDAP Authentication on the Server"
echo " "
echo " "
echo "    Answer with the following(write down if necessary): "
echo " "
echo "LDAP server Uniform Resource Identifier:	ldap://127.0.0.1"
echo "search base:    				$LdapDomain"
echo "LDAP version to use:   			3"
echo "Make local root Database admin:		Yes"
echo "Does the LDAP database require login?:	No"
echo "LDAP account for root:			cn=admin,$LdapDomain"
echo "LDAP root account password: #<enter the LDAP admin password> $Ldappasswd"
echo " "
echo " "
echo "Press Enter to continue."
read lvar

apt-get --yes install ldap-auth-client

cp /etc/ldap.conf $BackupDIR
mv /etc/ldap.conf /etc/ldap.conf.bk

echo "
###DEBCONF###
##
## Configuration of this file will be managed by debconf as long as the
## first line of the file says '###DEBCONF###'
##
## You should use dpkg-reconfigure to configure this file via debconf
##

#
# @(#)\$Id: ldap.conf,v 1.38 2006/05/15 08:13:31 lukeh Exp $
#
# This is the configuration file for the LDAP nameservice
# switch library and the LDAP PAM module.
#
# PADL Software
# [http://www.padl.com](http://www.padl.com)
#

# Your LDAP server. Must be resolvable without using LDAP.
# Multiple hosts may be specified, each separated by a 
# space. How long nss_ldap takes to failover depends on
# whether your LDAP client library supports configurable
# network or connect timeouts (see bind_timelimit).
host 127.0.0.1

# The distinguished name of the search base.
base $LdapDomain

# Another way to specify your LDAP server is to provide an
uri ldap://127.0.0.1
# Unix Domain Sockets to connect to a local LDAP Server.
#uri ldap://127.0.0.1/
#uri ldaps://127.0.0.1/   
#uri ldapi://%2fvar%2frun%2fldapi_sock/
# Note: %2f encodes the '/' used as directory separator

# The LDAP version to use (defaults to 3
# if supported by client library)
ldap_version 3

# The distinguished name to bind to the server with.
# Optional: default is to bind anonymously.
#binddn cn=proxyuser,$LdapDomain

# The credentials to bind with. 
# Optional: default is no credential.
#bindpw secret

# The distinguished name to bind to the server with
# if the effective user ID is root. Password is
# stored in /etc/ldap.secret (mode 600)
rootbinddn cn=admin,$LdapDomain

# The port.
# Optional: default is 389.
#port 389

# The search scope.
#scope sub
#scope one
#scope base

# Search timelimit
#timelimit 30

# Bind/connect timelimit
#bind_timelimit 30

# Reconnect policy: hard (default) will retry connecting to
# the software with exponential backoff, soft will fail
# immediately.
bind_policy soft

# Idle timelimit; client will close connections
# (nss_ldap only) if the server has not been contacted
# for the number of seconds specified below.
#idle_timelimit 3600

# Filter to AND with uid=%s
#pam_filter objectclass=account

# The user ID attribute (defaults to uid)
#pam_login_attribute uid

# Search the root DSE for the password policy (works
# with Netscape Directory Server)
#pam_lookup_policy yes

# Check the 'host' attribute for access control
# Default is no; if set to yes, and user has no
# value for the host attribute, and pam_ldap is
# configured for account management (authorization)
# then the user will not be allowed to login.
#pam_check_host_attr yes

# Check the 'authorizedService' attribute for access
# control
# Default is no; if set to yes, and the user has no
# value for the authorizedService attribute, and
# pam_ldap is configured for account management
# (authorization) then the user will not be allowed
# to login.
#pam_check_service_attr yes

# Group to enforce membership of
#pam_groupdn cn=PAM,ou=Groups,$LdapDomain

# Group member attribute
#pam_member_attribute uniquemember

# Specify a minium or maximum UID number allowed
#pam_min_uid 0
#pam_max_uid 0

# Template login attribute, default template user
# (can be overriden by value of former attribute
# in user's entry)
#pam_login_attribute userPrincipalName
#pam_template_login_attribute uid
#pam_template_login nobody

# HEADS UP: the pam_crypt, pam_nds_passwd,
# and pam_ad_passwd options are no
# longer supported.
#
# Do not hash the password at all; presume
# the directory server will do it, if
# necessary. This is the default.
pam_password md5

# Hash password locally; required for University of
# Michigan LDAP server, and works with Netscape
# Directory Server if you're using the UNIX-Crypt
# hash mechanism and not using the NT Synchronization
# service. 
#pam_password crypt

# Remove old password first, then update in
# cleartext. Necessary for use with Novell
# Directory Services (NDS)
#pam_password clear_remove_old
#pam_password nds

# RACF is an alias for the above. For use with
# IBM RACF
#pam_password racf

# Update Active Directory password, by
# creating Unicode password and updating
# unicodePwd attribute.
#pam_password ad

# Use the OpenLDAP password change
# extended operation to update the password.
#pam_password exop

# Redirect users to a URL or somesuch on password
# changes.
#pam_password_prohibit_message Please visit [http://internal](http://internal) to change your password.

# RFC2307bis naming contexts
# Syntax:
# nss_base_XXX	       base?scope?filter
# where scope is {base,one,sub}
# and filter is a filter to be &'d with the
# default filter.
# You can omit the suffix eg:
# nss_base_passwd	ou=People,
# to append the default base DN but this
# may incur a small performance impact.
#nss_base_passwd	ou=People,$LdapDomain?one
#nss_base_shadow	ou=People,$LdapDomain?one
#nss_base_group		ou=Group,$LdapDomain?one
#nss_base_hosts		ou=Hosts,$LdapDomain?one
#nss_base_services	ou=Services,$LdapDomain?one
#nss_base_networks	ou=Networks,$LdapDomain?one
#nss_base_protocols	ou=Protocols,$LdapDomain?one
#nss_base_rpc		ou=Rpc,$LdapDomain?one
#nss_base_ethers	ou=Ethers,$LdapDomain?one
#nss_base_netmasks	ou=Networks,$LdapDomain?ne
#nss_base_bootparams	ou=Ethers,$LdapDomain?one
#nss_base_aliases	ou=Aliases,$LdapDomain?one
#nss_base_netgroup	ou=Netgroup,$LdapDomain?one

# attribute/objectclass mapping
# Syntax:
#nss_map_attribute	rfc2307attribute	mapped_attribute
#nss_map_objectclass	rfc2307objectclass	mapped_objectclass

# configure --enable-nds is no longer supported.
# NDS mappings
#nss_map_attribute uniqueMember member

# Services for UNIX 3.5 mappings
#nss_map_objectclass posixAccount User
#nss_map_objectclass shadowAccount User
#nss_map_attribute uid msSFU30Name
#nss_map_attribute uniqueMember msSFU30PosixMember
#nss_map_attribute userPassword msSFU30Password
#nss_map_attribute homeDirectory msSFU30HomeDirectory
#nss_map_attribute homeDirectory msSFUHomeDirectory
#nss_map_objectclass posixGroup Group
#pam_login_attribute msSFU30Name
#pam_filter objectclass=User
#pam_password ad

# configure --enable-mssfu-schema is no longer supported.
# Services for UNIX 2.0 mappings
#nss_map_objectclass posixAccount User
#nss_map_objectclass shadowAccount user
#nss_map_attribute uid msSFUName
#nss_map_attribute uniqueMember posixMember
#nss_map_attribute userPassword msSFUPassword
#nss_map_attribute homeDirectory msSFUHomeDirectory
#nss_map_attribute shadowLastChange pwdLastSet
#nss_map_objectclass posixGroup Group
#nss_map_attribute cn msSFUName
#pam_login_attribute msSFUName
#pam_filter objectclass=User
#pam_password ad

# RFC 2307 (AD) mappings
#nss_map_objectclass posixAccount user
#nss_map_objectclass shadowAccount user
#nss_map_attribute uid sAMAccountName
#nss_map_attribute homeDirectory unixHomeDirectory
#nss_map_attribute shadowLastChange pwdLastSet
#nss_map_objectclass posixGroup group
#nss_map_attribute uniqueMember member
#pam_login_attribute sAMAccountName
#pam_filter objectclass=User
#pam_password ad

# configure --enable-authpassword is no longer supported
# AuthPassword mappings
#nss_map_attribute userPassword authPassword

# AIX SecureWay mappings
#nss_map_objectclass posixAccount aixAccount
#nss_base_passwd ou=aixaccount,?one
#nss_map_attribute uid userName
#nss_map_attribute gidNumber gid
#nss_map_attribute uidNumber uid
#nss_map_attribute userPassword passwordChar
#nss_map_objectclass posixGroup aixAccessGroup
#nss_base_group ou=aixgroup,?one
#nss_map_attribute cn groupName
#nss_map_attribute uniqueMember member
#pam_login_attribute userName
#pam_filter objectclass=aixAccount
#pam_password clear

# Netscape SDK LDAPS
#ssl on

# Netscape SDK SSL options
#sslpath /etc/ssl/certs

# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
#ssl start_tls
#ssl on

# OpenLDAP SSL options
# Require and verify server certificate (yes/no)
# Default is to use libldap's default behavior, which can be configured in
# /etc/openldap/ldap.conf using the TLS_REQCERT setting.  The default for
# OpenLDAP 2.0 and earlier is \"no\", for 2.1 and later is \"yes\".
#tls_checkpeer yes

# CA certificates for server certificate verification
# At least one of these are required if tls_checkpeer is \"yes\"
#tls_cacertfile /etc/ssl/ca.cert
#tls_cacertdir /etc/ssl/certs

# Seed the PRNG if /dev/urandom is not provided
#tls_randfile /var/run/egd-pool

# SSL cipher suite
# See man ciphers for syntax
#tls_ciphers TLSv1

# Client certificate and key
# Use these, if your server requires client authentication.
#tls_cert
#tls_key

# Disable SASL security layers. This is needed for AD.
#sasl_secprops maxssf=0

# Override the default Kerberos ticket cache location.
#krb5_ccname FILE:/etc/.ldapcache

# SASL mechanism for PAM authentication - use is experimental
# at present and does not support password policy control
#pam_sasl_mech DIGEST-MD5
nss_initgroups_ignoreusers backup,bin,daemon,games,gnats,irc,landscape,libuuid,list,lp,mail,man,news,openldap,proxy,root,sshd,sync,sys,syslog,uucp,www-data
" > /etc/ldap.conf

cp /etc/ldap.conf /etc/ldap/ldap.conf 

echo "
[open_ldap]
nss_passwd=passwd:      compat ldap
nss_group=group:        compat ldap
nss_shadow=shadow:      compat ldap
nss_netgroup=netgroup:  nis
pam_auth=auth           required        pam_env.so 
        auth            sufficient      pam_unix.so likeauth nullok 
        auth            sufficient      pam_ldap.so use_first_pass 
        auth            required        pam_deny.so
pam_account=account     sufficient      pam_unix.so 
       account          sufficient      pam_ldap.so 
       account          required        pam_deny.so
pam_password=password   sufficient      pam_unix.so nullok md5 shadow use_authtok 
        password        sufficient      pam_ldap.so use_first_pass 
        password        required        pam_deny.so
pam_session=session     required        pam_limits.so 
        session         required        pam_mkhomedir.so skel=/etc/skel/ umask=0077 
        session         required        pam_unix.so 
        session         optional        pam_ldap.so
" > /etc/auth-client-config/profile.d/open_ldap

auth-client-config -a -p open_ldap

echo " "
echo "If you receive the following error:"
echo "  Error in updating the file: 'nss_netgroup' not found"
echo "Then open your open_ldap file "
echo "	vi /etc/auth-client-config/profile.d/open_ldap"
echo "Delete the line that says \"nss_netgroup=netgroup: nis\" "
echo "And replace it with nss_netgroup=netgroup: compat ldap"
echo "Finally, run the auth-client-config -a -p open_ldap"
echo " "

getent group

#RESTART
echo "press any key to restart now"
read restartvar
shutdown now -r

---

### Post by fbifido on 2010-01-30
[COLOR="Red"]running:[/COLOR]

root@ubuntu:/etc/smbldap-tools# smbldap-populate
Populating LDAP directory for domain DCOA3 (S-1-5-21-2854776428-2897039083-2249456723)
(using builtin directory structure)

entry dc=dcoa3,dc=com already exist.
entry ou=Users,dc=dcoa3,dc=com already exist.
entry ou=Groups,dc=dcoa3,dc=com already exist.
entry ou=Computers,dc=dcoa3,dc=com already exist.
entry ou=Idmap,dc=dcoa3,dc=com already exist.
entry uid=root,ou=Users,dc=dcoa3,dc=com already exist.
entry uid=nobody,ou=Users,dc=dcoa3,dc=com already exist.
entry cn=Domain Admins,ou=Groups,dc=dcoa3,dc=com already exist.
entry cn=Domain Users,ou=Groups,dc=dcoa3,dc=com already exist.
entry cn=Domain Guests,ou=Groups,dc=dcoa3,dc=com already exist.
entry cn=Domain Computers,ou=Groups,dc=dcoa3,dc=com already exist.
entry cn=Administrators,ou=Groups,dc=dcoa3,dc=com already exist.
entry cn=Account Operators,ou=Groups,dc=dcoa3,dc=com already exist.
entry cn=Print Operators,ou=Groups,dc=dcoa3,dc=com already exist.
entry cn=Backup Operators,ou=Groups,dc=dcoa3,dc=com already exist.
entry cn=Replicators,ou=Groups,dc=dcoa3,dc=com already exist.
entry sambaDomainName=DCOA3,dc=dcoa3,dc=com already exist. Updating it...

Changing UNIX and samba passwords for root
New password:   qwerty
Retype new password: qwerty

[COLOR="Red"]gives me:[/COLOR]

Use of uninitialized value $_[1] in concatenation (.) or string at /usr/sbin/smbldap-passwd line 304, <STDIN> line 2.
I cannot generate the proper hash!

---

### Post by makak06 on 2010-02-01
Hi, 

With this "howto" is it possible to connect an ubuntu computer to my server ?
Because i can't

Someone can help me plz ?

I have to set up special things on my server ? on my client i just install "ldap-auth-client" and configure the pam.d file but it's doesn't work...

Thx for your help !

---

### Post by ibrahimuwc on 2010-02-04
I have followed your tutorial installation successfully till the end. However, when I try to join a Windows XP machine to the domain I have created, I get an error on the xp machine saying: Bad username or password. 

I have ports 137-139 & 445 open on the Ubuntu machine via Gufw. 

Also, I have another laptop running ubuntu desktop 9.10, I can't join it to the domain either. When I use the command sudo net join -W SERVERNAME -U administator-name it returns a help menu with all the possible command options. And when I write sudo net join SERVERNAME only, it returns an error that the machine can't be joing by in stand alone mode.

Any suggestions.

Thanks

---

### Post by ibrahimuwc on 2010-02-05
I had to reformat my Ubuntu 9.10 machine, followed the tutorial and every worked great. 
 
Thanks,

---

### Post by suck-kay on 2010-02-14
hello 

i`ve done all of this .. 

and its worked .. 

but . 

where my samba ldap  turned off 

my user can stil loggin using 

how do i stop this .. 

thank for any help..

---

### Post by Overcast32 on 2010-02-18
This worked well, thanks a ton to [**ingcabral**]("http://ubuntuforums.org/member.php?u=834368") for the original thread and the [**abishur**]("http://ubuntuforums.org/member.php?u=943906") on this one, kudos guys. 

The only thing I had to do in the end was give that user permissions to the home folder. I'm going to try a few tweaks... I hope they work, but I think if I have to do this a second time, it will be much faster, I made a copy of all the config files after my edits. 

:popcorn:

Well - Oddly, last night right after joining initially it whined about loosing connection with the DC, but after I rebooted - copied profiles with a different user (copy local profile to domain profile) account in windows and re-logged into the domain, it hasn't complained one bit.

---

### Post by Overcast32 on 2010-02-18
One question though - if I want to setup H: drives in windows for the users - not profiles at all, just an H: drive mapping to /ldaphome/*username*.. what all would I need to add?

I tried this - but no luck just yet. 

Added to [B]smbldap.conf
[/B]
```

# The UNC path to home drives location (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon home'
# directive and/or disable roaming profiles
# Ex: userSmbHome="\\PDC-SMB3\%U"
userSmbHome="\\192.168.0.2\%U"

# The UNC path to profiles locations (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon path'
# directive and/or disable roaming profiles
# Ex: userProfile="\\PDC-SMB3\profiles\%U"
userProfile=

# The default Home Drive Letter mapping
# (will be automatically mapped at logon time if home directory exist)
# Ex: userHomeDrive="H:"
userHomeDrive="H:"

```

And then added to **smb.conf**
```

        logon drive = H:
        logon home = \\192.168.0.2\%u
        logon path =
        logon script = logon.cmd
```

Am I missing something?

Should I only be editing one of the two or should I be using the Debian path on any of those? (like /ldaphome/%U)

I can browse/read/create manually in the folder, so it's not permissions - I don't think, it's set to '700'

---

### Post by arylinth on 2010-02-23
I have followed your guide, but when I get to ```
  			 				 [FONT=Verdana][SIZE=2]ldapsearch   -xLLL -b  "dc=example,dc=com"[/SIZE][/FONT] 			 		 
``` I get the following output: ```
 ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1) 
```

When I do a ```
 ldapsearch -xLLL -b "dc=greenburghlibrary,dc=org" -h 127.0.0.1
``` I get ```
 dn: dc=greenburghlibrary,dc=org
objectClass: dcObject
objectClass: organizationalUnit
dc: greenburghlibrary
ou:: SECRET

dn: cn=admin,dc=greenburghlibrary,dc=org
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator

dn: ou=Users,dc=greenburghlibrary,dc=org
objectClass: organizationalUnit
ou:: VXNlcnMg

dn: ou=Groups,dc=greenburghlibrary,dc=org
objectClass: organizationalUnit
ou:: R3JvdXBzIA==

dn: ou=Computers,dc=greenburghlibrary,dc=org
objectClass: organizationalUnit
ou:: Q29tcHV0ZXJzIA==

dn: ou=Idmap,dc=greenburghlibrary,dc=org
objectClass: organizationalUnit
ou: Idmap 
```

When I get to net getlocalsid I get the following error: ```
 [2010/02/23 14:30:26,  0] lib/smbldap.c:656(smb_ldap_start_tls)
  Failed to issue the StartTLS instruction: Protocol error
[2010/02/23 14:30:27,  0] lib/smbldap.c:656(smb_ldap_start_tls)
  Failed to issue the StartTLS instruction: Protocol error
[2010/02/23 14:30:28,  0] passdb/secrets.c:71(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2010/02/23 14:30:28,  0] lib/util.c:1480(smb_panic)
  PANIC (pid 1972): could not open secrets db
[2010/02/23 14:30:28,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 13 stack frames:
   #0 net(log_stack_trace+0x1a) [0x7effba310bca]
   #1 net(smb_panic+0x1f) [0x7effba310c8f]
   #2 net(get_global_sam_sid+0x6dd) [0x7effba2428dd]
   #3 net [0x7effba52f0c6]
   #4 net(smbldap_search_domain_info+0x2fe) [0x7effba52f68e]
   #5 net(pdb_init_ldapsam+0x173) [0x7effba2ce493]
   #6 net(make_pdb_method_name+0xe9) [0x7effba2bfc39]
   #7 net [0x7effba2c000c]
   #8 net(initialize_password_db+0x14) [0x7effba2c2e74]
   #9 net [0x7effba1c14a2]
   #10 net(main+0x7f9) [0x7effba1c0ed9]
   #11 /lib/libc.so.6(__libc_start_main+0xfd) [0x7effb7738abd]
   #12 net [0x7effba1c0609]
[2010/02/23 14:30:28,  0] lib/util.c:1485(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 1972]
[2010/02/23 14:30:28,  0] lib/util.c:1493(smb_panic)
  smb_panic(): action returned status 0
[2010/02/23 14:30:28,  0] lib/fault.c:307(dump_core)
  Can not dump core: corepath not set up

```

I am also unable to add users or change passwords.


Any ideas?

---

### Post by cbhr4u on 2010-03-10
Hey Abishur,
   Just wanted to say thanks for all your help and for the tutorial, learned so much about linux and I have a working PDC without paying Microsoft a cent. I appreciate you taking your time to do a tutorial like this. Thanks again.
Josh

---

### Post by Pablo Alonso on 2010-03-16
> **makak06 said:**
> Hi everyone, 

When I execute 
[FONT=Verdana][SIZE=2]
agnes@old:~$ sudo slapadd -v -l /etc/ldap/init.ldif
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
I have this :
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
/etc/ldap/slapd.conf: line 116: rootdn is always granted unlimited privileges.
/etc/ldap/slapd.conf: line 133: rootdn is always granted unlimited privileges.
added: "dc=example,dc=local" (00000001)
added: "cn=admin,dc=example,dc=local" (00000002)
added: "ou=Users,dc=example,dc=local" (00000003)
added: "ou=Groups,dc=example,dc=local" (00000004)
added: "ou=Computers,dc=example,dc=local" (00000005)
added: "ou=Idmap,dc=example,dc=local" (00000006)
_#################### 100.00% eta   none elapsed            none fast!         
Closing DB... 			 		[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
I would like to know if the two first line are an errors ? or just an information ?
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

Hi to all !!!

Makak06 and everybody have you found out an answer, I'm stuck in same question!
Thanks!

Pablo

---

### Post by cbhr4u on 2010-03-17
> **Pablo Alonso said:**
> Hi to all !!!

Makak06 and everybody have you found out an answer, I'm stuck in same question!
Thanks!

Pablo

I believe that the first two lines will always appear as long as you are getting the 100% on the end I believe you should be good to go.

---

### Post by Pablo Alonso on 2010-03-17
> **cbhr4u said:**
> I believe that the first two lines will always appear as long as you are getting the 100% on the end I believe you should be good to go.

Hi cbhr4u, thanks for the reply and confirmation! Finally yesterday I thought that because everybody has posted similar results...

I have another issue that was mentioned already but I cannot get rid of it the way it was suggested, maybe you have a clue...

when doing: smbldap-populate I get this same error of RomanJr and I have triple checked the correct password supplied in /etc/smbldap-tools/smbldap_bind.conf and it is the same as provided in steps:

[FONT=Verdana]slappasswd   -s YOUR-PASSWORD-GOES-HERE 			 		

and
[/FONT][FONT=Verdana][SIZE=1]
smbpasswd -W[/SIZE][/FONT]
[FONT=Verdana]
[/FONT]I don't understand whats wrong! ... help appreciated....

regards,
Pablo


> **RomanJr said:**
> Hi..First off thanks for this great tutorial.  

rromanjr@ubuntu-svr:/usr/sbin$ sudo smbldap-populate
Populating LDAP directory for domain RTECH (S-1-5-21-2673721247-2330088800-401481966)
(using builtin directory structure)

entry dc=RTECH,dc=local already exist.
entry ou=Users,dc=RTECH,dc=local already exist.
entry ou=Groups,dc=RTECH,dc=local already exist.
entry ou=Computers,dc=RTECH,dc=local already exist.
entry ou=Idmap,dc=RTECH,dc=local already exist.
adding new entry: uid=root,ou=Users,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 55.
adding new entry: uid=nobody,ou=Users,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 83.
adding new entry: cn=Domain Admins,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 95.
adding new entry: cn=Domain Users,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 106.
adding new entry: cn=Domain Guests,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 117.
adding new entry: cn=Domain Computers,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 128.
adding new entry: cn=Administrators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 173.
adding new entry: cn=Account Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 195.
adding new entry: cn=Print Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 206.
adding new entry: cn=Backup Operators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 217.
adding new entry: cn=Replicators,ou=Groups,dc=RTECH,dc=local
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 228.
entry sambaDomainName=RTECH,dc=RTECH,dc=local already exist. Updating it...
failed to modify entry: modifications require authentication at /usr/sbin/smbldap-populate line 492, <GEN1> line 236.

Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist
rromanjr@ubuntu-svr:/usr/sbin$


not sure where to go from here...I did not have any errors up till now and I am not sure how to fix the root doesn't exist.

---

### Post by cbhr4u on 2010-03-17
No means am I a Linux expert but it almost looks like you dont have admin rights wehn you run the smbldap-populate are you doing it as root? If not you may try that, or do a sudo when you run it.

> **Pablo Alonso said:**
> Hi cbhr4u, thanks for the reply and confirmation! Finally yesterday I thought that because everybody has posted similar results...

I have another issue that was mentioned already but I cannot get rid of it the way it was suggested, maybe you have a clue...

when doing: smbldap-populate I get this same error of RomanJr and I have triple checked the correct password supplied in /etc/smbldap-tools/smbldap_bind.conf and it is the same as provided in steps:

[FONT=Verdana]slappasswd   -s YOUR-PASSWORD-GOES-HERE                      

and
[/FONT][FONT=Verdana][SIZE=1]
smbpasswd -W[/SIZE][/FONT]
[FONT=Verdana]
[/FONT]I don't understand whats wrong! ... help appreciated....

regards,
Pablo

---

### Post by Pablo Alonso on 2010-03-17
> **cbhr4u said:**
> No means am I a Linux expert but it almost looks like you dont have admin rights wehn you run the smbldap-populate are you doing it as root? If not you may try that, or do a sudo when you run it.

Hi cbhr4u, I have found and overcome the problem!!!

the answer is:

in smbldap_bind.conf is says by default "Manager" instead of "admin"
I figured it out looking in the installldap.sh automated script posted here: [http://ubuntuforums.org/showpost.php?p=7921519&postcount=24](http://ubuntuforums.org/showpost.php?p=7921519&postcount=24)

> 
############################
# Credential Configuration #
############################
# Notes: you can specify two differents configuration if you use a
# master ldap for writing access and a slave ldap server for reading access
# By default, we will use the same DN (so it will work for standard Samba
# release)
slaveDN=\"cn=admin,$LdapDomain\"
slavePw=\"$Ldappasswd\"
masterDN=\"cn=admin,$LdapDomain\"
masterPw=\"$Ldappasswd\" Thanks for your help !!! I'm going to continue now to achive ultimate success !!! :p

Regards,
Pablo

---

### Post by Pablo Alonso on 2010-03-17
> **Overcast32 said:**
> One question though - if I want to setup H: drives in windows for the users - not profiles at all, just an H: drive mapping to /ldaphome/*username*.. what all would I need to add?

I tried this - but no luck just yet. 

Added to [B]smbldap.conf
[/B]
```

# The UNC path to home drives location (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon home'
# directive and/or disable roaming profiles
# Ex: userSmbHome="\\PDC-SMB3\%U"
userSmbHome="\\192.168.0.2\%U"

# The UNC path to profiles locations (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon path'
# directive and/or disable roaming profiles
# Ex: userProfile="\\PDC-SMB3\profiles\%U"
userProfile=

# The default Home Drive Letter mapping
# (will be automatically mapped at logon time if home directory exist)
# Ex: userHomeDrive="H:"
userHomeDrive="H:"

```And then added to **smb.conf**
```

        logon drive = H:
        logon home = \\192.168.0.2\%u
        logon path =
        logon script = logon.cmd
```Am I missing something?

Should I only be editing one of the two or should I be using the Debian path on any of those? (like /ldaphome/%U)

I can browse/read/create manually in the folder, so it's not permissions - I don't think, it's set to '700'

Hi, I have it working now.
forget using smbldap.conf
use /etc/samba/smb.conf to do this.

Suggestion: have tried using %U instead of %u ? I have read somewhere you can try %S instead. don know why.

also I have configured just in case is useful somehow...
        logon path = \\servername\%U


Good luck,
Pablo

---

### Post by waygooder on 2010-03-25
First off, thank you for all of the good info. Ive gotten further into installing openldap using your guide than any other I have tried.

That said I have hit a bump and need a little help.

I have gotten to the point of adding a user. I have been able to figure out my mistakes and get everything working to this point.

but when I try to add user I get this:

$ sudo smbldap-useradd -a -m matthewb -c "Matthew B" matthewb
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/smbldap_tools.pm line 135, <CONFIGFILE> line 23.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/smbldap_tools.pm line 135, <CONFIGFILE> line 24.
Could not find base dn, to get next uidNumber at /usr/share/perl5/smbldap_tools.pm line 1073, <DATA> line 466.


any ideas, ive spent hours searching for what I have done wrong but have been unsuccessful.

thanks:D

---

### Post by waygooder on 2010-03-25
Nevermind I found the problem

found some extra code that made its way into the config file, it just took me looking at it 50 times to find it.

it works now :D

---

### Post by tombutcher1990 on 2010-03-30
Hi There,

first off, this is a great guide! really useful, i'm not so great with linux servers but its helped a lot.

only one question, when i try and join the domain with a windows 7 client, i get an "access denied" error, and it says that the join attempt was unsuccessful, this could be down to the computer account already existing or the credentials being incorrect.

i assume the credentials are not incorrect, as i've used my sysadmin account that i created at the start. i did try using the root account as well at one point (i know, i shouldn't!) and i went into my Webmin config and there was 2 computer accounts (i tried changing the computer name to see if this would help at all) and i deleted both of those entries.


Any ideas? cos i've got all windows 7 clients and i need to get them working!!

Thanks in advance

Tom

---

### Post by cdblindaus on 2010-04-05
Received this message when populating samba;

"failed to modify entry: structural object class modification from 'sambaDomain' to 'inetOrgPerson' not allowed at /usr/sbin/smbldap-populate line 492, <GEN1> line 235"

not sure what this means can someone help?

---

### Post by Pablo Alonso on 2010-04-06
Hi, I have followed all instructions and I got it working perfect. But as a result of this implementation a new problem arised and I would like to know if someone have faced it and fixed it.

the problem is finally when everything works with ldap and samba you cannot change or set passwords for new normal users in the system.

for example if I run the command: $sudo adduser paul
when time to set password comes I receive the following error msg:

passwd: Authentication token manipulation error
passwd: password unchanged

and if I try to change it manually, I can't and I receive same error!

please help with this one!
all the rest with ldap works fine.

Thank you all.

regards,
Pablo Alonso

---

### Post by ragnaruss on 2010-04-06
Hey guys,

Awesome guide, the best on here for this and everything worked fine so far until i get to the point where I add a new user with:

[FONT=Verdana]                                         smbldap-useradd   -a -m -M matthewb -c &#8220;Matthew B&#8221; matthewb                      [/FONT]

All I get is 

/usr/sbin/smbldap-useradd: illegal username

I'm nearly there and would really appreciate the help. I would of looked up any errors i had except i have had any to this point.

FIXED
If i removed:

[FONT=Verdana]-c &#8220;Matthew B&#8221;

It works.

New problem now, I told my xp sp3 machine to join the domain, which it did, then restarted it and tried to log in which it starts to do, but the it just sits at loading your personal setting an doesn't seem to go anywhere. Is there some configuration i've missed out on here?
                     [/FONT]

---

### Post by Hokorippoi on 2010-04-13
When I try to populate I get this:
```
adding new entry: dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <DATA> line 466.
adding new entry: ou=Users,dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <GEN1> line 12.
adding new entry: ou=Groups,dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <GEN1> line 17.
adding new entry: ou=Computers,dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <GEN1> line 22.
adding new entry: ou=Idmap,dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <GEN1> line 27.
adding new entry: uid=root,ou=Users,dc=school,dc=local
failed to add entry: objectClass: value #3 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 55.
adding new entry: uid=nobody,ou=Users,dc=school,dc=local
failed to add entry: objectClass: value #3 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 83.
adding new entry: cn=Domain Admins,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 95.
adding new entry: cn=Domain Users,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 106.
adding new entry: cn=Domain Guests,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 117.
adding new entry: cn=Domain Computers,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 128.
adding new entry: cn=Administrators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 173.
adding new entry: cn=Account Operators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 195.
adding new entry: cn=Print Operators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 206.
adding new entry: cn=Backup Operators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 217.
adding new entry: cn=Replicators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 228.
adding new entry: sambaDomainName=school,dc=school,dc=local
failed to add entry: invalid DN at /usr/sbin/smbldap-populate line 499, <GEN1> line 236.

```

---

### Post by Rokurosv on 2010-04-18
Hi, just wanna say thanks for this tutorial it has been very helpful.
So far I've encountered an error when I try to join a Vista machine to the domain. I get a message saying that it cannot find the domain, let's say example.com

And I get this
```
The following error occurred when DNS was queried for the service location
(SRV) resource record used to locate a domain controller for domain
smallbusiness.local:

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for
_ldap._tcp.dc._msdcs.example.com

Common causes of this error include the following:

- The DNS SRV records required to locate a domain controller for the domain
are not registered in DNS. These records are registered with a DNS server
automatically when a domain controller is added to a domain. They are
updated by the domain controller at set intervals. This computer is
configured to use DNS servers with following IP addresses:

dns.server.1(not my actual dns servers)
dns.server.2

- One or more of the following zones do not include delegation to its child
zone:

example.com
com
. (the root zone)
```

My dns servers resolve the bceslx.com address, I can even ping it succesfully, but for some reason my client looks for _ldap._tcp.dc._msdcs.example.com

Any idea on what should I do, is it a DNS error or something with my LDAP server?

---

### Post by bepis1337 on 2010-04-24
Great guide, I failed setting up ldap with the new [FONT=Verdana][SIZE=2]slapd.d directory structure[/SIZE][/FONT].
Thanks for sharing it!!!

greetings

---

### Post by UncleBoxy on 2010-04-24
Great step by step guide.  I was trying to use Webmin to set up my LDAP server, and I was getting no where.  You'd think that there would be an easier way to do all this stuff, but no pain, no gain, right?

I got everything set up and working great.  I was able to get my windows 7 machines to join my newly created domain just fine.  However, I do get some errors when trying to add domain users to my box (at least I think that's what I'm doing).  I hate to sound like a complete n00b here, so I attached the screenshots of what it did right after I joined the domain (before the 1st reboot).

They are, in order of occurrence, DomainUser01.png, DomainUser02.png, DomainUser03.png.

Btw, this didn't prevent me from actually joining the domain.  That went fine and I was able to do a domain login after a reboot.

Chris

---

### Post by xpam on 2010-07-10
Thanks a lot for the information, specially about windows 7


Regards,  ):P

---

### Post by BarryDocks on 2010-10-06
Hi there,

really struggling to get this to work, have already tried unsuccessfully on 9.04 with this tutorial [http://ubuntuforums.org/showthread.php?t=1184288]("http://ubuntuforums.org/showthread.php?t=1184288")

I get as far as:```
root@ubuntu:~# ldapsearch -xLLL -b "dc=example,dc=com"
No such object (32)

```

any suggestions?](*,)

---

### Post by GoTerpsGo on 2010-12-26
Did you ever fix this?  Could you please clue me in if you did?


> **Hokorippoi said:**
> When I try to populate I get this:
```
adding new entry: dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <DATA> line 466.
adding new entry: ou=Users,dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <GEN1> line 12.
adding new entry: ou=Groups,dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <GEN1> line 17.
adding new entry: ou=Computers,dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <GEN1> line 22.
adding new entry: ou=Idmap,dc=school,dc=local
failed to add entry: no global superior knowledge at /usr/sbin/smbldap-populate line 499, <GEN1> line 27.
adding new entry: uid=root,ou=Users,dc=school,dc=local
failed to add entry: objectClass: value #3 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 55.
adding new entry: uid=nobody,ou=Users,dc=school,dc=local
failed to add entry: objectClass: value #3 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 83.
adding new entry: cn=Domain Admins,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 95.
adding new entry: cn=Domain Users,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 106.
adding new entry: cn=Domain Guests,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 117.
adding new entry: cn=Domain Computers,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 128.
adding new entry: cn=Administrators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 173.
adding new entry: cn=Account Operators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 195.
adding new entry: cn=Print Operators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 206.
adding new entry: cn=Backup Operators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 217.
adding new entry: cn=Replicators,ou=Groups,dc=school,dc=local
failed to add entry: objectClass: value #1 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 228.
adding new entry: sambaDomainName=school,dc=school,dc=local
failed to add entry: invalid DN at /usr/sbin/smbldap-populate line 499, <GEN1> line 236.

```

---

### Post by sergio_6 on 2011-03-02
I have a problem when I do:

[FONT=Verdana][SIZE=2]ldapsearch   -xLLL -b "dc=example,dc=com"

It says:

sergio@desktop:~$ ldapsearch -xLLL -b "dc=example,dc=com"
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)


And I dont know how to fix it because i am a noob in Linux. Any help please?

regards,
Sergio
[/SIZE][/FONT]

---

### Post by sergio_6 on 2011-03-02
I have solved!!! sorry to cause troubles.

I didnt start the daemon so i cant run. I am trying the default configuration so dc=example dc=com i changed it to dc=example dc=local


about the post of a mate before mine i wanna tell him if he did firstly

[FONT=Verdana][SIZE=2]/etc/init.d/slapd start

and after that [/SIZE][/FONT] 

[FONT=Verdana][SIZE=2]ldapsearch   -xLLL -b "dc=example,dc=com"[/SIZE][/FONT]

If you dont type /etc/init.d/slapd start first you will have problems.

I hope it helps you and sorry about my English.

Regards,
Sergio

---

### Post by sergio_6 on 2011-03-02
I have another problem and I cant find the answer.....

When I tried to do:

 net getlocalSID


it says that net isnt in the system and that i have to install it from samba-client-bin or from samba4.  I tried to install it from samba-client-bin or something like this and it gave me a SID, but it gives me errors too.... Can you tell me why I dont have NET?. O'll try to do again all the guide (again xD)...., little by litttle I am advancing...


thanks for your help

Regards,
Sergio.

---

### Post by VlaDeMaN on 2011-05-16
hey everyone,

im having issues test binding a windows 7 x64 ultimate SP1 to a newly created scientific linux 6 box running samba 3.5.4. i posted in the ubuntu forums cause you guys seem to know your stuff.

well, i modified the registry settings for Lanman:

HKLM\system\currentcontrolset\lanmanworkstation\parameters:

DNSNameResolutionRequired = 0
DomainCompatibilityMode = 1

HKLM\system\currentcontrolset\services\netlogon\parameters

RequireSignOrSeal = 1
RequireStrongKey = 1

WINS servers are added

primary DNS is manually set to the DC

Local Security Policy for LAN manager Authentication Level is Send LM & NTLM - use NTLMv2 if negotiated

i keep getting this error.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192381&stc=1&d=1305584904[/IMG]

the name has not been registered before and the error also comes if i change the name too. 

ive searched quite a bit, and nothing seems to help

thanks in advance!

---

### Post by lance bermudez on 2011-07-02
Hey do you guy have a guid that works with the new ubuntu 11.04? I have tried some but Got lost check out my post [http://ubuntuforums.org/showthread.php?p=11003686#post11003686](http://ubuntuforums.org/showthread.php?p=11003686#post11003686)

---

### Post by s33d3r on 2011-11-22
Hi there... Nice Tutorial

I have a bit problem...
I am trying to configure open LDAP on Ubuntu 11.10 
Everything goes perfect but in configuring samba i am getting a bit of problem.

after making the necessary changes in smb.conf when i m starting restart following the command
/init.d/samba restart i am getting an error message stating 
-bash: /etc/init.d/samba: No such file or directory

I am not able to get the solution for this error 

moving ahead in finding out the sid value again i m getting one error stating

[2011/11/22 01:31:30.277551,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:30.278168,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:30.278519,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:30.278800,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:31.279795,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:31.279904,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:31.280420,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:31.280465,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:32.281898,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:32.282008,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:32.282038,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:32.282063,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:33.282843,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:33.283065,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:33.283099,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:33.283125,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:34.283858,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:34.283967,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:34.283997,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:34.284023,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:35.285074,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:35.285184,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:35.285214,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:35.285240,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:36.285982,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:36.286090,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:36.286119,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:36.286145,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:37.286932,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:37.287042,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:37.287072,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:37.287098,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:38.288056,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:38.288165,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:38.288194,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:38.288220,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:39.289014,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:39.289118,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:39.289147,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:39.289173,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:40.290114,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:40.290223,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:40.290253,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:40.290279,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:41.291119,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:41.291221,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:41.291251,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:41.291277,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:42.294646,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:42.294805,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:42.294847,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:42.294874,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:43.296122,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:43.296228,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:43.296257,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:43.296283,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:44.296907,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:44.297011,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:44.297041,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:44.297067,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:45.298138,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:45.298246,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:45.298276,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/11/22 01:31:45.298303,  0] lib/smbldap.c:1108(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/11/22 01:31:45.298397,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/11/22 01:31:45.298426,  0] lib/util.c:1468(smb_panic)
  PANIC (pid 6334): could not open secrets db
[2011/11/22 01:31:45.480993,  0] lib/util.c:1572(log_stack_trace)
  BACKTRACE: 11 stack frames:
   #0 net(log_stack_trace+0x1a) [0x7fcde1a2f03a]
   #1 net(smb_panic+0x21) [0x7fcde1a2f111]
   #2 net(get_global_sam_sid+0x688) [0x7fcde1950e98]
   #3 net(pdb_init_ldapsam+0x69f) [0x7fcde19e8daf]
   #4 net(make_pdb_method_name+0xe9) [0x7fcde19d9709]
   #5 net(+0x1f7acc) [0x7fcde19d9acc]
   #6 net(initialize_password_db+0x14) [0x7fcde19dc6b4]
   #7 net(+0xdc7f0) [0x7fcde18be7f0]
   #8 net(main+0x830) [0x7fcde18be510]
   #9 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7fcddedd230d]
   #10 net(+0xdc6f5) [0x7fcde18be6f5]
[2011/11/22 01:31:45.481636,  0] lib/util.c:1473(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 6334]
[2011/11/22 01:31:45.569713,  0] lib/util.c:1481(smb_panic)
  smb_panic(): action returned status 0
[2011/11/22 01:31:45.570471,  0] lib/fault.c:312(dump_core)
  Can not dump core: corepath not set up


Plzz Help me out

---

### Post by vinterkind on 2011-12-19
> **tombutcher1990 said:**
> Hi There,

first off, this is a great guide! really useful, i'm not so great with linux servers but its helped a lot.

only one question, when i try and join the domain with a windows 7 client, i get an "access denied" error, and it says that the join attempt was unsuccessful, this could be down to the computer account already existing or the credentials being incorrect.

i assume the credentials are not incorrect, as i've used my sysadmin account that i created at the start. i did try using the root account as well at one point (i know, i shouldn't!) and i went into my Webmin config and there was 2 computer accounts (i tried changing the computer name to see if this would help at all) and i deleted both of those entries.


Any ideas? cos i've got all windows 7 clients and i need to get them working!!

Thanks in advance

Tom

Hi Tom,

 have you ever solved this problem ? I've got the same error. I checked on the packages, and they've provided me with [COLOR=RoyalBlue]*SAM Response - user unknown.*[/COLOR] I tried to join Win7 with user root. 

But exactly the same user could provide me with the information I get from running *net rpc info*.

My System: ubuntu 11.10 with Samba 3.4.7 

cheers

---

### Post by jitenderana on 2012-04-30
Hi Sir,
 
i was successfully configure the LDAP domain controller, and i am very thanksful to you, to write greate guide to configure Samba LDAP in simple and quick.
 
Can you do more more favior to we all, can you write about the replication of the above mentioed master ldap server. i was try to configure the BDC but don't work...
 
 
Thanks in advance...

---

### Post by rahuljanghel on 2012-10-10
I am facing below error :

>>>>
root@dataproctor:/etc/smbldap-tools# smbldap-populate
Populating LDAP directory for domain EXAMPLE (S-1-5-21-4073358430-2772322667-4277095439)
(using builtin directory structure)

erreur LDAP: Can't contact master ldap server for writing (IO::Socket::INET: Bad hostname 'ldap.iallanis.info') at /usr/share/perl5/smbldap_tools.pm line 322.
>>>
line 322 from file as below :
/usr/share/perl5/smbldap_tools.pm :
[B]322         $ldap_master = Net::LDAP->new(
323             "$config{masterLDAP}",
324             port    => "$config{masterPort}",
325             version => 3,
326             timeout => 60,
327
328             # debug => 0xffff,
[/B]
Were i am doing mistake ?

---

### Post by rahuljanghel on 2013-03-02
Hi,
I have left with 9.10 and now trying with 12.04.
now the problem is .. it is able to authenticate with root account from a win7 desktop but unable to auth any ldap client.
pls let me know if you want any log to check...

Regards,
Rahul Janghel.

---

### Post by cdtu on 2013-10-24
similar issue on Centos6:

migrationtools.noarch            47-7.el6                     @base   
openldap.x86_64                  2.4.23-32.el6_4.1            @updates
[

ISSUE1
[root@sv migrationtools]# pwd
/usr/share/migrationtools
[root@sv migrationtools]# ./migrate_all_offline.sh

slapadd: could not add entry dn="cn=raid-am,ou=Services,dc=example,dc=com" (line=16500)


SOLUTION1

[https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=428037](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=428037)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch31_:_Centralized_Logins_Using_LDAP_and_RADIUS#.Umla_tcvCcY](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch31_:_Centralized_Logins_Using_LDAP_and_RADIUS#.Umla_tcvCcY)

  265  sed -i.bck 's/2013\/tcp/22013\/tcp/g' /etc/services 
grep raid-am /etc/services 
raid-am         2007/udp                #
raid-am         22013/tcp    



ISSUE2
slapadd: could not add entry dn="cn=terminaldb,ou=Services,dc=example,dc=com" (line=16550): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)

SOLUTION2
[root@sv migrationtools]# grep terminaldb /etc/services
terminaldb      2008/udp                #
terminaldb      2018/tcp 

[root@sv migrationtools]# sed -i.blcl 's/2018\/tcp/12018\/tcp/g' /etc/services
[root@sv migrationtools]# grep 12018 /etc/servicesterminaldb      12018/tcp                #
[root@sv migrationtools]# grep terminaldb /etc/servicesterminaldb      2008/udp                #
terminaldb      12018/tcp                #
[root@sv migrationtools]# 

[root@sv migrationtools]# rm -fr /var/lib/ldap/*



ISSUE 3:
slapadd: could not add entry dn="cn=whosockami,ou=Services,dc=example,dc=com" (line=16557): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
*#######               35.15% eta 01m57s elapsed          01m03s spd   4.2 k/s 
Closing DB...
Migration failed: saving failed LDIF to /tmp/nis.ldif.yn2KuY



SOLUTION3:
[root@sv migrationtools]# grep whosockami /etc/services
whosockami      2009/udp                #
whosockami      2019/tcp                #
[root@sv migrationtools]# grep 12019 /etc/services
[root@sv migrationtools]# sed -i.blc2 's/2019\/tcp/12019\/12019/g' /etc/services
[root@sv migrationtools]# grep whosockami /etc/serviceswhosockami      2009/udp                #
whosockami      12019/12019     

[root@sv migrationtools]# rm -fr /var/lib/ldap/*[root@sv migrationtools]# 



ISSUE 4
=> bdb_tool_entry_put: txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
slapadd: could not add entry dn="cn=Mon,ou=Services,dc=example,dc=com" (line=42798): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)


SOLUTION 4:
[root@sv ~]# grep -i "manager on" /etc/services
Mon             9255/tcp                # Manager On Network
Mon             9255/udp                # Manager On Network
[root@sv ~]# 

[root@sv ~]# sed -i.blcl2 's/9255\/tcp/19255\/tcp/g' /etc/services
[root@sv ~]# grep -i "manager on" /etc/services
Mon             19255/tcp                # Manager On Network
Mon             9255/udp                # Manager On Network

[root@sv migrationtools]# rm -fr /var/lib/ldap/*


Not working but commenting out:
#Mon             19255/tcp                # Manager On Network
Mon             9255/udp                # Manager On Network

[root@sv migrationtools]# rm -fr /var/lib/ldap/*

slapadd: could not add entry dn="cn=Mon,ou=Services,dc=example,dc=com" (line=42798): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
.##################    91.40% eta    26s elapsed          04m32s spd   2.2 k/s 
Closing DB...
Migration failed: saving failed LDIF to /tmp/nis.ldif.NNBL1K
[root@sv migrationtools]# grep Mon /tmp/nis.ldif.NNBL1K 
dn: cn=Mon,ou=Services,dc=example,dc=com
cn: Mon



Not working again. Commenting both:

#Mon             19255/tcp                # Manager On Network
#Mon             9255/udp                # Manager On Network


[root@sv migrationtools]# rm -fr /var/lib/ldap/*




ISSUE 2 was back again:
slapadd: could not add entry dn="cn=terminaldb,ou=Services,dc=example,dc=com" (line=44242): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)


Commenting out:
[root@sv migrationtools]# grep terminaldb /etc/services
terminaldb      2008/udp                #
terminaldb      12018/tcp                #
[root@sv migrationtools]# sed -i.bca 's/terminaldb/\#terminaldb/g' /etc/services
[root@sv migrationtools]# grep terminaldb /etc/services#terminaldb      2008/udp                #
#terminaldb      12018/tcp                #
[root@sv migrationtools]# 



ISSUE3 came back:
slapadd: could not add entry dn="cn=whosockami,ou=Services,dc=example,dc=com" (line=44235): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)
-##################    94.52% eta    12s elapsed          03m19s spd   3.6 k/s 
Closing DB...
Migration failed: saving failed LDIF to /tmp/nis.ldif.haZTK0
[root@sv migrationtools]# grep whosockami /etc/services
whosockami      2009/udp                #
whosockami      12019/12019  


Commenting out both

[root@sv migrationtools]# grep whosockami /etc/services#whosockami      2009/udp                #
#whosockami      12019/12019                #
[root@sv migrationtools]# 

[root@sv migrationtools]# rm -fr /var/lib/ldap/*[root@sv migrationtools]# 



ISSUE 1 came back:
slapadd: could not add entry dn="cn=raid-am,ou=Services,dc=example,dc=com" (line=45342): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)


Commenting out both

[root@sv migrationtools]# grep raid-am /etc/services
raid-am         2007/udp                #
raid-am         22013/tcp                #
[root@sv migrationtools]# sed -i.bl21 's/raid-am/\#raid-am/g' /etc/services
[root@sv migrationtools]# grep raid-am /etc/services#raid-am         2007/udp                #
#raid-am         22013/tcp      .

[root@sv migrationtools]# rm -fr /var/lib/ldap/*



ISSUE 5
slapadd: could not add entry dn="cn=vipera-ssl,ou=Services,dc=example,dc=com" (line=46749): txn_aborted! DB_KEYEXIST: Key/data pair already exists (-30995)

[root@sv migrationtools]# grep vipera-ssl /etc/services
vipera-ssl      122013/tcp               # Vipera Messaging Service over SSL Communication
vipera-ssl      12013/udp               # Vipera Messaging Service over SSL Communication
[root@sv migrationtools]# sed -i.bl2 's/vipera-ssl/\#vipera-ssl/g' /etc/services
[root@sv migrationtools]# grep vipera-ssl /etc/services#vipera-ssl       122013/tcp               # Vipera Messaging Service over SSL  Communication
#vipera-ssl      12013/udp               # Vipera Messaging Service over SSL Communication

[root@sv migrationtools]# rm -fr /var/lib/ldap/*[root@sv migrationtools]# 


done. finally :)

*###################    99.53% eta        elapsed          03m34s spd  "###################    99.63% eta        elapsed          03m35s spd  *###################    99.75% eta        elapsed          03m35s spd  -###################    99.90% eta   none elapsed          03m36s spd  .####################  100.00% eta   none elapsed          03m36s spd   4.4 k/s 
Closing DB...[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

---

