---
title: "windows can not access samba share - username case senitivity issue"
date: 2016-02-03
forum: Ubuntu Development Version
---

### Post by Doug S on 2016-02-03
I have been attempting to make samba work on an Ubuntu amd64 server 16.04 I am building.
My windows user account name is "Doug". My Ubuntu user account name is "doug". This appears to be the root issue.

The related segment of the smb.conf man page is copied below:
```
       username level (G)

           This option helps Samba to try and 'guess' at the real UNIX username, as many DOS clients send an all-uppercase username. [COLOR="#FF0000"]By default Samba tries all lowercase[/COLOR], followed by
           the username with the first letter capitalized, and fails if the username is not found on the UNIX machine.

           If this parameter is set to non-zero the behavior changes. This parameter is a number that specifies the number of uppercase combinations to try while trying to determine the
           UNIX user name. The higher the number the more combinations will be tried, but the slower the discovery of usernames will be. Use this parameter when you have strange
           usernames on your UNIX machine, such as AstrangeUser .

           This parameter is needed only on UNIX systems that have case sensitive usernames.

           Default: username level = 0

           Example: username level = 5

```This has always worked for me in the past (I think back to Ubuntu version 6) and currently on my 12.04 and 14.04 servers. Turning the log levels up full gives:

On my 14.04 server:
```
  check_ntlm_password:  authentication for user [Doug] -> [Doug] -> [doug] succeeded
```

On my 16.04 server:
```
  check_ntlm_password: sam authentication for user [Doug] FAILED with error NT_STATUS_NO_SUCH_USER
  check_ntlm_password:  Authentication for user [Doug] -> [Doug] FAILED with error NT_STATUS_NO_SUCH_USER
```

I have searched [https://bugzilla.samba.org/](https://bugzilla.samba.org/) and launchpad for an appropriate bug report, but haven't yet found one.

Does anyone know of some new configuration requirement or whatever?

---

### Post by Doug S on 2016-02-05
Bump?

Adding my smb.conf file:
```
# Smythies.com 2016.02.04
#       samba isn't working due to case sensitive
#       username issues. Try stuff.
#
# Smythies.com 2016.02.02 16.04.
#       start from the new smb.conf file and attempt to
#       merge in older smythies.com specific stuff.
#
# smythies.com 2013.01.09 Force Browse Master.
# smythies.com 2011.04.14 Permissions changes.
# smythies.com 2011.01.06 Attempts to make work properly.
# smythies.com specific edits. 2010.12.31
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = SHOME

# server string is the equivalent of the NT Description field
        server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
#   interfaces = 127.0.0.0/8 eth0
    interfaces = enp2s0

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

# For debuggin only:
#
   log level = 10

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
#   syslog = 0

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
#   server role = standalone server
   server role = classic primary domain controller

# smythies.com: What happened to security = user and
# encrypt passwords = true? Put them back.
   security = user
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
# smythies.com: This makes no sense if security=user. So comment out.
#   map to guest = bad user

# smythies.com: Try this:
   username level = 5

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set
#
# smythies.com: The next line has been put back:
#
   domain logons = yes


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
   logon drive = U:
   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the
# SAMR RPC pipe.
# The following assumes a "machines" group exists on the system
 add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# smythies.com:
#
   domain master = yes

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
#   idmap uid = 10000-20000
#   idmap gid = 10000-20000
   template shell = /bin/bash

# smythies.com: Try putting this back. Makes no difference.
#   winbind enum groups = yes
#   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = no

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0644

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0755

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   read only = yes

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
   guest ok = yes
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = no
   read only = yes
   guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

```

---

### Post by Doug S on 2016-02-17
Bump?

Anybody?

Note: I did get some feedback on the [server e-mail list]("https://lists.ubuntu.com/archives/ubuntu-server/2016-February/007181.html"), but no conclusion yet.

---

### Post by Morbius1 on 2016-02-17
I've never used the "username level" option so I don't know why it no longer works.

Did you ever try a username map?

** Create a file as root: /etc/samba/smbusers
** Add a line to smb.conf in the [global] section pointing to that file:
```
username map = /etc/samba/smbusers
```
** Then add the conversion in /etc/samba/smbusers:
```
doug = Doug
```

Now that user names in Windows can have Microsoft Account names like [email]username@email.com[/email] I don't think "username level" ( based on your description ) would account for that anyway.

---

### Post by Doug S on 2016-02-17
@Morbius1: Thanks for the suggestion. I tried it and it didn't make any difference.

I now think the case sensitivity thing was a red herring.
I now believe my issues stem from there no longer being a libpam-smbpass package (that was definitely present and installed with samba in earlier server daily ISO's).
Anyway, I gave up on "classic primary domain controller" and changed to "standalone server" and it works fine, so far.

---

### Post by Doug S on 2016-02-18
Someone pointed me to [this upstream email]("https://lists.samba.org/archive/samba-cvs/2015-October/111473.html") about libpam-smbpass being deleted. 
I can not do what I have been doing for years the way I have been doing it.... Moving on.

---

