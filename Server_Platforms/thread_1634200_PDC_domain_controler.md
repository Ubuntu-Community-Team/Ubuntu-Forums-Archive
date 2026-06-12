---
title: "PDC domain controler"
date: 2010-11-30
forum: Server Platforms
---

### Post by Zitan on 2010-11-30
Could you explain mi something about PDC configuration?. 
This is piece of my samba configuration with LDAP
```
workgroup = PCPR
netbios name = SERWER
server string = Samba %h PDC

```My domain name is PCPR, (workgroup name is equal to the PDC's domain name, right?) but when I execute ```
net getlocalsid 
```i get ```
SID for domain SERWER is: S-1-5-21-3946501231-293034350-4217055208
```I'm confused, Why SERWER, should not be PCPR?

---

### Post by mdlueck on 2010-11-30
I am seeing similar results on my servers as well, returning the hostname of the box. hhhmmm.... This is with a 10.04 server, fully updated.

---

### Post by mdlueck on 2010-11-30
aaahhh, per "man net"...

> GETLOCALSID [DOMAIN]
       Prints the SID of the specified domain, or if the parameter is omitted, the SID of the local server.

so try:

```
net getlocalsid PCPR
```

---

### Post by Zitan on 2010-12-01
New problem When i tried to join to the domain i get this
message:
```
The following error ocurred attempting to join the domain "PCPR":
A device attached to the system is not functioning.
```This error can be caused by a thousand things. I do not know what is wrong. My configuration files

/etc/samba/smb.conf
```

[global]
# podstawowe opcje konfiguracji serwera
workgroup = PCPR
netbios name = Debian
server string = Samba PDC
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192

os level = 65
preferred master = yes
local master = yes
domain master = yes
domain logons = yes

security = user
guest ok = no
encrypt passwords = yes
null passwords = no

# hosts allow LAN
interfaces = eth1
hosts allow = 192.168.16. 127.
wins support = yes
name resolve order = wins lmhosts host bcast
dns proxy = no

log file = /var/log/samba/log.%m
log level = 2
syslog = 0
max log size = 50
hide unreadable = yes
hide dot files = yes

# konfiguracja LDAP
#passdb backend = ldapsam:ldap://127.0.0.1
passdb backend = ldapsam:ldap://serwer.pcpr.lan
ldap suffix = dc=pcpr,dc=lan
ldap machine suffix = ou=machines
ldap user suffix = ou=users
ldap group suffix = ou=groups
ldap admin dn = cn=admin,dc=pcpr,dc=lan
ldap ssl = no
enable privileges = yes

logon home = \%L%U.profile
logon drive = U:
logon path = \%Lprofiles%U
logon script = netlogon.bat OR %U.bat

# Do ldap passwd sync
ldap passwd sync = Yes
passwd program = /usr/sbin/smbldap-passwd %u
passwd chat = *New*password* %nn *Retype*new*password* %nn 

#*all*authentication*tokens*updated*
add user script = /usr/sbin/smbldap-useradd -m "%u"
ldap delete dn = Yes
delete user script = /usr/sbin/smbldap-userdel "%u"
add machine script = /usr/sbin/smbldap-useradd -w "%u"
add group script = /usr/sbin/smbldap-groupadd -p "%g"
delete group script = /usr/sbin/smbldap-groupdel "%g"
add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"

#polskie znaki
unix charset = ISO8859-2
dos charset = CP852

[netlogon]
comment = Network Logon Service
path = /home/samba/netlogon
guest ok = no
read only = yes
browseable = no

[homes]
path = /home/%U
comment = HOME Directories
browseable = no
writeable = yes
valid users = %S
read only = no
guest ok = no
inherit permissions = yes

[profiles]
path = /home/samba/profiles
valid users = %U, "@Domain Admins"
writeable = yes
browseable = no
default case = lower
preserve case = no
short preserve case = no
case sensitive = no
hide files = /desktop.ini/ntuser.ini/NTUSER.*/
create mask = 0600
directory mask = 0700
csc policy = disable
[global]
# podstawowe opcje konfiguracji serwera
workgroup = PCPR
netbios name = Debian
server string = Samba PDC
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192

os level = 65
preferred master = yes
local master = yes
domain master = yes
domain logons = yes

security = user
guest ok = no
encrypt passwords = yes
null passwords = no

# hosts allow LAN
interfaces = eth1
hosts allow = 192.168.16. 127.
wins support = yes
name resolve order = wins lmhosts host bcast
dns proxy = no

log file = /var/log/samba/log.%m
log level = 2
syslog = 0
max log size = 50
hide unreadable = yes
hide dot files = yes

# konfiguracja LDAP
#passdb backend = ldapsam:ldap://127.0.0.1
passdb backend = ldapsam:ldap://serwer.pcpr.lan
ldap suffix = dc=pcpr,dc=lan
ldap machine suffix = ou=machines
ldap user suffix = ou=users
ldap group suffix = ou=groups
ldap admin dn = cn=admin,dc=pcpr,dc=lan
ldap ssl = no
enable privileges = yes

logon home = \%L%U.profile
logon drive = U:
logon path = \%Lprofiles%U
logon script = netlogon.bat OR %U.bat

# Do ldap passwd sync
ldap passwd sync = Yes
passwd program = /usr/sbin/smbldap-passwd %u
passwd chat = *New*password* %nn *Retype*new*password* %nn 

#*all*authentication*tokens*updated*
add user script = /usr/sbin/smbldap-useradd -m "%u"
ldap delete dn = Yes
delete user script = /usr/sbin/smbldap-userdel "%u"
add machine script = /usr/sbin/smbldap-useradd -w "%u"
add group script = /usr/sbin/smbldap-groupadd -p "%g"
delete group script = /usr/sbin/smbldap-groupdel "%g"
add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"

#polskie znaki
unix charset = ISO8859-2
dos charset = CP852

[netlogon]
comment = Network Logon Service
path = /home/samba/netlogon
guest ok = no
read only = yes
browseable = no

[homes]
path = /home/%U
comment = HOME Directories
browseable = no
writeable = yes
valid users = %S
read only = no
guest ok = no
inherit permissions = yes

[profiles]
path = /home/samba/profiles
valid users = %U, "@Domain Admins"
writeable = yes
browseable = no
default case = lower
preserve case = no
short preserve case = no
case sensitive = no
hide files = /desktop.ini/ntuser.ini/NTUSER.*/
create mask = 0600
directory mask = 0700
csc policy = disable

```/etc/hostname
```

SERWER.PCPR.LAN
127.0.0.1    SERWER.PCPR.LAN    localhost.localdomain    localhost
1127.0.0.1    localhost
192.168.16.1    serwer.pcpr.lan    Debian

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```/etc/ldap/slapd.conf
```

# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/samba.schema

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

# The tool-threads parameter sets the actual amount of cpu's that is used
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
suffix dc=pcpr,dc=lan

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn cn=admin,dc=pcpr,dc=lan
rootpw {MD5}xWdfmrH7SHUMYKOBcAJQRw==

#### to zmienilem ####
index entryCSN eq
index entryUUID eq


# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

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
index                   objectClass eq
index cn                      pres,sub,eq
index sn                      pres,sub,eq
index uid                     pres,sub,eq
index displayName             pres,sub,eq
index uidNumber               eq
index gidNumber               eq
index memberUID               eq
index sambaSID                eq
index sambaPrimaryGroupSID    eq
index sambaDomainName         eq
index default                 sub

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
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=test,dc=com" write
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
        by dn="cn=admin,dc=test,dc=com" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=test,dc=com" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix        "dc=debian,dc=org"

```/etc/ldap/ldap.conf
```

BASE dc=pcpr,dc=lan
URI ldap://serwer.pcpr.lan/
#host server.pcpr.lan
#binddn cn=admin,dc=pcpr,dc=lan
#bindpw {MD5}xWdfmrH7SHUMYKOBcAJQRw==
#bind_policy soft
#pam_password exop
#nss_base_passwd ou=People,ou=Users,dc=pcpr,dc=lan?one
#nss_base_shadow ou=People,ou=Users,dc=pcpr,dc=lan?one
#nss_base_passwd ou=Computers,ou=Users,dc=pcpr,dc=lan?one
#nss_base_shadow ou=Computers,ou=Users,dc=pcpr,dc=lan?one
#nss_base_group  ou=Groups,dc=pcpr,dc=lan?one
#ssl noldap data base

```Ldap data base
```

# extended LDIF
#
# LDAPv3
# base <dc=pcpr,dc=lan> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# pcpr.lan
dn: dc=pcpr,dc=lan
objectClass: dcObject
objectClass: organization
o: pcpr
dc: pcpr

# people, pcpr.lan
dn: ou=people,dc=pcpr,dc=lan
objectClass: top
objectClass: organizationalUnit
ou: people

# group, pcpr.lan
dn: ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: organizationalUnit
ou: group

# computer, pcpr.lan
dn: ou=computer,dc=pcpr,dc=lan
objectClass: top
objectClass: organizationalUnit
ou: computer

# idmap, pcpr.lan
dn: ou=idmap,dc=pcpr,dc=lan
objectClass: top
objectClass: organizationalUnit
ou: idmap

# root, people, pcpr.lan
dn: uid=root,ou=people,dc=pcpr,dc=lan
cn: root
sn: root
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: sambaSamAccount
objectClass: posixAccount
objectClass: shadowAccount
gidNumber: 0
uid: root
uidNumber: 0
homeDirectory: /home/root
sambaLogonTime: 0
sambaLogoffTime: 2147483647
sambaKickoffTime: 2147483647
sambaPwdCanChange: 0
sambaPrimaryGroupSID: S-1-5-21-3946501231-293034350-4217055208-512
sambaSID: S-1-5-21-3946501231-293034350-4217055208-500
loginShell: /bin/false
gecos: Netbios Domain Administrator
sambaLMPassword: 89EA3F9716D0E44A2C5AE1F1CFB9210F
sambaAcctFlags: [U]
sambaNTPassword: 7662BAB1D8FC49EF19E629FBA796C0E8
sambaPwdLastSet: 1291150784
sambaPwdMustChange: 1293742784
shadowMax: 30

# nobody, people, pcpr.lan
dn: uid=nobody,ou=people,dc=pcpr,dc=lan
cn: nobody
sn: nobody
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: sambaSamAccount
objectClass: posixAccount
objectClass: shadowAccount
gidNumber: 65534
uid: nobody
uidNumber: 65534
homeDirectory: /nonexistent
sambaPwdLastSet: 0
sambaLogonTime: 0
sambaLogoffTime: 2147483647
sambaKickoffTime: 2147483647
sambaPwdCanChange: 0
sambaPwdMustChange: 2147483647
sambaPrimaryGroupSID: S-1-5-21-3946501231-293034350-4217055208-514
sambaLMPassword: NO PASSWORDXXXXXXXXXXXXXXXXXXXXX
sambaNTPassword: NO PASSWORDXXXXXXXXXXXXXXXXXXXXX
sambaAcctFlags: [NUD        ]
sambaSID: S-1-5-21-3946501231-293034350-4217055208-2998
loginShell: /bin/sh

# Domain Admins, group, pcpr.lan
dn: cn=Domain Admins,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 512
cn: Domain Admins
memberUid: root
description: Netbios Domain Administrators
sambaSID: S-1-5-21-3946501231-293034350-4217055208-512
sambaGroupType: 2
displayName: Domain Admins

# Domain Users, group, pcpr.lan
dn: cn=Domain Users,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 513
cn: Domain Users
description: Netbios Domain Users
sambaSID: S-1-5-21-3946501231-293034350-4217055208-513
sambaGroupType: 2
displayName: Domain Users

# Domain Guests, group, pcpr.lan
dn: cn=Domain Guests,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 514
cn: Domain Guests
description: Netbios Domain Guests Users
sambaSID: S-1-5-21-3946501231-293034350-4217055208-514
sambaGroupType: 2
displayName: Domain Guests

# Domain Computers, group, pcpr.lan
dn: cn=Domain Computers,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 515
cn: Domain Computers
description: Netbios Domain Computers accounts
sambaSID: S-1-5-21-3946501231-293034350-4217055208-515
sambaGroupType: 2
displayName: Domain Computers

# Administrators, group, pcpr.lan
dn: cn=Administrators,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 544
cn: Administrators
description: Netbios Domain Members can fully administer the computer/sambaDom
 ainName
sambaSID: S-1-5-32-544
sambaGroupType: 5
displayName: Administrators

# Account Operators, group, pcpr.lan
dn: cn=Account Operators,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 548
cn: Account Operators
description: Netbios Domain Users to manipulate users accounts
sambaSID: S-1-5-32-548
sambaGroupType: 5
displayName: Account Operators

# Print Operators, group, pcpr.lan
dn: cn=Print Operators,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 550
cn: Print Operators
description: Netbios Domain Print Operators
sambaSID: S-1-5-32-550
sambaGroupType: 5
displayName: Print Operators

# Backup Operators, group, pcpr.lan
dn: cn=Backup Operators,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 551
cn: Backup Operators
description: Netbios Domain Members can bypass file security to back up files
sambaSID: S-1-5-32-551
sambaGroupType: 5
displayName: Backup Operators

# Replicators, group, pcpr.lan
dn: cn=Replicators,ou=group,dc=pcpr,dc=lan
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 552
cn: Replicators
description: Netbios Domain Supports file replication in a sambaDomainName
sambaSID: S-1-5-32-552
sambaGroupType: 5
displayName: Replicators

# PCPR, pcpr.lan
dn: sambaDomainName=PCPR,dc=pcpr,dc=lan
gidNumber: 3000
sambaDomainName: PCPR
sambaSID: S-1-5-21-3946501231-293034350-4217055208
objectClass: top
objectClass: sambaDomain
objectClass: sambaUnixIdPool
uidNumber: 3001
sambaPwdHistoryLength: 0
sambaMaxPwdAge: -1
sambaRefuseMachinePwdChange: 0
sambaNextRid: 1002

# monika, people, pcpr.lan
dn: uid=monika,ou=people,dc=pcpr,dc=lan
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
objectClass: sambaSamAccount
cn: monika
sn: monika
givenName: monika
uid: monika
uidNumber: 3000
gidNumber: 513
homeDirectory: /home/monika
loginShell: /bin/bash
gecos: Monika Zawada
sambaLogonTime: 0
sambaLogoffTime: 2147483647
sambaKickoffTime: 2147483647
sambaPwdCanChange: 0
displayName: monika
sambaSID: S-1-5-21-3946501231-293034350-4217055208-7000
sambaPrimaryGroupSID: S-1-5-21-3946501231-293034350-4217055208-513
sambaLMPassword: 44EFCE164AB921CAAAD3B435B51404EE
sambaAcctFlags: [U]
sambaNTPassword: 32ED87BDB5FDC5E9CBA88547376818D4
sambaPwdLastSet: 1291151926
sambaPwdMustChange: 1293743926
shadowMax: 30

# search result
search: 2
result: 0 Success

# numResponses: 19
# numEntries: 18

```SID
```

SID for domain PCPR is: S-1-5-21-3946501231-293034350-4217055208

```/etc/smbldap-tools/smbldap.conf
```

# $Source: $
# $Id: smbldap.conf,v 1.18 2005/05/27 14:28:47 jtournier Exp $
#
# smbldap-tools.conf : Q & D configuration file for smbldap-tools

#  This code was developped by IDEALX (http://IDEALX.org/) and
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

# Put your own SID. To obtain this number do: "net getlocalsid".
# If not defined, parameter is taking from "net getlocalsid" return
SID="S-1-5-21-3946501231-293034350-4217055208"

# Domain name the Samba server is in charged.
# If not defined, parameter is taking from smb.conf configuration file
# Ex: sambaDomain="IDEALX-NT"
sambaDomain=""

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
# If not defined, parameter is set to "127.0.0.1"
slaveLDAP="serwer.pcpr.lan"

# Slave LDAP port
# If not defined, parameter is set to "389"
slavePort="389"

# Master LDAP server: needed for write operations
# Ex: masterLDAP=127.0.0.1
# If not defined, parameter is set to "127.0.0.1"
masterLDAP="serwer.pcpr.lan"

# Master LDAP port
# If not defined, parameter is set to "389"
masterPort="389"

# Use TLS for LDAP
# If set to 1, this option will use start_tls for connection
# (you should also used the port 389)
# If not defined, parameter is set to "1"
ldapTLS="0"

# How to verify the server's certificate (none, optional or require)
# see "man Net::LDAP" in start_tls section for more details
verify=""

# CA certificate
# see "man Net::LDAP" in start_tls section for more details
cafile=""

# certificate to use to connect to the ldap server
# see "man Net::LDAP" in start_tls section for more details
clientcert=""

# key certificate to use to connect to the ldap server
# see "man Net::LDAP" in start_tls section for more details
clientkey=""

# LDAP Suffix
# Ex: suffix=dc=IDEALX,dc=ORG
suffix="dc=pcpr,dc=lan"

# Where are stored Users
# Ex: usersdn="ou=Users,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for usersdn
usersdn="ou=people,${suffix}"

# Where are stored Computers
# Ex: computersdn="ou=Computers,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for computersdn
computersdn="ou=computer,${suffix}"

# Where are stored Groups
# Ex: groupsdn="ou=Groups,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for groupsdn
groupsdn="ou=group,${suffix}"

# Where are stored Idmap entries (used if samba is a domain member server)
# Ex: groupsdn="ou=Idmap,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for idmapdn
idmapdn="ou=idmap,${suffix}"

# Where to store next uidNumber and gidNumber available for new users and groups
# If not defined, entries are stored in sambaDomainName object.
# Ex: sambaUnixIdPooldn="sambaDomainName=${sambaDomain},${suffix}"
# Ex: sambaUnixIdPooldn="cn=NextFreeUnixId,${suffix}"
#sambaUnixIdPooldn="sambaDomainName=${sambaDomain},${suffix}"
sambaUnixIdPooldn="sambaDomainName=PCPR,${suffix}"
# Default scope Used
scope="sub"

# Unix password encryption (CRYPT, MD5, SMD5, SSHA, SHA, CLEARTEXT)
hash_encrypt="MD5"

# if hash_encrypt is set to CRYPT, you may set a salt format.
# default is "%s", but many systems will generate MD5 hashed
# passwords if you use "$1$%.8s". This parameter is optional!
crypt_salt_format=""

##############################################################################
#
# Unix Accounts Configuration
#
##############################################################################

# Login defs
# Default Login Shell
# Ex: userLoginShell="/bin/bash"
userLoginShell="/bin/bash"

# Home directory
# Ex: userHome="/home/%U"
userHome="/home/%U"

# Default mode used for user homeDirectory
userHomeDirectoryMode="700"

# Gecos
userGecos="System User"

# Default User (POSIX and Samba) GID
defaultUserGid="513"

# Default Computer (Samba) GID
defaultComputerGid="515"

# Skel dir
skeletonDir="/etc/skel"

# Default password validation time (time in days) Comment the next line if
# you don't want password to be enable for defaultMaxPasswordAge days (be
# careful to the sambaPwdMustChange attribute's value)
defaultMaxPasswordAge="30"

##############################################################################
#
# SAMBA Configuration
#
##############################################################################

# The UNC path to home drives location (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon home'
# directive and/or disable roaming profiles
# Ex: userSmbHome="\\PDC-SMB3\%U"
userSmbHome=""

# The UNC path to profiles locations (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon path'
# directive and/or disable roaming profiles
# Ex: userProfile="\\PDC-SMB3\profiles\%U"
userProfile=""

# The default Home Drive Letter mapping
# (will be automatically mapped at logon time if home directory exist)
# Ex: userHomeDrive="H:"
userHomeDrive=""

# The default user netlogon script name (%U username substitution)
# if not used, will be automatically username.cmd
# make sure script file is edited under dos
# Ex: userScript="startup.cmd" # make sure script file is edited under dos
userScript=""

# Domain appended to the users "mail"-attribute
# when smbldap-useradd -M is used
# Ex: mailDomain="idealx.com"
mailDomain="pcpr.lan"

##############################################################################
#
# SMBLDAP-TOOLS Configuration (default are ok for a RedHat)
#
##############################################################################

# Allows not to use smbpasswd (if with_smbpasswd == 0 in smbldap_conf.pm) but
# prefer Crypt::SmbHash library
with_smbpasswd="0"
smbpasswd="/usr/bin/smbpasswd"

# Allows not to use slappasswd (if with_slappasswd == 0 in smbldap_conf.pm)
# but prefer Crypt:: libraries
with_slappasswd="0"
slappasswd="/usr/sbin/slappasswd"

# comment out the following line to get rid of the default banner
# no_banner="1"

```/etc/smbldap-tools/smbldap_bind.conf
```

############################
# Credential Configuration #
############################
# Notes: you can specify two differents configuration if you use a
# master ldap for writing access and a slave ldap server for reading access
# By default, we will use the same DN (so it will work for standard Samba
# release)
slaveDN="cn=admin,dc=pcpr,dc=lan"
slavePw="my_secret_password"
masterDN="cn=admin,dc=pcpr,dc=lan"
masterPw="my_secret_password"

```getent group
```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:bacula
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
Debian-exim:x:103:
mlocate:x:104:
ssh:x:105:
messagebus:x:106:
sambashare:x:107:
winbindd_priv:x:108:proxy
bind:x:109:
ssl-cert:x:110:
komisja:x:1001:
openldap:x:111:
machines:x:1002:
smbuser:x:1003:
debian-transmission:x:112:
komputery:x:1004:
mysql:x:113:
utempter:x:114:
avahi:x:115:
netdev:x:116:
bluetooth:x:117:
fuse:x:118:
Debian-gdm:x:119:
scanner:x:120:saned
saned:x:121:
jabberd:x:122:
bacula:x:123:
artur:x:1005:
nobody:x:1006:
sambamachines:x:1007:
nslcd:x:124:
nvram:x:125:
rdma:x:126:
kvm:x:127:
tss:x:128:
Domain Admins:*:512:root
Domain Users:*:513:
Domain Guests:*:514:
Domain Computers:*:515:
Administrators:*:544:
Account Operators:*:548:
Print Operators:*:550:
Backup Operators:*:551:
Replicators:*:552:

```/etc/pam_ldap.conf
```

###DEBCONF###
# the configuration of this file will be done by debconf as long as the
# first line of the file says '###DEBCONF###'
#
# you should use dpkg-reconfigure to configure this file
#
# @(#)$Id: pam_ldap.conf,v 1.38 2006/05/15 08:13:31 lukeh Exp $
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
#host 127.0.0.1

# The distinguished name of the search base.
base dc=pcpr,dc=lan

# Another way to specify your LDAP server is to provide an
#uri ldap://127.0.0.1
# Unix Domain Sockets to connect to a local LDAP Server.
uri ldap://serwer.pcpr.lan
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
# stored in /etc/pam_ldap.secret (mode 600)
rootbinddn cn=admin,dc=pcpr,dc=lan

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
#bind_policy hard

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
#pam_password_prohibit_message Please visit http://internal to change your password.

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
# Default is to use libldap's default behavior, which can be configured in
# /etc/openldap/pam_ldap.conf using the TLS_REQCERT setting.  The default for
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
pam_filter !(uidNumber=0)

```/etc/pam.d/common-account
```

#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
#

# here are the per-package modules (the "Primary" block)
account    [success=1 new_authtok_reqd=done default=ignore]    pam_unix.so 
# here's the fallback if no module succeeds
account    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
account    [success=ok new_authtok_reqd=done ignore=ignore user_unknown=ignore authinfo_unavail=ignore default=bad]    pam_ldap.so minimum_uid=1000
# end of pam-auth-update config

account sufficient pam_ldap.so
account required pam_unix.so try_first_pass

```/etc/pam.d/common-auth
```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_ldap.so minimum_uid=1000 use_first_pass
# here's the fallback if no module succeeds
auth    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

#auth sufficient pam_ldap.so
#auth required pam_unix.so nullok_secure try_first_pass

```/etc/pam.d/common-password
```

#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix crypt.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.

# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
password    [success=2 default=ignore]    pam_unix.so obscure sha512
password    [success=1 default=ignore]    pam_ldap.so minimum_uid=1000 try_first_pass
# here's the fallback if no module succeeds
password    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
password    optional    pam_gnome_keyring.so 
# end of pam-auth-update config

password sufficient pam_ldap.so
password required pam_unix.so nullok obscure min=4 max=8 md5 try_first_pass

```

---

### Post by Zitan on 2010-12-15
I had to issue the command ```
smbldap-useradd -w <name_of_the_computer>$
 
```only then successfully logged on to a domain. Unfortunately I can not move a user profile on the server. Instead, it is saved on the client hard disk C:.

Test user from database
```
ldapsearch -x -b "uid=testuser,ou=people,dc=pcpr,dc=lan"
# extended LDIF
#
# LDAPv3
# base <uid=testuser,ou=people,dc=pcpr,dc=lan> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# testuser, people, pcpr.lan
dn: uid=testuser,ou=people,dc=pcpr,dc=lan
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
objectClass: sambaSamAccount
cn: testuser
sn: testuser
givenName: testuser
uid: testuser
uidNumber: 3016
gidNumber: 513
homeDirectory: /home/testuser
loginShell: /bin/bash
gecos: Test User
sambaLogonTime: 0
sambaLogoffTime: 2147483647
sambaKickoffTime: 2147483647
sambaPwdCanChange: 0
displayName: testuser
sambaSID: S-1-5-21-3946501231-293034350-4217055208-7032
sambaPrimaryGroupSID: S-1-5-21-3946501231-293034350-4217055208-513
sambaLMPassword: 01FC5A6BE7BC6929AAD3B435B51404EE
sambaAcctFlags: [U]
sambaNTPassword: 0CB6948805F797BF2A82807973B89537
sambaPwdLastSet: 1291967553
sambaPwdMustChange: 1294559553

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1
```

Is this correct?

---

