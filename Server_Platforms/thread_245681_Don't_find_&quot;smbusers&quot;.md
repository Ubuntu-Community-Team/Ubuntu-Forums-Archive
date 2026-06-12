---
title: "Don't find &quot;smbusers&quot;"
date: 2006-08-28
forum: Server Platforms
---

### Post by cyberlayer on 2006-08-28
Hello,

I'm going to be mad...

I'm working with Ubuntu Server (line command).

First time, i mad an installation of samba without problems and i made differents tests.

After i made a second installation but nothing runs like before :cry: 

When the installation is finish, i made this commande :

-sudo -s <password>.
-apt-get update.
-apt-get upgrade.
-apt-get install samba
but at the end i've got this lines :

ParamÃ©trage de samba (3.0.22-1ubuntu3.1) ...
Generating /etc/default/samba...
TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
* Starting Samba daemons...  

I dont know why !

After

-adduser toto.
-smbpasswd -a toto.

But why i dont have anymore the file "smbusers" in my /etc/samba/ ?

This is my current files "smb.conf" i made some change for test.

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = TEST

# server string is the equivalent of the NT Description field
   server string = TEST SAMBA

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
   security = user

#Fichier utilisateurs
 username map = /etc/samba/smbusers

# Emplacement du fichier de mots de passes
   smb passwd file = /etc/samba/smbpasswd

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
  unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

Somebody can help me to know where i made a fault ?

thank you :D

---

### Post by lamego on 2006-08-28
Try reinstalling the package.
The default samba dir should be /etc/samba and not /etc/default/samba as shown on the install message.

---

### Post by cyberlayer on 2006-08-29
Thank you,

But how can i change that ?

I make a "sudo apt-get install samba" and that's all.

After your information i made a "apt-get remove --purge <paquets(s)> and i try another time the same command but it's always the same destination and the same problem.

Please help me ](*,) 

CyberLayer

Same message again :

Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), r                                                                             eturning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), retu                                                                             rning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to chan                                                                             ge password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age),                                                                              returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age),                                                                              returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), retu                                                                             rning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), r                                                                             eturning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), r                                                                             eturning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), retur                                                                             ning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine passwor                                                                             d change), returning 0
 * Starting Samba daemons...                                             [ ok ]

---

### Post by gertmul on 2006-08-29
try to purge and install the samba-common package, if that does not work, look into something simular with mysql where the config files need to be freshly installed at [http://www.ubuntuforums.org/showthread.php?t=242036](http://www.ubuntuforums.org/showthread.php?t=242036)

---

### Post by Krieg on 2006-09-07
smbusers does not exist when you install.   You have to add this line to smb.conf :

```

username map = /etc/samba/smbusers

```

then create the file smbusers with the appropiate contain

---

