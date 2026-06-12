---
title: "Samba+LDAP problem"
date: 2010-03-22
forum: Server Platforms
---

### Post by alekseyn on 2010-03-22
Dear guys and gals,

I am new in *nix world so please bear with me and forgive my noob  questions.

I am trying to setup a server running Ubuntu Server 8.04 LTS to be a  Primary Domain Controller authenticating users with LDAP (running on the  same server), act like a print server for domain users, and act like a  mail server (with web access)

Here is my setup so far:

Apache  Webserver
 BIND DNS Server
 Dovecot IMAP/POP3 Server
 LDAP Server
 MySQL Database Server
 Postfix Mail Server
 Read User Mail
 SSH Server
 Samba Login Scripts
 Samba Windows File Sharing
 
 
I use Webmin.

everything is the latest version as of today.

on the front-end, I run an Endian Firewall Community edition 2.3, so my  Ubuntu server is behind this firewall.

Being a complete newbie I had to follow the tutorial on how to setup a  Samba PDC with OpenLDAP

[http://www.rrcomputerconsulting.com/view.php?article_id=3#articletop](http://www.rrcomputerconsulting.com/view.php?article_id=3#articletop)

That tutorial is probably the only one out there for complete newbies  and I have learned a lot trying to make it all work in the last few  weeks. Well... not everything works as I expected it to be...

To all of you experts out there - please guide me - and I am sure the  community will benefit from this threat as well.

Few notes:

The server I started to rebuild had UNIX users and groups on it.. not  too many, but they had home directories with info and a public share for  all

I must have installed everything from scratch (except for Ubuntu Server)  at least 5 times before I got it to sort of run...

So here are the problems I am having and workarounds that I found to  make is sort of work....

if I add user through Webmin module (LDAP users and groups) the user is  NOT created in Samba with an error 
```
 [B]Failed to save user : /usr/bin/pdbedit failed : ldapsam_add_sam_account: User 'tester' already in the base, with samba attributes
[/B]

 
```When in fact the user is NOT added to samba.... but added only to LDAP  users.... these two (Samba and LDAP) are not talking to each other but  only in Webmin as you will see below

So... If I want to add a user to the LDAP system so he can access Samba  shares I must stick to the following steps:
 (using UNIX user name - "tester" as an example with UID 1000)

 1. Rename the existing Unix user to tester1
 2. Add user to LDAP using the command inteface (I use Putty)
 smbldap-useradd -a -m -M tester-c "tester" tester
 then
 smbldap-passwd tester
 3. Rename a Unix user back to tester1 (Samba user by the name "tester"  and UID of 3000 as created by LDAP script will also be update to UID  1000)
4. Change UID in LDAP to unix UID (in my case from 3000 to 1000)

This way I have the same user name "tester" with same UID in all 3  systems - in local users of ubuntu, in Samba and in LDAP...

the reason for all of the above is that I can not just create a group in  LDAP, put users in it and assign this group to Samba share... 

creation of a group in LDAP Users and Groups module in Webmin resulst in  the following error
```

Failed to save group :

must supply a name

```Group is created in LDAP but not in Samba....
I can not create Domain Groups in Samba....
I can only create a group in Samba and link it to Unix group... and then  things work... hence the activities on user creating in LDAP described  above

I ran out of ideas and tired of reinstalling things.... it does not help  anyways.... 

Please help....

my config files are below.

/etc/host
```
127.0.0.1    server.nrg-global.local server
192.168.1.3    server.nrg-global.local server
127.0.0.1    localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```/etc/hostname
```
server
```/etc/samba/smb.conf
```

#======================= Global Settings =======================

[global]
    passwd chat = *Enter\snew\s*\spassword:* %n\n  *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    idmap gid = 10000-20000
    obey pam restrictions = no
    delete user from group script = /usr/sbin/smbldapgroupmod -x '%u'  '%g'
    passwd program = /usr/bin/passwd %u
    dns proxy = no
    netbios name = SERVER
    ldap passwd sync = Yes
    idmap uid = 10000-20000
    logon script = allusers.vbs
    workgroup = NRG-GLOBAL
    server signing = auto        
    syslog only = yes
    ldap admin dn = cn=admin,dc=nrg-global,dc=local
    security = user
    add machine script = /usr/sbin/smbldap-useradd -w '%m'
    usershare allow guests = yes
    max log size = 1000
    delete user script = /usr/sbin/smbldap-userdel '%u'
    server schannel = Auto 
    log file = /var/log/samba/log.%m
    printer = HP_Color_LaserJet_2600n
    ldap user suffix = ou=Users
    add group script = /usr/sbin/smbldap-groupadd -p '%g'
    socket options = TCP_NODELAY
    delete group script = /usr/sbin/smbldap-groupdel '%g'
    add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
    logon drive = 
    domain master = yes
    map to guest = bad user
    encrypt passwords = true
    passdb backend = ldapsam:ldap://localhost/
    logon home = 
    wins support = yes
    ldap delete dn = Yes
    ldap machine suffix = ou=Computers
    server string = %h server (Samba, Ubuntu)
    ldap group suffix = ou=Groups
    ldap suffix = dc=nrg-global, dc=local
    unix password sync = yes
    logon path = 
    add user script = /usr/sbin/smbldap-useradd -m '%u'
    set primary group script = /usr/sbin/smbldap-usermod -g '%g'  '%u'       
    syslog = 10
    ldap idmap suffix = ou=Users
    panic action = /usr/share/samba/panic-action %d
    domain logons = yes


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and  /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192


#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = no
   read only = no

   valid users = %S

[netlogon]
    comment = Network Logon Service
    writeable = yes
    valid users = @"Domain Admins"
    public = yes
    share modes = no
    path = /home/samba/netlogon

[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
   write list = root,aleksey

[public]
comment = Public Stuff
writeable = yes
public = yes
path = /data/public

[projects]
comment = Project Stuff
path = /data/projects
public = yes
write list = @Management,@Projects
;write list = @management,@projects

[management]
    writeable = yes
    valid users = @Management
    path = /home/management
[Test]
    comment = test
    valid users = @Testers
    writeable = yes
    public = yes
    path = /home/management_test

```/etc/ldap/sldap.conf
```
# This is the main slapd configuration file. See slapd.conf(5) for  more
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
loglevel        none

# Where the dynamically loaded modules are stored
modulepath    /usr/lib/ldap
moduleload    back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is  used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend        bdb

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend        <other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix dc=nrg-global,dc=local

rootdn cn=admin,dc=nrg-global,dc=local
# for syncrepl.
# rootdn          "cn=admin,dc=nrg-global,dc=local"

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing  DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG  directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update  this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057 for  more
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
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
#access to attrs=userPassword,shadowLastChange
access to  attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
        by dn="cn=admin,dc=nrg-global,dc=local" write
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
        by dn="cn=admin,dc=nrg-global,dc=local" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=nrg-global,dc=local" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix        "dc=debian,dc=org"
rootpw {crypt}24QOhzbSqbf56

```/etc/ldap/ldap.conf
```
###DEBCONF###
##
## Configuration of this file will be managed by debconf as long as the
## first line of the file says '###DEBCONF###'
##
## You should use dpkg-reconfigure to configure this file via debconf
##

#
# @(#)$Id: ldap.conf,v 1.38 2006/05/15 08:13:31 lukeh Exp $
#
# This is the configuration file for the LDAP nameservice
# switch library and the LDAP PAM module.
#
# PADL Software
# http://www.padl.com
#

# Your LDAP server. Must be resolvable without using LDAP.
# Multiple hosts may be specified, each separated by a 
# space. How long nss_ldap takes to failover depends on
# whether your LDAP client library supports configurable
# network or connect timeouts (see bind_timelimit).
host SERVER

# The distinguished name of the search base.
base dc=nrg-global,dc=local

# Another way to specify your LDAP server is to provide an
# uri with the server name. This allows to use
# Unix Domain Sockets to connect to a local LDAP Server.
uri ldap://127.0.0.1/
#uri ldaps://127.0.0.1/   
#uri ldapi://%2fvar%2frun%2fldapi_sock/
# Note: %2f encodes the '/' used as directory separator

# The LDAP version to use (defaults to 3
# if supported by client library)
ldap_version 3

# The distinguished name to bind to the server with.
# Optional: default is to bind anonymously.
#binddn cn=proxyuser,dc=padl,dc=com

# The credentials to bind with. 
# Optional: default is no credential.
#bindpw secret

# The distinguished name to bind to the server with
# if the effective user ID is root. Password is
# stored in /etc/ldap.secret (mode 600)
rootbinddn cn=admin,dc=nrg-global,dc=local

# The port.
# Optional: default is 389.
port 389

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
#bind_policy hard
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
#pam_groupdn cn=PAM,ou=Groups,dc=padl,dc=com

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
#pam_password clear

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
#pam_password_prohibit_message Please visit http://internal to change  your password.

# RFC2307bis naming contexts
# Syntax:
# nss_base_XXX        base?scope?filter
# where scope is {base,one,sub}
# and filter is a filter to be &'d with the
# default filter.
# You can omit the suffix eg:
# nss_base_passwd    ou=People,
# to append the default base DN but this
# may incur a small performance impact.
#nss_base_passwd    ou=People,dc=padl,dc=com?one
#nss_base_shadow    ou=People,dc=padl,dc=com?one
#nss_base_group        ou=Group,dc=padl,dc=com?one
#nss_base_hosts        ou=Hosts,dc=padl,dc=com?one
#nss_base_services    ou=Services,dc=padl,dc=com?one
#nss_base_networks    ou=Networks,dc=padl,dc=com?one
#nss_base_protocols    ou=Protocols,dc=padl,dc=com?one
#nss_base_rpc        ou=Rpc,dc=padl,dc=com?one
#nss_base_ethers    ou=Ethers,dc=padl,dc=com?one
#nss_base_netmasks    ou=Networks,dc=padl,dc=com?ne
#nss_base_bootparams    ou=Ethers,dc=padl,dc=com?one
#nss_base_aliases    ou=Aliases,dc=padl,dc=com?one
#nss_base_netgroup    ou=Netgroup,dc=padl,dc=com?one

# attribute/objectclass mapping
# Syntax:
#nss_map_attribute    rfc2307attribute    mapped_attribute
#nss_map_objectclass    rfc2307objectclass    mapped_objectclass

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
# Default is to use libldap's default behavior, which can be configured  in
# /etc/openldap/ldap.conf using the TLS_REQCERT setting.  The default  for
# OpenLDAP 2.0 and earlier is "no", for 2.1 and later is "yes".
#tls_checkpeer yes

# CA certificates for server certificate verification
# At least one of these are required if tls_checkpeer is "yes"
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
nss_initgroups_ignoreusers  backup,bin,bind,daemon,dhcp,dovecot,games,gnats,irc,klog,libuuid,list,lp,mail,man,mysql,news,ntp,openldap,postfix,proxy,root,sshd,sync,sys,syslog,uucp,www-data

```

---

