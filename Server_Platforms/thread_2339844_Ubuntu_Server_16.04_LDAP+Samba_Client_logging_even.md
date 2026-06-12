---
title: "Ubuntu Server 16.04 LDAP+Samba Client logging even Server down"
date: 2016-10-13
forum: Server Platforms
---

### Post by whoami123 on 2016-10-13
Hello everyone,
I installed an Ubuntu server on which I configure LDAP and SAMBA from this source [https://www.unixmen.com/setup-samba-domain-controller-with-openldap-backend-in-ubuntu-13-04/](https://www.unixmen.com/setup-samba-domain-controller-with-openldap-backend-in-ubuntu-13-04/). Now When I joined my Windows Client to the domain it's working but when I log in with the samba user and log out, even if I shutdown the server and restart the client. I can still log in on the client. It seem it's not authenticating from the server every time I tried o log using domain user. How to solve this matter and for the client to always authenticate from the server ? 

------------------------------------------------------------Thank You in Advance----------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------------------------smbldap.conf--------------------------------------------------------------------------------------------------------------------------------

```
# $Id: smbldap.conf 139 2012-08-07 11:11:37Z fumiyas $
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

# Put your own SID. To obtain this number do: "net getlocalsid".
# If not defined, parameter is taking from "net getlocalsid" return
SID="S-1-5-21-1111655423-3830135891-3817771963"

# Domain name the Samba server is in charged.
# If not defined, parameter is taking from smb.conf configuration file
# Ex: sambaDomain="IDEALX-NT"
sambaDomain="EXAMPLE"

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

# Slave LDAP server URI
# Ex: slaveLDAP=ldap://slave.ldap.example.com/
# If not defined, parameter is set to "ldap://127.0.0.1/"
#slaveLDAP="ldap://ldap.example.com/"

# Master LDAP server URI: needed for write operations
# Ex: masterLDAP=ldap://master.ldap.example.com/
# If not defined, parameter is set to "ldap://127.0.0.1/"
masterLDAP="ldap://server.example.com/"

# Use TLS for LDAP
# If set to 1, this option will use start_tls for connection
# (you must also used the LDAP URI "ldap://...", not "ldaps://...")
# If not defined, parameter is set to "0"
ldapTLS="0"

# How to verify the server's certificate (none, optional or require)
# see "man Net::LDAP" in start_tls section for more details
verify="none"

# CA certificate
# see "man Net::LDAP" in start_tls section for more details
cafile="/etc/smbldap-tools/ca.pem"

# certificate to use to connect to the ldap server
# see "man Net::LDAP" in start_tls section for more details
clientcert="/etc/smbldap-tools/smbldap-tools.example.com.pem"

# key certificate to use to connect to the ldap server
# see "man Net::LDAP" in start_tls section for more details
clientkey="/etc/smbldap-tools/smbldap-tools.example.com.key"

# LDAP Suffix
# Ex: suffix=dc=IDEALX,dc=ORG
suffix="dc=example,dc=com"

# Where are stored Users
# Ex: usersdn="ou=Users,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for usersdn
usersdn="ou=Users,${suffix}"

# Where are stored Computers
# Ex: computersdn="ou=Computers,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for computersdn
computersdn="ou=Computers,${suffix}"

# Where are stored Groups
# Ex: groupsdn="ou=Groups,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for groupsdn
groupsdn="ou=Groups,${suffix}"

# Where are stored Idmap entries (used if samba is a domain member server)
# Ex: idmapdn="ou=Idmap,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for idmapdn
idmapdn="ou=Idmap,${suffix}"

# Where to store next uidNumber and gidNumber available for new users and groups
# If not defined, entries are stored in sambaDomainName object.
# Ex: sambaUnixIdPooldn="sambaDomainName=${sambaDomain},${suffix}"
# Ex: sambaUnixIdPooldn="cn=NextFreeUnixId,${suffix}"
sambaUnixIdPooldn="sambaDomainName=${sambaDomain},${suffix}"

# Default scope Used
scope="sub"

# Unix password hash scheme (CRYPT, MD5, SMD5, SSHA, SHA, CLEARTEXT)
# If set to "exop", use LDAPv3 Password Modify (RFC 3062) extended operation.
password_hash="SSHA"

# if password_hash is set to CRYPT, you may set a salt format.
# default is "%s", but many systems will generate MD5 hashed
# passwords if you use "$1$%.8s". This parameter is optional!
password_crypt_salt_format="%s"

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

# Treat shadowAccount object or not
shadowAccount="1"

# Default password validation time (time in days) Comment the next line if
# you don't want password to be enable for defaultMaxPasswordAge days (be
# careful to the sambaPwdMustChange attribute's value)
defaultMaxPasswordAge="45"

##############################################################################
#
# SAMBA Configuration
#
##############################################################################

# The UNC path to home drives location (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon home'
# directive and/or disable roaming profiles
# Ex: userSmbHome="\\PDC-SMB3\%U"
userSmbHome="\\SERVER\%U"

# The UNC path to profiles locations (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon path'
# directive and/or disable roaming profiles
# Ex: userProfile="\\PDC-SMB3\profiles\%U"
userProfile="\\SERVER\profiles\%U"

# The default Home Drive Letter mapping
# (will be automatically mapped at logon time if home directory exist)
# Ex: userHomeDrive="H:"
userHomeDrive="H:"

# The default user netlogon script name (%U username substitution)
# if not used, will be automatically username.cmd
# make sure script file is edited under dos
# Ex: userScript="startup.cmd" # make sure script file is edited under dos
userScript="logon.bat"

# Domain appended to the users "mail"-attribute
# when smbldap-useradd -M is used
# Ex: mailDomain="idealx.com"
mailDomain="example.com"

##############################################################################
#
# SMBLDAP-TOOLS Configuration (default are ok for a RedHat)
#
##############################################################################

# Allows not to use smbpasswd (if with_smbpasswd="0" in smbldap.conf) but
# prefer Crypt::SmbHash library
with_smbpasswd="0"
smbpasswd="/usr/bin/smbpasswd"

# Allows not to use slappasswd (if with_slappasswd="0" in smbldap.conf)
# but prefer Crypt:: libraries
with_slappasswd="0"
slappasswd="/usr/sbin/slappasswd"

# comment out the following line to get rid of the default banner
# no_banner="1"
```



------------------------------------------------------------------------------------------------------------------------smb.conf------------------------------------------------------------------------------------------------------------------------------

```
[global]
    workgroup = EXAMPLE
    netbios name = SERVER

    deadtime = 10

    log level = 1
    log file = /var/log/samba/log.%m
    max log size = 5000
    debug pid = yes
    debug uid = yes
    syslog = 0
    utmp = yes

    security = user
    domain logons = yes
    os level = 64
    logon path =
    logon home =
    logon drive = H:
    logon script =

    passdb backend = ldapsam:"ldap://server.example.com/"
    ldap ssl = off
    ldap admin dn = cn=admin,dc=example,dc=com
    ldap delete dn = no

    ## Sync UNIX password with Samba password
    ## Method 1:
    ldap password sync = yes
    ## Method 2:
    ;ldap password sync = no
    ;unix password sync = yes
    ;passwd program = /usr/sbin/smbldap-passwd -u '%u'
    ;passwd chat = "Changing *\nNew password*" %n\n "*Retype new password*" %n\n"

    ldap suffix = dc=example,dc=com
    ldap user suffix = ou=Users
    ldap group suffix = ou=Groups
    ldap machine suffix = ou=Computers
    ldap idmap suffix = ou=Idmap

    add user script = /usr/sbin/smbldap-useradd -m '%u' -t 1
    rename user script = /usr/sbin/smbldap-usermod -r '%unew' '%uold'
    delete user script = /usr/sbin/smbldap-userdel '%u'
    set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
    add group script = /usr/sbin/smbldap-groupadd -p '%g'
    delete group script = /usr/sbin/smbldap-groupdel '%g'
    add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
    delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
    add machine script = /usr/sbin/smbldap-useradd -w '%u' -t 1

[NETLOGON]
    path = /var/lib/samba/netlogon
    browseable = no
    share modes = no

[PROFILES]
    path = /var/lib/samba/profiles
    browseable = no
    writeable = yes
    create mask = 0611
    directory mask = 0700
    profile acls = yes
    csc policy = disable
    map system = yes
    map hidden = yes
```


----------------------------------------------------------------------------------------------------------ldap.conf------------------------------------------------------------------------------------------------------

```
#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

BASE    dc=example,dc=com
URI    ldap://server.example.com:389

#SIZELIMIT    12
#TIMELIMIT    15
#DEREF        never

# TLS certificates (needed for GnuTLS)
TLS_CACERT    /etc/ssl/certs/ca-certificates.crt
```

---

### Post by darkod on 2016-10-13
That is normal windows behaviour, it caches the credentials. In most cases you can log in even if the server is down.

---

### Post by volkswagner on 2016-10-13
As darkod said, this is normal.

You may be able to change the behavior with group policy, but it's in place for a reason. i think the biggest is for occasions when
domain controller is unavailable, but there's also cases for roaming mobile devices, that aren't always on the network.

There may be more than one setting to modify, but [this link]("https://social.technet.microsoft.com/Forums/sharepoint/en-US/6f9389ab-0f93-4837-aea7-3224ab806396/cached-logon-count-via-group-policy?forum=winserverGP") may get you started.

---

