---
title: "[SOLVED] openLDAP/Samba authentication from XP issue"
date: 2008-06-27
forum: Server Platforms
---

### Post by erolleman on 2008-06-27
I have openLDAP and SAMBA running on ubuntu server 7.10 .  I have samba configured to use ldap as it's database back end. The problem is that when I am on the Windows XP machine and I try to join the samba domain or just try connect to the share with the username and password it just tells me that the username and password is incorrect...  Could someone shed some light on this situation for me?

I'll post config files if necessary.

Thanks.

---

### Post by promodus on 2008-06-28
Try adding the machine first:

```
smbldap-useradd -w machine_name$
```

Then try joining the domain in the typical fashion on your XP setup.

---

### Post by erolleman on 2008-06-28
Thank you for the suggestion.  Unfortunatly that didn't work.  I didn't add the machine account to start with because I thought SAMBA would to it automatically, because of the " add machine script = /usr/sbin/smbldap-useradd -w %u " line added into the smb.conf file.  If it helps you understand my issue a little bit more: I can't authenticate just to access a share either.  The error I get from either trying to access a share or join the SAMBA domain is " Logon failure: unknown user name or bad password. ".  I have linux authentication to openLDAP working fine.  I can create a user then login with ssh or locally on the ubuntu server with that user, so I know that isn't the issue.  The problem seems to be getting SAMBA to authenticate.

Any more insight?

---

### Post by promodus on 2008-06-29
> **erolleman said:**
> Thank you for the suggestion.  Unfortunatly that didn't work.  I didn't add the machine account to start with because I thought SAMBA would to it automatically, because of the " add machine script = /usr/sbin/smbldap-useradd -w %u " line added into the smb.conf file. 

Try that command and see if you have the object sambaSamAccount
and then check to see if you have sambaSID object. Without those two even if you are passing the the correct Username and Password, you will still get the user or password error joining a domain.

It may be an error in my samba configuration that my add machine script isn't doing this automatically. I have not investigated.

> 
 If it helps you understand my issue a little bit more: I can't authenticate just to access a share either.  The error I get from either trying to access a share or join the SAMBA domain is " Logon failure: unknown user name or bad password. ". 


What is your domain name? 
How are you accessing the share?
I'm assuming you get a "connect to yourserver" where you specify the username and password. What are you putting in for the username?

> 
I have linux authentication to openLDAP working fine.  I can create 
a user then login with ssh or locally on the ubuntu server with that user, so I know that isn't the issue.  The problem seems to be getting SAMBA to authenticate.

PAM may be binding to LDAP fine.
Samba may not binding OR it is binding fine AND keep in mind that:
You will be accessing different attributes from different schemas in either authentication from a Linux host versus a Windows host.

> 
Any more insight?

To solve your problem? Yes. 
Some insight as to the account you're using to authenticate from your directory, your smb.conf configuration, and slapd.conf configuration.

Remove any password hashes as necessary.

---

### Post by erolleman on 2008-06-29
Okay, here's the dn entries exactly as they exist in both slapd and smb for my directory admin account:
slapd:  rootdn          "cn=diradmin,dc=test"
        rootpw         {SSHA}EnoWIMQNwMUslbzj+n5xLqiJG/9jjbv 
smb:    ldap admin dn = cn=diradmin,dc=test

I then ran " smbpasswd -w pass " to update the password into samba's secrets file (Yes the password I'm using is " pass ", it's a virtual test environment so it doesn't matter to me if you know the password).

The root account information as created by the smbldap-populate command is:
# root, users, test
dn: uid=root,ou=users,dc=test
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
sambaHomePath: \\ldap1\root
sambaHomeDrive: H:
sambaProfilePath: \\ldap1\profiles$\root
sambaPrimaryGroupSID: S-1-5-21-1895558073-422317946-2241188313-512
sambaSID: S-1-5-21-1895558073-422317946-2241188313-500
loginShell: /bin/false
gecos: Netbios Domain Administrator
sambaLMPassword: B267DF22CB945E3EAAD3B435B51404EE
sambaAcctFlags: [U]
sambaNTPassword: 36AA83BDCAB3C9FDAF321CA42A31C3FC
sambaPwdLastSet: 1214782117
sambaPwdMustChange: 1218670117
userPassword:: e1NTSEF9THJSVW5XQzlQUHBQZllJbmtJOXorckF6b2N0TFpEZzM=

(Password = " pass ")

Computer account ldap info created manually is:
# ldap-xp$, computers, test
dn: uid=ldap-xp$,ou=computers,dc=test
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: posixAccount
cn: ldap-xp$
sn: ldap-xp$
uid: ldap-xp$
uidNumber: 10001
gidNumber: 515
homeDirectory: /dev/null
loginShell: /bin/false
description: Computer
gecos: Computer

When I try to join the domain I used " root " and pass, I also tried " TEST\root " and " pass ".  When I try to just access the shares I go " \\ldap1\netlogon\ " in the run command and it prompts me for username and password to which I try the same combos when trying to join to the domain with no success.

---

### Post by promodus on 2008-07-01
If you are able to post the samba smb.conf and your ldap slapd.conf file I may have a better idea. I'm not sure if SAMBA is binding correctly or not.

It sounds like part of smbldap-tools is working, your ldap server is running. I'm not sure if the proper samba objects are properly put into your [DIT]("http://en.wikipedia.org/wiki/Directory_Information_Tree")

---

### Post by erolleman on 2008-07-01
**SMB.CONF:**

[global]
log level = 10
   workgroup = TEST
   netbios name = ldap1
   server string = TEST Directory Server
   wins support = yes
;   wins server = w.x.y.z
   dns proxy = nonames
   name resolve order = wins bcast hosts lmhosts

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0

####### Authentication #######

;   security = user
add user script = /usr/sbin/smbldap-useradd -m "%u"
ldap delete dn = yes
delete user script = /usr/sbin/smbldap-userdel %u
add group script = /usr/sbin/smbldap-groupadd-p "%g"
delete group script = /usr/sbin/smbldap-groupdel "%g"
add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
add machine script = /usr/sbin/smbldap-useradd -w "%u"
username map = /etc/samba/smbusers
   encrypt passwords = true 
   passdb backend = tdbsam
   obey pam restrictions = no

;   guest account = nobody
;   unix password sync = no
   passwd program = /usr/bin/passwd %u

   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

;   pam password change = no

########## Domains ###########

   domain logons = yes
   domain master = yes
   preferred master = yes
   os level = 35
   logon path = \\ldap1\profiles$\%U
;   logon path = \\%N\%U\profile
   logon drive = H:
   logon home = \\ldap1\%U
   logon script = logon.bat

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

ldap suffix = dc=test
ldap machine suffix = ou=computers,dc=test
ldap user suffix = ou=users,dc=test
ldap group suffix = ou=groups,dc=test
ldap idmap suffix = ou=idmap,dc=test
ldap admin dn = cn=diradmin,dc=test
ldap ssl = no
ldap passwd sync = Yes

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   writable = yes
   create mask = 0700
   directory mask = 0700

[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   writable = no
   share modes = no

[profiles$]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700
   read only = no
   profile acls = yes
   valid users = %U
   admin users = root @"Domain Admins"


**SLAPD.CONF**

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include		/etc/ldap/schema/samba.schema
include		/etc/ldap/schema/misc.schema


pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        8

# Where the dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

# 'backend' directive occurs
backend		bdb
checkpoint 512 30

# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=test"

  rootdn          "cn=diradmin,dc=test"
  rootpw	{SSHA}EnoWIMQNwMUslbzj+n5xLqiJG/9jjbvN

directory       "/var/lib/ldap"

dbconfig set_cachesize 0 20971520 0


dbconfig set_lk_max_objects 1500
dbconfig set_lk_max_locks 1500
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index	objectClass		eq
index	sn,uid,displayname	pres,sub,eq
index	sambaSIDList,uidNumber	eq
index	gidNumber,memberUid	eq
index	sambaSID		eq
index	sambaPrimaryGroupSID	eq
index	sambaDomainName		eq
index	cn,mail,givenname	eq,subinitial
index	default			sub

lastmod         on

# replogfile	/var/lib/ldap/replog

access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
        by dn="cn=diradmin,dc=test" write
	by dn="uid=root,ou=users,dc=test" write
        by anonymous auth
        by self write
        by * none

access to dn.base="" by * read

access to *
        by dn="cn=diradmin,dc=test" write
        by * read

---

### Post by promodus on 2008-07-01
> 
access to attrs=userPassword,shadowLastChange,sambaNTPasswor d,sambaLMPassword


Is there a space in sambaNTPassword, just before the d?

---

### Post by erolleman on 2008-07-01
No there isn't.  When I saw that space after I posted I checked, haha. Some wierd thingy the the post in the forum added.

---

### Post by promodus on 2008-07-02
> 
   encrypt passwords = true 
[COLOR="Yellow"]   passdb backend = tdbsam[/COLOR]
   obey pam restrictions = no

;   guest account = nobody
;   unix password sync = no
[COLOR="SeaGreen"]   passwd program = /usr/bin/passwd %u[/COLOR]

   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

;   pam password change = no


Two things I've noticed:

[COLOR="Yellow"]passdb backend = ldapsam:ldap://ip_or_dns_of_ldap1[/COLOR]

[COLOR="SeaGreen"]/usr/sbin/smbldap-passwd %u[/COLOR]

---

### Post by erolleman on 2008-07-02
So I feel pretty dumb about forgetting the " ldapsam:ldap:// ".
My issue now is that when I try to join the domain I get the error message " The following error occured attempting to joing the domain 'test';  The network path was not found."

I have set up bind and created the corresponding master zone (test) and created a host record for ldap1.  I run " nslookup ldap1 " and it auto appends the .test (I configured the suffix) and resolves fine.  I also tried " nslookup ldap1.test " and " nslookup 192.168.0.253 " which both resolved correctly (I created the reverse lookup zone as well).  I'm not sure where it's failing to find network path.  It even fails when I try to just connect to the share fromt he run command.

Any help?

---

### Post by promodus on 2008-07-02
> 
wins support = yes

Something to try:
On your XP Clients set the WINS server to the IP: 192.168.0.253 (your samba pdc)

---

### Post by erolleman on 2008-07-03
Yeah... I had that setup, but no luck.  Don't suppose you have any more ideas do you?

---

### Post by promodus on 2008-07-03
A couple ideas.
> ldap user suffix = ou=users,dc=test
In your directory, within the **users** OU what users do you have?

When running this command on your server:
```
net user
```

Do you see any users that are from your users OU?

---

### Post by erolleman on 2008-07-11
Okay here's my current status: when I try to join I get the error: "The user name could not be found.".  Wierd thing is that I have no problem authenticating with that same user account to view shares (the user account being " root ").  So I'm stuck once again.  When I do a " net user " I get the following info:
root
nobody
user1

When I do a " net group " I get the following info:
Domain Admins
Domain Users
Domain Guests
Domain Computers
Users

And some ldap information about root, Domain Admins and the machine accound I created manually to see if that will work:

# root, users, test
dn: uid=root,ou=users,dc=test
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
sambaHomePath: \\ldap1\root
sambaHomeDrive: H:
sambaProfilePath: \\ldap1\profiles$\root
sambaPrimaryGroupSID: S-1-5-21-1895558073-422317946-2241188313-512
sambaSID: S-1-5-21-1895558073-422317946-2241188313-500
loginShell: /bin/false
gecos: Netbios Domain Administrator
sambaLMPassword: B267DF22CB945E3EAAD3B435B51404EE
sambaAcctFlags: [U]
sambaNTPassword: 36AA83BDCAB3C9FDAF321CA42A31C3FC
sambaPwdLastSet: 1214782117
sambaPwdMustChange: 1218670117
userPassword:: e1NTSEF9THJSVW5XQzlQUHBQZllJbmtJOXorckF6b2N0TFpEZzM=

# Domain Admins, groups, test
dn: cn=Domain Admins,ou=groups,dc=test
objectClass: top
objectClass: posixGroup
objectClass: sambaGroupMapping
gidNumber: 512
cn: Domain Admins
description: Netbios Domain Administrators
sambaSID: S-1-5-21-1895558073-422317946-2241188313-512
sambaGroupType: 2
displayName: Domain Admins
memberUid: root

# ldap-xp$, computers, test
dn: uid=ldap-xp$,ou=computers,dc=test
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: posixAccount
cn: ldap-xp$
sn: ldap-xp$
uid: ldap-xp$
uidNumber: 10004
gidNumber: 515
homeDirectory: /dev/null
loginShell: /bin/false
description: Computer
gecos: Computer

I hope this is enough info for any samba + openldap guru's to provide some assistance.

Thanks.

---

### Post by promodus on 2008-07-12
Could you 
```
net getlocalsid
```

I'm thinking your domain sid may be too short.

Secondly for your computer object

add 
```
objectClass: sambaSamAccount
```

onces that's added, also add:

sambaSID, sambaAcctFlags and sambaNTPassword

I don't know why smbldap-useradd did not add those.

---

### Post by promodus on 2008-07-12
Sorry your SID should be fine.
"SID is in a standard format (3 32-bit subauthorities preceded by three 32-bit authority fields)." As quoted from:
[http://technet.microsoft.com/en-us/sysinternals/bb897418.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897418.aspx)

I believe your problem is, when trying to join the domain, samba is trying to modify the attributes for ldap-xp$ but since they are not there it says account not found.

It in fact finds the account you use to authenticate, but does not find the account for the machine (ldap-xp$).

---

### Post by erolleman on 2008-07-14
Okay I think I figured out part of the problem I put the computer account (ldap-xp$) into " ou=users,dc=test " and now I get a different error which reads " A device attached to the system is not functioning. "

---

### Post by promodus on 2008-07-14
What do you get when:
```

net lookup name ldap-xp$

```

---

### Post by erolleman on 2008-07-15
I get:

S-1-22-1-10004 1 (User) UNIX USER\ldap-xp$

---

### Post by promodus on 2008-07-16
The SID should be longer.

The output I recieve:
```
S-1-5-21-2077956632-1721461777-1151864052-1001 1 (User) mydomain\computername$
```

Check the attributes associated with this LDAP Object.

---

### Post by erolleman on 2008-07-19
I can't seem to figure out why smbldap-tools doesn't create the proper SID for the computer account.  I works for creating users... Am I missing something?

*I edited the "computersdn" to be "ou=users,dc=test" because samba seems to only look for the account in the users OU and not a separate computers OU.
smbldap.conf:

# Put your own SID. To obtain this number do: "net getlocalsid".
# If not defined, parameter is taking from "net getlocalsid" return
SID="S-1-5-21-1895558073-422317946-2241188313"

# Domain name the Samba server is in charged.
# If not defined, parameter is taking from smb.conf configuration file
# Ex: sambaDomain="IDEALX-NT"
sambaDomain="TEST"

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
slaveLDAP="127.0.0.1"

# Slave LDAP port
# If not defined, parameter is set to "389"
slavePort="389"

# Master LDAP server: needed for write operations
# Ex: masterLDAP=127.0.0.1
# If not defined, parameter is set to "127.0.0.1"
masterLDAP="127.0.0.1"

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
verify="require"

# CA certificate
# see "man Net::LDAP" in start_tls section for more details
cafile="/etc/opt/IDEALX/smbldap-tools/ca.pem"

# certificate to use to connect to the ldap server
# see "man Net::LDAP" in start_tls section for more details
clientcert="/etc/opt/IDEALX/smbldap-tools/smbldap-tools.pem"

# key certificate to use to connect to the ldap server
# see "man Net::LDAP" in start_tls section for more details
clientkey="/etc/opt/IDEALX/smbldap-tools/smbldap-tools.key"

# LDAP Suffix
# Ex: suffix=dc=IDEALX,dc=ORG
suffix="dc=test"

# Where are stored Users
# Ex: usersdn="ou=Users,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for usersdn
usersdn="ou=users,${suffix}"

# Where are stored Computers
# Ex: computersdn="ou=Computers,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for computersdn
computersdn="ou=users,${suffix}"

# Where are stored Groups
# Ex: groupsdn="ou=Groups,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for groupsdn
groupsdn="ou=groups,${suffix}"

# Where are stored Idmap entries (used if samba is a domain member server)
# Ex: groupsdn="ou=Idmap,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for idmapdn
idmapdn="ou=Idmap,${suffix}"

# Where to store next uidNumber and gidNumber available for new users and groups
# If not defined, entries are stored in sambaDomainName object.
# Ex: sambaUnixIdPooldn="sambaDomainName=${sambaDomain},${suffix}"
# Ex: sambaUnixIdPooldn="cn=NextFreeUnixId,${suffix}"
sambaUnixIdPooldn="sambaDomainName=TEST,${suffix}"

# Default scope Used
scope="sub"

# Unix password encryption (CRYPT, MD5, SMD5, SSHA, SHA, CLEARTEXT)
hash_encrypt="SSHA"

# if hash_encrypt is set to CRYPT, you may set a salt format.
# default is "%s", but many systems will generate MD5 hashed
# passwords if you use "$1$%.8s". This parameter is optional!
crypt_salt_format="%s"

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
userSmbHome="\\ldap1\%U"

# The UNC path to profiles locations (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon path'
# directive and/or disable roaming profiles
# Ex: userProfile="\\PDC-SMB3\profiles\%U"
userProfile="\\ldap1\profiles$\%U"

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
mailDomain="test"

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

---

### Post by promodus on 2008-07-20
Discrepancy:
Your smbldap.conf
```

computersdn="ou=users,${suffix}"
```
your smb.conf:
```
ldap machine suffix = ou=computers,dc=test
```

your smbldap.conf
```

idmapdn="ou=Idmap,${suffix}"
```
your smb.conf
```
ldap idmap suffix = ou=idmap,dc=test

```
I would change the case Idmap to idmap in smbldap.conf.

---

### Post by erolleman on 2008-07-21
Thanks, it's working now.  Down right awesome!

---

### Post by scottws on 2008-11-04
Do you mind if I piggyback on this thread?  I'm having a somewhat similar problem.  When I try to join a XP client to a domain run by a openLDAP/Samba server (Ubuntu 8.04), I get "The network path was not found."

Going though the thread here I see I have a few problems:

[LIST=1]
[*]When I do a "net user" or even a "sudo net user," I am prompted for a password.  When I enter either my "root" account's password or the password for cn=admin,dc=sander,dc=local (yes they are different), it says "Could not connect to server 127.0.0.1 Connection failed: NT_STATUS_CONNECTION_REFUSED."  There is a root listing in the LDAP database, but my actual username is "swsander".  "net group" or "sudo net group" result in the same thing.
[*]When I do "sudo net lookup name winxptest$", I get "S-1-22-1-30000 1 (User) UNIX USER\winxptest$"  This was pointed out as a problem on page 2 but I didn't see where this was fixed.
[/LIST]

One thing that might throw a monkey wrench into all this is I have two DNS servers and two Samba servers (though only one is set up as an openLDAP + Samba domain controller... the other one is acting like a simple Samba workgroup file server).

Help!

---

### Post by scottws on 2008-11-04
Here is the "net user" error:

> swsander@userver:~$ sudo net user
Password:
Could not connect to server 127.0.0.1
Connection failed: NT_STATUS_CONNECTION_REFUSED

I don't know what this password could be as there are only three passwords I've used on this box for anybody for anything and none of them are accepted.

**Edit**: *I tried the "net user" command (as root) on my Debian 4.0 Etch Samba file server.  This is a standalone server, not a domain controller, and I built it a few years ago.  Well... the same thing happens on *that* server as well.  I'm starting to think my problem lies somewhere else, but where I have no idea.*

Here is the computer error:

> swsander@userver:~$ sudo net lookup name winxptest$
[sudo] password for swsander:
S-1-22-1-30000 1 (User) UNIX USER\winxptest$

Here are the attributes for the problematic (?) computer account:

**uid=winxptest$,ou=Computers,dc=sander,dc=local**
```

version: 1

# LDIF Export for: uid=winxptest$,ou=Computers,dc=sander,dc=local
# Generated by phpLDAPadmin ( http://phpldapadmin.sourceforge.net/ ) on November 4, 2008 11:55 pm
# Server: My LDAP Server (127.0.0.1)
# Search Scope: base
# Search Filter: (objectClass=*)
# Total Entries: 1

dn: uid=winxptest$,ou=Computers,dc=sander,dc=local
objectClass: top
objectClass: account
objectClass: posixAccount
cn: winxptest$
uid: winxptest$
uidNumber: 30000
gidNumber: 515
homeDirectory: /dev/null
loginShell: /bin/false
description: Computer
gecos: Computer
structuralObjectClass: account
entryUUID: 1735c88e-3ee6-102d-970b-e1cb2170c21b
creatorsName: cn=admin,dc=sander,dc=local
createTimestamp: 20081104175937Z
entryCSN: 20081104175937.978024Z#000000#000#000000
modifiersName: cn=admin,dc=sander,dc=local
modifyTimestamp: 20081104175937Z
entryDN: uid=winxptest$,ou=Computers,dc=sander,dc=local
subschemaSubentry: cn=Subschema
hasSubordinates: FALSE

```


I created that computer account with the command "smbldap-useradd -w winxptest."  I'm not sure what's up, because smbldap-useradd works just fine.

**Edit**: *According to [this link](http://fixunix.com/samba/140308-samba-smbldap-useradd-not-creating-machine-accounts-correct-fashion.html), the correct SID information is generated when the client joins the domain.  I'm thinking I can't get it to join due to some problem related to the problem I'm having with the "net user" and "net group" commands.  What I don't get is I have no trouble with commands like "net getlocalsid," or logging into PhpLDAPadmin and manipulating the database there, or creating user accounts with smbldap-useradd (which can be logged into on the server).*


Oh, and here are the relevant files:

**/etc/samba/smb.conf** (testparm output):
```

swsander@userver:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions

[global]
        workgroup = SANDER
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        passdb backend = ldapsam:ldap://localhost/
        pam password change = Yes
        passwd program = /usr/sbin/smbldap-passwd %u
        passwd chat = *New*password* %n\n *Retype*new*password* %n\n *all*authentication*tokens*updated*
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        add user script = /usr/sbin/smbldap-useradd -m "%u"
        delete user script = /usr/sbin/smbldap-userdel "%u"
        add group script = /usr/sbin/smbldap-groupadd -p "%g"
        delete group script = /usr/sbin/smbldap-groupdel "%g"
        add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
        delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
        set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
        add machine script = /usr/sbin/smbldap-useradd -w "%u"
        logon path =
        domain logons = Yes
        dns proxy = No
        wins support = Yes
        ldap admin dn = cn=admin,dc=sander,dc=local
        ldap delete dn = Yes
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        ldap machine suffix = ou=Computers
        ldap passwd sync = Yes
        ldap suffix = dc=sander,dc=local
        ldap user suffix = ou=Users
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


```


**/etc/smbldap-tools/smbldap.conf**
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
SID="S-1-5-21-2859302911-1785395067-2313358270"

# Domain name the Samba server is in charged.
# If not defined, parameter is taking from smb.conf configuration file
# Ex: sambaDomain="IDEALX-NT"
sambaDomain="SANDER"

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
slaveLDAP="127.0.0.1"

# Slave LDAP port
# If not defined, parameter is set to "389"
slavePort="389"

# Master LDAP server: needed for write operations
# Ex: masterLDAP=127.0.0.1
# If not defined, parameter is set to "127.0.0.1"
masterLDAP="127.0.0.1"

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
verify="require"

# CA certificate
# see "man Net::LDAP" in start_tls section for more details
cafile="/etc/smbldap-tools/ca.pem"

# certificate to use to connect to the ldap server
# see "man Net::LDAP" in start_tls section for more details
clientcert="/etc/smbldap-tools/smbldap-tools.pem"

# key certificate to use to connect to the ldap server
# see "man Net::LDAP" in start_tls section for more details
clientkey="/etc/smbldap-tools/smbldap-tools.key"

# LDAP Suffix
# Ex: suffix=dc=IDEALX,dc=ORG
suffix="dc=sander,dc=local"

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
# Ex: groupsdn="ou=Idmap,dc=IDEALX,dc=ORG"
# Warning: if 'suffix' is not set here, you must set the full dn for idmapdn
idmapdn="ou=Idmap,${suffix}"

# Where to store next uidNumber and gidNumber available for new users and groups
# If not defined, entries are stored in sambaDomainName object.
# Ex: sambaUnixIdPooldn="sambaDomainName=${sambaDomain},${suffix}"
# Ex: sambaUnixIdPooldn="cn=NextFreeUnixId,${suffix}"
sambaUnixIdPooldn="sambaDomainName=${sambaDomain},${suffix}"

# Default scope Used
scope="sub"

# Unix password encryption (CRYPT, MD5, SMD5, SSHA, SHA, CLEARTEXT)
hash_encrypt="SSHA"

# if hash_encrypt is set to CRYPT, you may set a salt format.
# default is "%s", but many systems will generate MD5 hashed
# passwords if you use "$1$%.8s". This parameter is optional!
crypt_salt_format="%s"

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
userSmbHome=

# The UNC path to profiles locations (%U username substitution)
# Just set it to a null string if you want to use the smb.conf 'logon path'
# directive and/or disable roaming profiles
# Ex: userProfile="\\PDC-SMB3\profiles\%U"
userProfile=

# The default Home Drive Letter mapping
# (will be automatically mapped at logon time if home directory exist)
# Ex: userHomeDrive="H:"
userHomeDrive=

# The default user netlogon script name (%U username substitution)
# if not used, will be automatically username.cmd
# make sure script file is edited under dos
# Ex: userScript="startup.cmd" # make sure script file is edited under dos
userScript=

# Domain appended to the users "mail"-attribute
# when smbldap-useradd -M is used
# Ex: mailDomain="idealx.com"
mailDomain="sander.local"

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

```


**/etc/ldap/slapd.conf**
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
suffix          "dc=sander,dc=local"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
# rootdn          "cn=admin,dc=sander,dc=local"

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
access to attrs=userPassword,sambaNTPassword,sambaLMPassword
        by dn="cn=admin,dc=sander,dc=local" write
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
        by dn="cn=admin,dc=sander,dc=local" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=sander,dc=local" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"

```


**/etc/smbldap-tools/smbldap_bind.conf**
```

############################
# Credential Configuration #
############################
# Notes: you can specify two differents configuration if you use a
# master ldap for writing access and a slave ldap server for reading access
# By default, we will use the same DN (so it will work for standard Samba
# release)
slaveDN="cn=admin,dc=sander,dc=local"
slavePw="Simon&garfunkel"
masterDN="cn=admin,dc=sander,dc=local"
masterPw="Simon&garfunkel"

```


**/etc/ldap/ldap.conf**
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
host 127.0.0.1

# The distinguished name of the search base.
base dc=sander,dc=local

# Another way to specify your LDAP server is to provide an
#uri ldapi:///127.0.0.1
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
rootbinddn cn=admin,dc=sander,dc=local

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
# nss_base_XXX          base?scope?filter
# where scope is {base,one,sub}
# and filter is a filter to be &'d with the
# default filter.
# You can omit the suffix eg:
# nss_base_passwd       ou=People,
# to append the default base DN but this
# may incur a small performance impact.
#nss_base_passwd        ou=People,dc=padl,dc=com?one
#nss_base_shadow        ou=People,dc=padl,dc=com?one
#nss_base_group         ou=Group,dc=padl,dc=com?one
#nss_base_hosts         ou=Hosts,dc=padl,dc=com?one
#nss_base_services      ou=Services,dc=padl,dc=com?one
#nss_base_networks      ou=Networks,dc=padl,dc=com?one
#nss_base_protocols     ou=Protocols,dc=padl,dc=com?one
#nss_base_rpc           ou=Rpc,dc=padl,dc=com?one
#nss_base_ethers        ou=Ethers,dc=padl,dc=com?one
#nss_base_netmasks      ou=Networks,dc=padl,dc=com?ne
#nss_base_bootparams    ou=Ethers,dc=padl,dc=com?one
#nss_base_aliases       ou=Aliases,dc=padl,dc=com?one
#nss_base_netgroup      ou=Netgroup,dc=padl,dc=com?one

# attribute/objectclass mapping
# Syntax:
#nss_map_attribute      rfc2307attribute        mapped_attribute
#nss_map_objectclass    rfc2307objectclass      mapped_objectclass

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

```


**/etc/auth-client-config/profile.d/open_ldap**
```

[open_ldap]
nss_passwd=passwd: compat ldap
nss_group=group: compat ldap
nss_shadow=shadow: compat ldap
pam_auth=auth       required     pam_env.so
 auth       sufficient   pam_unix.so likeauth nullok
 auth       sufficient   pam_ldap.so use_first_pass
 auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
 account    sufficient   pam_ldap.so
 account    required     pam_deny.so
pam_password=password   sufficient   pam_unix.so nullok md5 shadow use_authtok
 password   sufficient   pam_ldap.so use_first_pass
 password   required     pam_deny.so
pam_session=session    required     pam_limits.so
 session    required     pam_mkhomedir.so skel=/etc/skel/
 session    required     pam_unix.so
 session    optional     pam_ldap.so

```

---

### Post by scottws on 2008-11-04
Ok.  It's definitely an authentication issue.

If I type the domain as anything but "SANDER," I get a response that the domain controller could not be contacted.  But if I do put "SANDER" for the domain, I get a password prompt for a user with credentials to join PCs to the domain.  So it's seeing the openLDAP+Samba server, but I just can't get anything to authenticate.

No matter what computer name (pre-staged in openLDAP or not) or login credentials I type in, I get...

> The following error occurred attempting to join the domain "SANDER":

The network path was not found.

So it's definitely failing on the login part.  [The guide I'm using](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10) says that the user "root" (who does exist in my openLDAP database somehow) should have the ability to join computers to the domain.  Well it wasn't working.  I tried "smbldap-passwd root" and typing in a new password, but this did not solve the issue.

I'm pulling my hair out over this one!  I've gotten it working before on a previous build (admittedly, Ubuntu 7.10 Gutsy Gibbon instead of Ubuntu 8.04 Hardy Heron).

---

### Post by scottws on 2008-11-04
Ok, I solved it.  It was one of two things:

[LIST=1]
[*]WINS:  I saw another post on the Internet where someone was having a similar problem.  It was actually much older (Samba pre v3 and Windows 2000) but the problem was identical.  Users recommeded he disable WINS.
[*]Samba wasn't started:  After I did "wins support = false" in /etc/samba/smb.conf, I did "sudo /etc/init.d/samba restart" and was greeted with this lovely message:  "start-stop-daemon: warning: failed to kill 5646: No such process."  It seemed to start ok, but I repeated the command just to be sure and it worked ok that time. So it's possible that Samba wasn't running properly this whole time.
[/LIST]

In any case after doing both of these things I was able to join the domain.

---

