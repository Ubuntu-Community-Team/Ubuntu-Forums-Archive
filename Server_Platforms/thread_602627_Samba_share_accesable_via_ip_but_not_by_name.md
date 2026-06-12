---
title: "Samba share accesable via ip but not by name"
date: 2007-11-04
forum: Server Platforms
---

### Post by tuckie on 2007-11-04
I've been trying to get samba back up and running after finally upgrading Ubuntu to the newest version, and I am now unable to browse the samba file share running on it by name (via my xp box).  my smb.conf looks as follows:
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
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	wins support = true
	dns proxy = no
	netbios name = nibbler
	server string = %h server (Samba, Ubuntu)
	invalid users = root
	workgroup = HOME
	os level = 20
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

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

# Put a capping on the size of the log files (in Kb).

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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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
   public = no
   writable = no
   create mode = 0700

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
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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


[raid]
	valid users = media,@media
	writeable = yes
	user = media,@media
	public = yes
	path = /mnt/raid

```

The Fileshare I'm trying to connect to is raid.  my samba log shows:

```
[2007/11/04 11:42:56, 1] smbd/service.c:make_connection_snum(1033)
  skynet (192.168.1.2) connect to service raid initially as user media (uid=1001, gid=1001) (pid 16039)
[2007/11/04 11:42:59, 0] smbd/service.c:make_connection(1191)
  skynet (192.168.1.2) couldn't find service ::{2227a280-3aea-1069-a2de-08002b30309d}
[2007/11/04 11:43:04, 1] smbd/service.c:close_cnum(1230)
  skynet (192.168.1.2) closed connection to service raid

```

does anyone have any ideas?

---

### Post by HermanAB on 2007-11-04
For named access to work, you need something that will translate the name to the IP address.

You can either run a BIND server (if you have more than about 5 machines), or you can put the names and numbers in /etc/hosts on every machine. (In windows it is c:\windows\system32\drivers\etc\hosts).

Cheers,

Herman

---

### Post by Nepherte on 2007-11-05
I have exactly the same problem though it is not a raid setup.Worked flawless in 7.04 but after upgrading to 7.10 I can only access them by IP. Didn't find a solution as of yet.

---

### Post by homerj742 on 2007-11-05
> **Nepherte said:**
> I have exactly the same problem though it is not a raid setup.Worked flawless in 7.04 but after upgrading to 7.10 I can only access them by IP. Didn't find a solution as of yet.

Same here, I run a geexbox which saw my shares w/o a problem in 7.04, but after the upgrade -> NADA. Pls help!

---

### Post by conjur3r on 2007-11-06
Guys, a good test would be to see if you can ping the name of your server.  If you can't then there's a problem with name resolutions.  In this case, it cannot convert the name into an IP address.  This is not a samba issue.

---

### Post by Nepherte on 2007-11-06
I can't ping to any of the ubuntu 7.10 machines in my network either from windows or linux machines. Neither can I ping from my ubuntu 7.10 to windows or linux machines. Pinging from windows to windows does work. I always get unknown host. Again ip works.

---

### Post by conjur3r on 2007-11-07
The ability to ping a computer's hostname (netbios name) is a Microsoft Windows feature.  It is apart of WINS.  You'll need to do what HermanAB suggested above.  Here's some more information re implementing a [WINS]("http://en.wikipedia.org/wiki/Windows_Internet_Naming_Service") component in [Samba]("http://www.linuxquestions.org/questions/linux-networking-3/ping-netbios-names-from-linux-samba-271336/").

---

### Post by Brazen on 2007-11-07
My guess is there is some changes in the default WINS config, or maybe the WINS config is broken in the latest Ubuntu/Samba.  You should not be using the latest Ubuntu on a server anyway; this is yet another reason why you stick with the LTS release (currently 6.04 Dapper) on production servers.  My home file server has been running without a hitch now for about a year but it has always had Ubuntu Dapper on it.

---

### Post by n411303 on 2008-06-03
Using Hardy

I am fairly new at this stuff.  I had same problem.  Searching via Google, everyone talks about settings for Ubuntu, Samba etc.  

I discovered my fix by making a change to the Windows Vista client.  This may be obvious to more experienced users, but on the Vista client, I believe, one has to edit the network card config and provide the IP address of a single Ubuntu computer which is acting as WINS server for the LAN.  

Once  my Vista machines were pointed at the WINS server, they could all browse my Samba shares by name instead of just IP address.  This proved to be important to me because Microsoft Access 2007 has an annoying new security habit of not trusting database locations.  You can allow specified network locations as safe but not by IP address.  Once I solved the above problem, I could use a share on the Ubuntu PC by name as where I store my Access databases on my LAN.  Access is now happy.  So am I.  (Also now trying to learn how to use Open Office).

Tom

---

