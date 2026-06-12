---
title: "Samba configuration ... strange problems ..."
date: 2010-11-01
forum: Server Platforms
---

### Post by bhalper on 2010-11-01
Last week, I put together a Samba file server for my small Windows network.  With the exception of two minor problems, it almost works correctly...

1. When I'm not logged into the server, only the shares are visible on my Windows computer.  Clicking on the share folder displays an error message. As soon as I log in at the server, the files within the shares become accessible on the Windows box.

2. File transfers between the machines are extremely slow.  Watching the system monitor, there's a brief burst of network activity followed by 10-30 seconds of nothing...on a gigabit network, the effective transfer rate is ~120kbs.  There's no other network activity going on that would account for this behavior.

I'm at a loss as how to logically troubleshoot this.  Any suggestions?

---

### Post by kitplane01 on 2010-11-01
I don't know the answer, but I wonder if you have your home directory mounted with encryption.  If so, I would disable that and try again.

---

### Post by redmk2 on 2010-11-01
> **bhalper said:**
> Last week, I put together a Samba file server for my small Windows network.  With the exception of two minor problems, it almost works correctly...

1. When I'm not logged into the server, only the shares are visible on my Windows computer.  Clicking on the share folder displays an error message. As soon as I log in at the server, the files within the shares become accessible on the Windows box.


Can you ping the server when you are not logged in?  How is the IP address configured on the server?  Just a guess, but I'll bet you are using DHCP to assign the IP address.  You should configure a static IP address for the host to use even if there is no user logged in.   
> 

2. File transfers between the machines are extremely slow.  Watching the system monitor, there's a brief burst of network activity followed by 10-30 seconds of nothing...on a gigabit network, the effective transfer rate is ~120kbs.  There's no other network activity going on that would account for this behavior.


Is this a wireless interface?  This could be a driver issue.

---

### Post by dtfinch on 2010-11-01
Regarding #2:

If you're copying large files, we've had (most recently) bad/old gigabit switches and (long ago) bad/old gigabit network cards and drivers cause this sort of issue. When it happened, the slowness was only in one direction, and there was never any ping loss except under heavy load. Replacing the bad hardware fixed the problem.

If you're copying thousands/millions of little files, Samba can get slow working with very large directories of lots of files, if case sensitivity is disabled and clients are requesting files by other than their exact names. If the folder is larger than Samba's stat cache, it ends up doing a full directory scan for every file lookup whenever there's no exact match, since linux filesystems are generally case sensitive.

edit: I've also had that level of slowness copying files over the network when I had MS Security Essentials running, and temporarily disabling it fixed the issue.

---

### Post by bhalper on 2010-11-01
I'd thought about the possibility that there was an address conflict on the network.  I'd originally set the server up with DHCP, but switched it to a static IP late last week.  There wasn't any change in behavior.  It can be pinged without logging in.   

The entire network is wired, except for a leg that's occasionally used for my laptop.  I'm normally using a hardwired machine.

I did encrypt the home directory when I installed Ubuntu  I'd prefer to keep it that way, but I can try unencrypting it and seeing if that affects anything.  Is there an easy way to do so?  The manual pages I've found all talk about encrypting, not going the other way...

---

### Post by bhalper on 2010-11-01
The bulk of the files are relatively small...docs, spreadsheets, mp3, etc.  The largest are a number of ISO DVD images.  There are somewhere between 300K and 500K files all told, but they're split into several thousand directories.  I doubt if any single directory has over a couple hundred files.

MS Security essentials is turned off...at least it's supposed to be.  I'm using BitDefender 2011 as my AV program.  Think that could be the problem?

---

### Post by redmk2 on 2010-11-01
> **bhalper said:**
> I'd thought about the possibility that there was an address conflict on the network.  I'd originally set the server up with DHCP, but switched it to a static IP late last week.  There wasn't any change in behavior.  It can be pinged without logging in. 

The next step would be to ssh to the server and see if Samba is running.```
sudo ps -ef | grep mbd
```

---

### Post by bhalper on 2010-11-01
Assuming I'm reading this right, it looks like it...

root      1015     1  0 13:08 ?        00:00:00 smbd -F
root      1044     1  0 13:08 ?        00:00:00 nmbd -D
root      1047  1015  0 13:08 ?        00:00:00 smbd -F
root      2966  1015  0 13:39 ?        00:00:00 smbd -F
root      2974  1015  0 13:39 ?        00:00:00 smbd -F
root      3004  1015  0 13:43 ?        00:00:00 smbd -F
root      3007  1015  0 13:44 ?        00:00:00 smbd -F
root      3424  1015  0 14:45 ?        00:00:01 smbd -F
1000      3500  3479  0 14:51 pts/0    00:00:00 grep --color=auto mbd

Would it help if I posted the smb.conf file?  It's a modified version of the sample conf file.

---

### Post by bhalper on 2010-11-01
In case this would help.  I know I should strip out all the unnecessary commented out lines, but (obviously) haven't yet...


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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WRKGRP

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

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = yes



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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
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
   map to guest = bad user

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
   printing = cups
   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
   SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

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
#   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
   valid users = %S

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

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


#  The *** is a replacement for my username

[music]
	path = /home/***/Music
	browsable = yes
	read only = no

[documents]
	path = /home/***/Documents
	browsable = yes
	read only = no

[Software]	
	path = /home/***/Software
	browsable = yes
	read only = no

[Pictures]
	path = /home/***/Pictures
	browsable = yes
	read only = no

[Web_Sites]
	path = /home/***/Web_Sites
	browsable = yes
	read only = no

[Scanned Documents]
	path = /home/***/Scanned_Documents
	browsable = yes
	read only = no

---

### Post by redmk2 on 2010-11-01
> **bhalper said:**
> In case this would help.  I know I should strip out all the unnecessary commented out lines, but (obviously) haven't yet...

Better yet, learn to put it between ```
[ /code] brackets. Like below.> 

[CODE]
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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WRKGRP

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

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = yes



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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
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
   map to guest = bad user

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
   printing = cups
   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
   SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

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
#   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
   valid users = %S

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

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


#  The *** is a replacement for my username

[music]
	path = /home/***/Music
	browsable = yes
	read only = no

[documents]
	path = /home/***/Documents
	browsable = yes
	read only = no

[Software]	
	path = /home/***/Software
	browsable = yes
	read only = no

[Pictures]
	path = /home/***/Pictures
	browsable = yes
	read only = no

[Web_Sites]
	path = /home/***/Web_Sites
	browsable = yes
	read only = no

[Scanned Documents]
	path = /home/***/Scanned_Documents
	browsable = yes
	read only = no
```

---

### Post by redmk2 on 2010-11-01
> **bhalper said:**
> Assuming I'm reading this right, it looks like it...

```
root      1015     1  0 13:08 ?        00:00:00 smbd -F
root      1044     1  0 13:08 ?        00:00:00 nmbd -D
root      1047  1015  0 13:08 ?        00:00:00 smbd -F
root      2966  1015  0 13:39 ?        00:00:00 smbd -F
root      2974  1015  0 13:39 ?        00:00:00 smbd -F
root      3004  1015  0 13:43 ?        00:00:00 smbd -F
root      3007  1015  0 13:44 ?        00:00:00 smbd -F
root      3424  1015  0 14:45 ?        00:00:01 smbd -F
1000      3500  3479  0 14:51 pts/0    00:00:00 grep --color=auto mbd
```

Would it help if I posted the smb.conf file?  It's a modified version of the sample conf file.

Samba is running and has multiple forks.  Meaning you are interacting with it in some way.  Browsing is only one way that you can use Samba.  From the terminal what do you get from this command? ```
smbtree
```

---

### Post by bhalper on 2010-11-01
Hmmm...


```

Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
Enter root's password: 
WRKGRP
	\\SERVER-WORK2   		server-work2 server (Samba, Ubuntu)
		\\SERVER-WORK2\IPC$           	IPC Service (server-work2 server (Samba, Ubuntu))
		\\SERVER-WORK2\Scanned Documents	
		\\SERVER-WORK2\Web_Sites      	
		\\SERVER-WORK2\Pictures       	
		\\SERVER-WORK2\Software       	
		\\SERVER-WORK2\documents      	
		\\SERVER-WORK2\music          	
		\\SERVER-WORK2\print$         	Printer Drivers
		\\SERVER-WORK2\homes          	Home Directories
	\\SERVER-WORK    		
cli_start_connection: failed to connect to SERVER-WORK<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\IBM-MS1        		
cli_start_connection: failed to connect to IBM-MS1<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BILL04         		
cli_start_connection: failed to connect to BILL04<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BILL-LAPTOP2   		
cli_start_connection: failed to connect to BILL-LAPTOP2<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME



```

---

### Post by redmk2 on 2010-11-01
> **bhalper said:**
> Hmmm...


```

Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
Enter root's password: 
WRKGRP
	\\SERVER-WORK2   		server-work2 server (Samba, Ubuntu)
		\\SERVER-WORK2\IPC$           	IPC Service (server-work2 server (Samba, Ubuntu))
		\\SERVER-WORK2\Scanned Documents	
		\\SERVER-WORK2\Web_Sites      	
		\\SERVER-WORK2\Pictures       	
		\\SERVER-WORK2\Software       	
		\\SERVER-WORK2\documents      	
		\\SERVER-WORK2\music          	
		\\SERVER-WORK2\print$         	Printer Drivers
		\\SERVER-WORK2\homes          	Home Directories
	\\SERVER-WORK    		
cli_start_connection: failed to connect to SERVER-WORK<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\IBM-MS1        		
cli_start_connection: failed to connect to IBM-MS1<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BILL04         		
cli_start_connection: failed to connect to BILL04<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BILL-LAPTOP2   		
cli_start_connection: failed to connect to BILL-LAPTOP2<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME



```

Why are you running as root ([COLOR="Red"]Enter root's password:[/COLOR])?  I would use a mortal user for diagnosis as these are the users who will be using the Samba shares; right?

We can try the same thing, but up the debugging with this:```
smbtree -d 4
```

---

### Post by bhalper on 2010-11-01
I didn't think I was...It first asked me for my password, popped up the two unknown parameter lines and then asked me for the root password.  

```

williamhalper@server-work2:~$ smbtree -d 4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WRKGRP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter interfaces = 127.0.0.0/8 eth0
doing parameter bind interfaces only = yes
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter printing = cups
doing parameter printcap name = cups
doing parameter SO_RCVBUF = 8192 SO_SNDBUF=8192
Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
doing parameter socket options = TCP_NODELAY
pm_process() returned Yes
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface eth0 ip=fe80::4261:86ff:fe63:1a6%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.20.90 bcast=192.168.20.255 netmask=255.255.255.0
Enter williamhalper's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=32190 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
nmb packet from 127.0.0.1(137) header: id=3403 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 8000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
nmb packet from 192.168.20.90(137) header: id=17920 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .SERVER-WORK2      hex 075345525645522D574F524B32202020
    answers  10 char ...SERVER-WORK2    hex 0004005345525645522D574F524B3220
    answers  20 char   ...SERVER-WORK   hex 20200304005345525645522D574F524B
    answers  30 char 2    ....__MSBRO   hex 3220202020040001025F5F4D5342524F
    answers  40 char WSE__....WRKGRP    hex 5753455F5F0201840057524B47525020
    answers  50 char         ...WRKGR   hex 20202020202020201D040057524B4752
    answers  60 char P         ...WRK   hex 502020202020202020201E840057524B
    answers  70 char GRP         ....   hex 47525020202020202020202000840000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ................   hex 00000000000000000000000000000000
    answers  a0 char .............   hex 00000000000000000000000000
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=26640 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
found master browser WRKGRP, 192.168.20.90
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
WRKGRP
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=108 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
	\\SERVER-WORK2   		server-work2 server (Samba, Ubuntu)
Connecting to host=SERVER-WORK2
resolve_lmhosts: Attempting lmhosts lookup for name SERVER-WORK2<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name SERVER-WORK2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER-WORK2<0x20>
Connecting to 127.0.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
		\\SERVER-WORK2\IPC$           	IPC Service (server-work2 server (Samba, Ubuntu))
		\\SERVER-WORK2\Scanned Documents	
		\\SERVER-WORK2\Web_Sites      	
		\\SERVER-WORK2\Pictures       	
		\\SERVER-WORK2\Software       	
		\\SERVER-WORK2\documents      	
		\\SERVER-WORK2\music          	
		\\SERVER-WORK2\print$         	Printer Drivers
		\\SERVER-WORK2\homes          	Home Directories
	\\SERVER-WORK    		
Connecting to host=SERVER-WORK
resolve_lmhosts: Attempting lmhosts lookup for name SERVER-WORK<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name SERVER-WORK<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER-WORK<0x20>
resolve_hosts: getaddrinfo failed for name SERVER-WORK [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name SERVER-WORK<0x20>
cli_start_connection: failed to connect to SERVER-WORK<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\IBM-MS1        		
Connecting to host=IBM-MS1
resolve_lmhosts: Attempting lmhosts lookup for name IBM-MS1<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name IBM-MS1<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name IBM-MS1<0x20>
resolve_hosts: getaddrinfo failed for name IBM-MS1 [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name IBM-MS1<0x20>
cli_start_connection: failed to connect to IBM-MS1<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BILL04         		
Connecting to host=BILL04
resolve_lmhosts: Attempting lmhosts lookup for name BILL04<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name BILL04<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BILL04<0x20>
resolve_hosts: getaddrinfo failed for name BILL04 [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name BILL04<0x20>
cli_start_connection: failed to connect to BILL04<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BILL-LAPTOP2   		
Connecting to host=BILL-LAPTOP2
resolve_lmhosts: Attempting lmhosts lookup for name BILL-LAPTOP2<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name BILL-LAPTOP2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BILL-LAPTOP2<0x20>
resolve_hosts: getaddrinfo failed for name BILL-LAPTOP2 [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name BILL-LAPTOP2<0x20>
cli_start_connection: failed to connect to BILL-LAPTOP2<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME

```

---

### Post by redmk2 on 2010-11-01
> **bhalper said:**
> I didn't think I was...It first asked me for my password, popped up the two unknown parameter lines and then asked me for the root password.  

```

williamhalper@server-work2:~$ smbtree -d 4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WRKGRP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter interfaces = 127.0.0.0/8 eth0
doing parameter bind interfaces only = yes
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter printing = cups
doing parameter printcap name = cups
doing parameter SO_RCVBUF = 8192 SO_SNDBUF=8192
Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
doing parameter socket options = TCP_NODELAY
pm_process() returned Yes
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface eth0 ip=fe80::4261:86ff:fe63:1a6%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.20.90 bcast=192.168.20.255 netmask=255.255.255.0
Enter williamhalper's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=32190 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
nmb packet from 127.0.0.1(137) header: id=3403 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 8000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
nmb packet from 192.168.20.90(137) header: id=17920 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .SERVER-WORK2      hex 075345525645522D574F524B32202020
    answers  10 char ...SERVER-WORK2    hex 0004005345525645522D574F524B3220
    answers  20 char   ...SERVER-WORK   hex 20200304005345525645522D574F524B
    answers  30 char 2    ....__MSBRO   hex 3220202020040001025F5F4D5342524F
    answers  40 char WSE__....WRKGRP    hex 5753455F5F0201840057524B47525020
    answers  50 char         ...WRKGR   hex 20202020202020201D040057524B4752
    answers  60 char P         ...WRK   hex 502020202020202020201E840057524B
    answers  70 char GRP         ....   hex 47525020202020202020202000840000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ................   hex 00000000000000000000000000000000
    answers  a0 char .............   hex 00000000000000000000000000
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=26640 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
found master browser WRKGRP, 192.168.20.90
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
WRKGRP
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=108 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
	\\SERVER-WORK2   		server-work2 server (Samba, Ubuntu)
Connecting to host=SERVER-WORK2
resolve_lmhosts: Attempting lmhosts lookup for name SERVER-WORK2<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name SERVER-WORK2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER-WORK2<0x20>
Connecting to 127.0.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
		\\SERVER-WORK2\IPC$           	IPC Service (server-work2 server (Samba, Ubuntu))
		\\SERVER-WORK2\Scanned Documents	
		\\SERVER-WORK2\Web_Sites      	
		\\SERVER-WORK2\Pictures       	
		\\SERVER-WORK2\Software       	
		\\SERVER-WORK2\documents      	
		\\SERVER-WORK2\music          	
		\\SERVER-WORK2\print$         	Printer Drivers
		\\SERVER-WORK2\homes          	Home Directories
	\\SERVER-WORK    		
Connecting to host=SERVER-WORK
resolve_lmhosts: Attempting lmhosts lookup for name SERVER-WORK<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name SERVER-WORK<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER-WORK<0x20>
resolve_hosts: getaddrinfo failed for name SERVER-WORK [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name SERVER-WORK<0x20>
cli_start_connection: failed to connect to SERVER-WORK<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\IBM-MS1        		
Connecting to host=IBM-MS1
resolve_lmhosts: Attempting lmhosts lookup for name IBM-MS1<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name IBM-MS1<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name IBM-MS1<0x20>
resolve_hosts: getaddrinfo failed for name IBM-MS1 [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name IBM-MS1<0x20>
cli_start_connection: failed to connect to IBM-MS1<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BILL04         		
Connecting to host=BILL04
resolve_lmhosts: Attempting lmhosts lookup for name BILL04<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name BILL04<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BILL04<0x20>
resolve_hosts: getaddrinfo failed for name BILL04 [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name BILL04<0x20>
cli_start_connection: failed to connect to BILL04<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BILL-LAPTOP2   		
Connecting to host=BILL-LAPTOP2
resolve_lmhosts: Attempting lmhosts lookup for name BILL-LAPTOP2<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name BILL-LAPTOP2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BILL-LAPTOP2<0x20>
resolve_hosts: getaddrinfo failed for name BILL-LAPTOP2 [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name BILL-LAPTOP2<0x20>
cli_start_connection: failed to connect to BILL-LAPTOP2<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME

```

Comment this line out in the smb.conf file```
bind interfaces only = yes
``` and try again.  The default uses the correct interface according to the running kernel.  The Loopback is definitely not needed.

---

### Post by bhalper on 2010-11-01
Although i'm really not sure how it'll work with DHCP, I created a lmhosts file for the systems that can use a static address.  Here's the current output from smbtree -d 4.  It's still not working the way it should, but I think I'm getting closer...maybe??

```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WRKGRP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter interfaces = 127.0.0.0/8 eth0
doing parameter bind interfaces only = yes
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter printing = cups
doing parameter printcap name = cups
pm_process() returned Yes
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface eth0 ip=fe80::4261:86ff:fe63:1a6%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.20.90 bcast=192.168.20.255 netmask=255.255.255.0
Enter williamhalper's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
getlmhostsent: lmhost entry: 192.168.20.101 BILL04 
getlmhostsent: lmhost entry: 192.168.20.103 IBM-MS1 
getlmhostsent: lmhost entry: 192.168.20.107 SERVER-WORK 
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=14301 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
nmb packet from 127.0.0.1(137) header: id=1209 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 8000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
nmb packet from 192.168.20.90(137) header: id=5001 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .SERVER-WORK2      hex 075345525645522D574F524B32202020
    answers  10 char ...SERVER-WORK2    hex 0004005345525645522D574F524B3220
    answers  20 char   ...SERVER-WORK   hex 20200304005345525645522D574F524B
    answers  30 char 2    ....__MSBRO   hex 3220202020040001025F5F4D5342524F
    answers  40 char WSE__....WRKGRP    hex 5753455F5F0201840057524B47525020
    answers  50 char         ...WRKGR   hex 20202020202020201D040057524B4752
    answers  60 char P         ...WRK   hex 502020202020202020201E840057524B
    answers  70 char GRP         ....   hex 47525020202020202020202000840000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ................   hex 00000000000000000000000000000000
    answers  a0 char .............   hex 00000000000000000000000000
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
getlmhostsent: lmhost entry: 192.168.20.101 BILL04 
getlmhostsent: lmhost entry: 192.168.20.103 IBM-MS1 
getlmhostsent: lmhost entry: 192.168.20.107 SERVER-WORK 
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=24114 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
found master browser WRKGRP, 192.168.20.90
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
WRKGRP
resolve_lmhosts: Attempting lmhosts lookup for name WRKGRP<0x1d>
getlmhostsent: lmhost entry: 192.168.20.101 BILL04 
getlmhostsent: lmhost entry: 192.168.20.103 IBM-MS1 
getlmhostsent: lmhost entry: 192.168.20.107 SERVER-WORK 
name_resolve_bcast: Attempting broadcast lookup for name WRKGRP<0x1d>
nmb packet from 127.0.0.1(137) header: id=13344 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WRKGRP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....Z   hex 0000C0A8145A
Got a positive name query response from 127.0.0.1 ( 192.168.20.90 )
Connecting to host=192.168.20.90
Connecting to 192.168.20.90 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
	\\SERVER-WORK2   		server-work2 server (Samba, Ubuntu)
Connecting to host=SERVER-WORK2
resolve_lmhosts: Attempting lmhosts lookup for name SERVER-WORK2<0x20>
getlmhostsent: lmhost entry: 192.168.20.101 BILL04 
getlmhostsent: lmhost entry: 192.168.20.103 IBM-MS1 
getlmhostsent: lmhost entry: 192.168.20.107 SERVER-WORK 
resolve_wins: Attempting wins lookup for name SERVER-WORK2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER-WORK2<0x20>
Connecting to 127.0.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
		\\SERVER-WORK2\homes          	Home Directories
		\\SERVER-WORK2\music          	
		\\SERVER-WORK2\documents      	
		\\SERVER-WORK2\Software       	
		\\SERVER-WORK2\Pictures       	
		\\SERVER-WORK2\Web_Sites      	
		\\SERVER-WORK2\Scanned Documents	
		\\SERVER-WORK2\IPC$           	IPC Service (server-work2 server (Samba, Ubuntu))
		\\SERVER-WORK2\williamhalper  	Home Directories
	\\SERVER-WORK    		
Connecting to host=SERVER-WORK
resolve_lmhosts: Attempting lmhosts lookup for name SERVER-WORK<0x20>
getlmhostsent: lmhost entry: 192.168.20.101 BILL04 
getlmhostsent: lmhost entry: 192.168.20.103 IBM-MS1 
getlmhostsent: lmhost entry: 192.168.20.107 SERVER-WORK 
Connecting to 192.168.20.107 at port 445
Connecting to 192.168.20.107 at port 139
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
NetShareEnum failed
	\\IBM-MS1        		
Connecting to host=IBM-MS1
resolve_lmhosts: Attempting lmhosts lookup for name IBM-MS1<0x20>
getlmhostsent: lmhost entry: 192.168.20.101 BILL04 
getlmhostsent: lmhost entry: 192.168.20.103 IBM-MS1 
Connecting to 192.168.20.103 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
		\\IBM-MS1\www            	
		\\IBM-MS1\C$             	Default share
		\\IBM-MS1\ADMIN$         	Remote Admin
		\\IBM-MS1\Printer2       	Microsoft XPS Document Writer
		\\IBM-MS1\SharedDocs     	
		\\IBM-MS1\print$         	Printer Drivers
		\\IBM-MS1\IPC$           	Remote IPC
	\\BILL04         		
Connecting to host=BILL04
resolve_lmhosts: Attempting lmhosts lookup for name BILL04<0x20>
getlmhostsent: lmhost entry: 192.168.20.101 BILL04 
Connecting to 192.168.20.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
NetShareEnum failed

```

---

### Post by redmk2 on 2010-11-01
> **bhalper said:**
> Although i'm really not sure how it'll work with DHCP, I created a lmhosts file for the systems that can use a static address.  Here's the current output from smbtree -d 4.  It's still not working the way it should, but I think I'm getting closer...maybe??
...


It won't work with DHCP.  The LMHOSTS file is for fixed IP addresses, just as the /etc/hosts file is a fixed mapping of IP to hostname.  It is not always a bad thing to have failures noted when debugging.  The system tries things in a specific order until it has success.  As long has the hosts it is looking for have a NetBIOS name (COMPUTER NAME) and they respond to the broadcasts the system will work.  The ports that should be open are:```
Port 135/TCP - used by smbd
Port 137/UDP - used by nmbd
Port 138/UDP - used by nmbd
Port 139/TCP - used by smbd
Port 445/TCP - used by smbd

```

---

### Post by redmk2 on 2010-11-01
In addition you should comment this out also```
dns proxy = no

```

---

### Post by bhalper on 2010-11-01
Done.  I also nuked the lmhost file since it didn't seem to make any difference...it's back to the NT_STATUS_BAD_NETWORK_NAME message.

For simplicity's sake, I cleaned the crud out of the smb.conf file:

```

#======================= Global Settings =======================

[global]

   workgroup = WRKGRP
   server string = %h server (Samba, Ubuntu)
;   dns proxy = no
   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   security = user
   encrypt passwords = true
   passdb backend = tdbsam

   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes

   map to guest = bad user

########## Printing ##########

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   create mask = 0775
   directory mask = 0775
   valid users = %S

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[music]
	path = /home/***/Music
	browsable = yes
	read only = no

[documents]
	path = /home/***/Documents
	browsable = yes
	read only = no

[Software]	
	path = /home/***/Software
	browsable = yes
	read only = no

[Pictures]
	path = /home/***/Pictures
	browsable = yes
	read only = no

[Web_Sites]
	path = /home/***/Web_Sites
	browsable = yes
	read only = no

[Scanned Documents]
	path = /home/***/Scanned_Documents
	browsable = yes
	read only = no

```

---

### Post by bhalper on 2010-11-01
It's still running at <150kbs between BILL04 (my Win7 desktop machine) and SERVER-WORK2 (the Ubuntu server).  Files transfer at >10Mbs between BILL04 and SERVER-WORK (my Windows Home Server (aka Win Server 2003) machine).

:(

---

