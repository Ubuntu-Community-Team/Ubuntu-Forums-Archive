---
title: "can only login to 1 folder at a time"
date: 2015-04-08
forum: Server Platforms
---

### Post by mick14 on 2015-04-08
HI,

I'm running Ubuntu 14.04 with samba.  I configured the server and samba  with 3 folders.  My win7 machines see the folders on the ubuntu server  fine. How ever I can only login to one folder at a time.  That is to  say: if I login to folder (A) first then the other 2 folders won't let  me login.  If I restart the win machine and login to (B) folder first  them I can't log into (A) or (C).

Any ideas? thanks

---

### Post by volkswagner on 2015-04-08
Can you post your smb.conf?

---

### Post by mick14 on 2015-04-08
volkswagner, thank you. I will post the smb.conf tomorrow the 9th

---

### Post by mick14 on 2015-04-09
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = *******

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <[EMAIL="kahan@informatik.tu-muenchen.de"]<kahan@informatik.tu-muenchen.de>[/EMAIL] for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = [B]*Enter\snew\s*\spassword:* %n\n [B]*Retype\snew\s*\spassword:* %n\n [B]*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

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
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[files]
 comment = all files
 path = /files
 browseable = yes
 read only = no
 valid users = files
 
[ops]
 comment = Operation files
 path = /ops
 browseable = yes
 read only = no
 valid users = ops

[ceo]
 comment = ceo's file
 path = /ceo
 browseable = yes
 read only = no
 valid users = ceo

[WIN-BACKUP]
 comment = Backup drive for all PCs
 path = /media/it/WIN-BACKUP
 browseable = yes
 read only = no
 valid users = it
```

---

### Post by SeijiSensei on 2015-04-10
Does one folder require logging in with a different username than the others?  If so, this is a Windows limitation. Since at least Vista, you [cannot]("https://social.technet.microsoft.com/Forums/windows/en-US/f3ee2c61-a5c7-48b3-a3bf-23ea323da699/connecting-to-multiple-shares-on-a-single-server-with-multiple-credentials-system-error-1219-?forum=itprovistanetworking") log into multiple shares hosted on the same server using different credentials.  The linked article suggests that using the server name for one connection and the server's IP address for another will get around this limitation.

---

### Post by mick14 on 2015-04-10
SeijiSensei,

Thanks for your help.  So I guess I'm going about this all wrong. This is what I thought I could set up with linux and samba.  Have mutltible folders on the linux server. Each folder would have a password.  Is that not the case?

---

### Post by nerdtron on 2015-04-11
> **mick14 said:**
> SeijiSensei,

Thanks for your help.  So I guess I'm going about this all wrong. This is what I thought I could set up with linux and samba.  Have mutltible folders on the linux server. Each folder would have a password.  Is that not the case?

Like Seiji said, there's nothing wrong on your setup. It's because windows "remembers" your credential for the IP samba server that you are connecting to. Then next time you access the server, it uses the stored credentials for that folder, which makes it difficult (impossible) to mount other folders (which have different user/password combination).

To solve the problem, you need to log out your previous session on the folder you first accessed. Then you will be asked again for user/password credential when you click on the other folders.
See here on how to do that: [http://superuser.com/questions/352270/how-to-make-windows-7-log-off-from-samba-shared-drive-manually-or-automatically](http://superuser.com/questions/352270/how-to-make-windows-7-log-off-from-samba-shared-drive-manually-or-automatically)

And to have a workaround on the problem, you should map the samba share as network drives. Don't access the samba share via the IP address or server name on the location bar.

---

### Post by SeijiSensei on 2015-04-11
If you set up "public" shares in Samba, everyone can access them.  Alternatively you can access shares owned by others if you have rights to those shares with your normal username.  What you cannot have is a share that is accessible if you log in as john, and another share simultaneously opened that requires you log in as sue.  If john needs access to that second share, you'll need to set the rights correctly as described here: [https://www.samba.org/samba/docs/using_samba/ch09.html](https://www.samba.org/samba/docs/using_samba/ch09.html).

---

