---
title: "anonymous samba logon"
date: 2010-10-11
forum: Server Platforms
---

### Post by eagle00789 on 2010-10-11
i have created 2 shares via the webmin installation on my server. i can not access both of these shares from a windows machine wich should have access to bot.
the trick is that 1 share needs password protection, so only certain users can login to the share. the 2nd share needs guest read/write access. i can't access both shares from any windows machine.
this is my smb.conf file
```
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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    socket options = TCP_NODELAY
    obey pam restrictions = yes
    force group = www-data
    map to guest = bad user
    encrypt passwords = yes
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    writeable = yes
    server string = %h server (Samba, Ubuntu)
    path = /var/www
    unix password sync = yes
    workgroup = WORKGROUP
    os level = 20
    valid users = www-data,paul,pbls,admin,administrator,@adm,@admin,@administrator,@sambashare,@www-data
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = yes
    max log size = 1000
    pam password change = yes

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

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

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
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

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

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
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

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



[Webserver]
    comment = Webserver
    valid users = admin,administrator,www-data,paul,pbls,@www-data,@adm,@admin,@administrator,@sambashare

[usrintra]
    path = /var/www/usrintra


```

---

### Post by luvshines on 2010-10-11
Smb.conf looks severely misconfigured :)

What paths do you want to share ??
What users do you want to enable ??
Which share is public and which is password protected ??

---

### Post by Morbius1 on 2010-10-11
> **luvshines said:**
> Smb.conf looks severely misconfigured :)

What paths do you want to share ??
What users do you want to enable ??
Which share is public and which is password protected ??
Agree 100%.

You have a lot of share specific options in the [global] section which will be the default for your shares unless listed otherwise in the share section itself:
> path = /var/www
valid users = www-data, paul, pbls, admin, administrator, @adm, @admin, @administrator, @sambashare, @www-data
force group = www-data
writeable = yesLet's take the first share:
> [Webserver]
comment = Webserver
valid users = admin,administrator,www-data,...It has no path. I'm not 100% sure but perhaps the "path=/var/www" in the global section will act as the path for that share. What do you think luveshines ?

There certainly doesn't seem to be any guest accessible shares in any event.

I would suggest eliminating the share specific parameters in the [global] section and placing them in their respective share section.

The other oddity if the path to [Webserver] is /var/www is that you are creating a share within a share since [usrintra] is pointing to a child of the [Webserver] share. That's tricky business. I suppose it could be done if it's OK that the users you are allowing into [websever] will also have access to [usrintra].

---

### Post by luvshines on 2010-10-11
> **Morbius1 said:**
> 
Let's take the first share:
It has no path. I'm not 100% sure but perhaps the "path=/var/www" in the global section will act as the path for that share. What do you think luvshines ?



From the man pages, looks like this will act as default path for shares which don't explicitly define any:
```
The [global] section
Parameters in this section apply to the server as a whole,
or are defaults for sections that do not specifically define
certain items.
The letter S indicates that a parameter can be specified in a
service specific section. All S parameters can also be specified
in the [global] section - in which case they will define the
default behavior for all services.
```

Though I haven't give it a try. Will try it tomorrow on the test machines :D

---

### Post by eagle00789 on 2010-10-12
i have made some changes according to your hints and tips:
```
#======================= Global Settings =======================

[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    socket options = TCP_NODELAY
    obey pam restrictions = yes
    map to guest = bad user
    encrypt passwords = yes
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    server string = %h server (Samba, Ubuntu)
    unix password sync = yes
    workgroup = WORKGROUP
    os level = 20
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = yes
    max log size = 1000
    pam password change = yes

#======================= Share Definitions =======================

[Webserver]
        path = /var/www
    comment = Webserver
        writeable = yes
        force group = www-data
    valid users = admin,administrator,www-data,paul,pbls,@www-data,@adm,@admin,@administrator,@sambashare

[usrintra]
        writeable = yes
    path = /var/www/usrintra
        force group = www-data
    read only = no
    guest ok = yes
```Thanks to this code, the usrintra share is now publicly available. Unfortunatly, the Webserver share is still not available. not even by using a username and password. The users (and groups) that need access to that share also need access to the usrintra folder inside the /var/www share, so this isn't a security risk for us.

---

### Post by eagle00789 on 2010-10-28
anybody??

---

### Post by Morbius1 on 2010-10-28
You might want to look at this thread: [http://ubuntuforums.org/showthread.php?t=919951](http://ubuntuforums.org/showthread.php?t=919951)

---

