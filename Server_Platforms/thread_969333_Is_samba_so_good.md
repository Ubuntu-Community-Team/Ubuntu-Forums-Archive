---
title: "Is samba so good?"
date: 2008-11-03
forum: Server Platforms
---

### Post by Buntubailey on 2008-11-03
I have been spending the last 2 days trying to configure a Samba server on my new ubuntu server 8.04 using webmin, either this really is a troublesome peice of software or I don't know what I am doing, probably the latter!

I have finally managed to get my shares working for certain users in my company giving access to only the folders that I specified for that particular user, this really seems a pain however, I am testing the security from a vista notebook and quite often it takes 3 attempts with the username and password before windows will let me into the share, sometimes 4 attempts, sometimes straight away! why is this, am I doing something obviously wrong? is this a windows vista issue? I have included a copy of my smb.conf below in the hope that somebody may be able to spot something that may be causing me all these problems.


[I]# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	write list = administrator,f,gai,gaidesign,gaimanager,gaisales,mam,mamdesign,mamsales,may,nat,note,paul,pooh,samu,tang,tangsales,ton,@Accounts,@Design,@Directors,@Management,@Sales,@adm,@admin
	force directory mode = 
	map to guest = bad user
	user = administrator,f,gai,gaidesign,gaimanager,gaisales,mam,mamdesign,mamsales,may,nat,note,paul,pooh,samu,tang,tangsales,ton,@Accounts,@Design,@Directors,@Management,@Sales
	passdb backend = tdbsam
	dns proxy = no
	netbios name = SOUTHERN
	writeable = yes
	server string = %h server (Samba, Ubuntu)
	path = /SERVER1
	default = global
	unix password sync = yes
	force create mode = 
	workgroup = WORKGROUP
	os level = 20
	valid users = administrator,f,gai,mam,may,nat,note,paul,pooh,samu,tang,ton,@Accounts,@Design,@Directors,@Management,@Sales,@adm,@admin
	syslog = 0
	security = share
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how nsuccessful authentication attempts are mapped 
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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

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
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

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
;   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0775

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
;   write list = root, @ntadmin

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

















[Accounting]
	comment = Accounting
	valid users = paul,gai,mam,tang,samu,may,@Accounts,@Directors
	invalid users = gaidesign,gaimanager,gaisales,mamdesign,mamsales,note,pooh,ton
	user = paul,gai,mam,tang,samu,may,@Accounts,@Directors
	path = /SERVER1/Accounting
	write list = paul,gai,mam,tang,samu,may,@Accounts,@Directors

[Design]
	valid users = paul,f,nat,ton,pooh,mam,gai,@Design,@Directors
	invalid users = gaidesign,gaimanager,gaisales,mamdesign,mamsales,may,note,samu,tang,tangsales
	user = paul,f,nat,ton,pooh,mam,gai,@Design,@Directors
	path = /SERVER1/Design
	write list = paul,f,nat,ton,pooh,mam,gai,@Design,@Directors

[Management]
	valid users = gai,paul,@Directors,@Management
	invalid users = f,gaidesign,gaimanager,gaisales,mam,mamdesign,mamsales,may,nat,note,pooh,samu,tang,tangsales,ton
	user = gai,paul,@Directors,@Management
	path = /SERVER1/Management
	write list = gai,paul,@Directors,@Management

[Support]
	path = /SERVER1/Support
	write list = f,gai,mam,may,note,paul,pooh,samu,tang,ton,@Accounts,@Design,@Directors,@Management,@Sales
	comment = Support
	valid users = f,gai,mam,may,note,paul,pooh,samu,tang,ton,@Accounts,@Design,@Directors,@Management,@Sales
	create mode = 755
	user = f,gai,mam,may,note,paul,pooh,samu,tang,ton,@Accounts,@Design,@Directors,@Management,@Sales
	directory mode = 755

[Sales]
	comment = Sales
	valid users = paul,gai,mam,tang,note,@directors,@sales
	invalid users = gaidesign,gaimanager,gaisales,mamdesign,mamsales,pooh,samu,tangsales,ton
	user = paul,gai,mam,tang,note,@directors,@sales
	path = /SERVER1/Sales
	write list = paul,gai,mam,tang,note,@directors,@sales[/I]


Hopefully someone can help me out with this issue before I kill myself,

Thanks in advance,

Buntubailey

---

### Post by tasos.kleisas on 2008-11-03
You could take a look at ebox, with it you can configure samba in a matter of minutes.

---

### Post by y@w on 2008-11-03
Samba is usually rock solid once you get it working. Is there anything showing up in the logs when you try to authenticate and it fails the first few times, then lets you in?

On a somewhat related note.. I've found that when beginning with Samba, it's sometimes quicker to learn using something like [Webmin]("http://webmin.com"). It lets you do point-and-click configuration. Learning the config files is beneficial, but sometimes Webmin will show you options you didn't know existed.

---

### Post by deltaprime on 2008-11-03
same with ebox
i prefer it because it has a nicer interface (looks wayyyy better = )  ) and it gives you more hardware options. 
its easy to configure the folders with gedit. 

sudo gedit /etc/samba/smb.conf

on the bottom you will see stuff in [these]
these are the folders the users can be specified below along with the r/w/b options. you can add in more if you know it... 
you can go to the samba homepage and download a pdf which is the official booklet (free) for the samba.conf and everything else samba. 
if you need anything else keep posting

good luck

delt4

---

### Post by bab1 on 2008-11-03
If I may...  The OP has configured Samba via the GUI.  The config files for the "shares" is at /var/lib/samba. They are binary and can't be modified.  To reconfigure, I believe one needs to remove everything via the GUI (the safe way) or delete the appropriate files in /var/lib/samba (who knows which ones??). Then I suggest that the OP either manually config ALL of /etc/samba/smb.conf or use eBox.  eBox is a set of PERL scripts that configure /etc/samba/smb.conf correctly.

> is this a windows vista issue? Vista can be an issue.  The login encryption defaults are improved over XP and Samb a need to be explicitly configed for this. See [[COLOR="Red"]**this**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=954691")

---

### Post by Buntubailey on 2008-11-04
Thanks for all of your responses, just incase anybody else has this issue in future, when I set up the server in my office the next day, everything ran very smoothly and worked how I wanted it to. Obviously a vista issue afterall! But I will definatly try ebox next time and see how that compares to using webmin.

---

