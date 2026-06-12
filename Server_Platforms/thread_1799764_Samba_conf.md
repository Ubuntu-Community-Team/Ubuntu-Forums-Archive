---
title: "Samba conf"
date: 2011-07-08
forum: Server Platforms
---

### Post by donniezazen on 2011-07-08
If you could please spare a minute and check my smb.conf for security flaw, i would really appreciate it.

Thanks.

```

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
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	netbios name = MyServerName
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = WORKGROUP
	os level = 20
	security = share
	syslog = 0
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
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
   load printers = yes

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
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
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
	printer = HP_Deskjet_F4200_series
	create mask = 0700
	comment = All Printers
	printable = yes
	path = /var/spool/samba
	

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
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


[Home]
	writeable = yes
	path = Pathtomyserverdrive


```

---

### Post by ian dobson on 2011-07-08
Hi,

I can see any problems with your samba configuration apart from the fact that you don't have any "socket options" enabled.

I found that if I set my socket options to  "socket options = TCP_NODELAY SO_RCVBUF=32767 SO_SNDBUF=32767" it increased my throughput by almost 30%

Regards
Ian Dobson

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
And:

security = share

Im pretty sure that disables the need for a password... 
Theres also no permissions configured on the shares, e.g. Home, and that should be restricted to you only. And i cant even be bothered to go throught the documentation, theres too much. Look at sambe documentation, youll find a lot of information that will help you.

---

### Post by ian dobson on 2011-07-08
Hi,

security=share just means that every share needs to have their own security settings, just like the windows option "share level security", rather than using global settings.

Regards
Ian Dobson

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
oh :/ i used to use it and i never got asked for a password :( probably just the way i configured it tho

---

### Post by Morbius1 on 2011-07-08
From [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html) :
> *SECURITY = SHARE* When clients connect to a share level security server, they      need not log onto the server with a valid username and password before      attempting to connect to a shared resource (although modern clients      such as Windows 95/98 and Windows NT will send a logon request with      a username but no password when talking to a security = share      server). Instead, the clients send authentication information      (passwords) on a per-share basis, at the time they attempt to connect      to that share.
Note that smbd *ALWAYS*      uses a valid UNIX user to act on behalf of the client, even in     security = share level security.
As clients are not required to send a username to the server     in share level security, smbd uses several     techniques to determine the correct UNIX user to use on behalf     of the client.
A list of possible UNIX usernames to match with the given     client password is constructed using the following methods :

[LIST]
[*]If the [guest only]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTONLY") parameter is set, then all the other          stages are missed and only the [guest account]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT") username is checked.
[*]Is a username is sent with the share connection          request, then this username (after mapping - see [username map]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP")),          is added as a potential username.
[*]If the client did a previous *logon         * request (the SessionSetup SMB call) then the          username sent in this SMB will be added as a potential username.
[*]The name of the service the client requested is          added as a potential username.
[*]The NetBIOS name of the client is added to          the list as a potential username.
[*]Any users on the [user]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USER") list are added as potential usernames.
[/LIST]

If the *guest only* parameter is      not set, then this list is then tried with the supplied password.      The first user for whom the password matches will be used as the      UNIX user.
If the *guest only* parameter is      set, or no username can be determined then if the share is marked      as available to the *guest account*, then this      guest user will be used, otherwise access is denied.
Note that it can be *very* confusing      in share-level security as to which UNIX username will eventually     be used in granting access.
If it were my server I would change security level back to the default of "USER":
> *SECURITY = USER* This is the default security setting in Samba 3.0.      With user-level security a client must first "log-on" with a      valid username and password (which can be mapped using the [username map]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP")      parameter). Encrypted passwords (see the [encrypted passwords]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ENCRYPTEDPASSWORDS") parameter) can also     be used in this security mode. Parameters such as [user]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USER") and [guest only]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTONLY") if set    are then applied and      may change the UNIX user to use on this connection, but only after      the user has been successfully authenticated.


---

### Post by donniezazen on 2011-07-08
Thanks for the suggestions. I have added the socket values for better performances and changed security = user. I wanted to get it started and then read samba manual in detail. Thanks.

---

### Post by donniezazen on 2011-07-08
And it never asks me passwords for reason i have same username and password for my windows login but my roommate is asked for password.

Man enabling socket have greatly increased speed. Thanks.

---

### Post by donniezazen on 2011-07-08
Is my internet data bandwidth used for transfer over wifi/Lan network? I am nearing my comcast bandwidth usage.

---

### Post by doas777 on 2011-07-08
> **soham_1207 said:**
> Is my internet data bandwidth used for transfer over wifi/Lan network? I am nearing my comcast bandwidth usage.
no, nothing to do with it.

> **soham_1207 said:**
> And it never asks me passwords for reason i have same username and password for my windows login but my roommate is asked for password.

Man enabling socket have greatly increased speed. Thanks.
have you run 'sudo smbpasswd -a <secondusername>' on the server for your roommates account? if not, give it a try. have your roommate on hand to set the password when prompted.

> **ian dobson said:**
> Hi,

I can see any problems with your samba configuration apart from the fact that you don't have any "socket options" enabled.

I found that if I set my socket options to  "socket options = TCP_NODELAY SO_RCVBUF=32767 SO_SNDBUF=32767" it increased my throughput by almost 30%

Regards
Ian Dobson

if you change the 32767's to 65535 you will get an even bigger boost.

---

### Post by ian dobson on 2011-07-08
> **doas777 said:**
> no, nothing to do with it.


have you run 'sudo smbpasswd -a <secondusername>' on the server for your roommates account? if not, give it a try. have your roommate on hand to set the password when prompted.



if you change the 32767's to 65535 you will get an even bigger boost.

In my tests with a gbit lan linux to linux box 32767 gave the highest throughput. For xp to linux over wireless 65535 was faster but as I mainly transfer data from one linux box to another the linux speed is more important.

I now actually have these performance optimisations in my smb.conf

socket options = TCP_NODELAY SO_RCVBUF=32767 SO_SNDBUF=32767 rlimit_max=8192 IPTOS_LOWDELAY SO_KEEPALIVE

write cache size = 262144

and quite often hit 50-60Mbyte/sec transfers.

Regards
Ian Dobson

---

### Post by donniezazen on 2011-07-08
Sorry.

---

### Post by donniezazen on 2011-07-08
> **ian dobson said:**
> 
socket options = TCP_NODELAY SO_RCVBUF=32767 SO_SNDBUF=32767 rlimit_max=8192 IPTOS_LOWDELAY SO_KEEPALIVE

write cache size = 262144

Regards
Ian Dobson


This is optimization for Linux. Right?

---

### Post by ian dobson on 2011-07-08
> **soham_1207 said:**
> This is optimization for Linux. Right?

Yes, most of my transfers are Linux to Linux. The only files that I copy under winodws are small.

Regards
Ian Dobson

---

### Post by donniezazen on 2011-10-05
My transfer rate from windows to ubuntu server is usually 700-1000 KB/s. Is this a standard or too slow? I know their are Gigabit ethernet routers to increase transfer rate 10 folds. Are their Gigabit wireless routers?

Thanks.

---

