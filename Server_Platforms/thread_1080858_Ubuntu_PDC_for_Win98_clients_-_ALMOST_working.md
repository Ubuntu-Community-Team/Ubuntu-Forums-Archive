---
title: "Ubuntu PDC for Win98 clients - ALMOST working"
date: 2009-02-25
forum: Server Platforms
---

### Post by kennsj on 2009-02-25
I am setting up an Ubuntu Server box to act as PDC, file and print server for 16 Windows 98 client workstations in a school IT lab. Through reading a whole lot of documentation and forum posts, I have been able to get the server set up to the point where a test account is able to log in with password verification, and map network shares manually with 100% success.

What is NOT happening is that the logon.bat (logon.cmd by default in Samba) is not being read by the client, so the home directory and shares are not automatically mounted at login.

Here's my smb.conf...

```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ICTROOM

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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = false

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
   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
   logon drive = H:
   logon home = \\ictroomserver\studentfiles\home\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
   logon script = logon.bat

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u

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
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
   comment = Network Logon Service
   path = /srv/samba/netlogon
   guest ok = yes
   read only = yes
   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700

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
```

You might notice that I've deactivated network password encryption.  This is to simplify communication between the clients and the server, and doesn't matter too much because this is a subnet with firewall protection on the school's main internet gateway.

You might also notice that I've configured the user home directories to be in subdirectory of "studentfiles". "studentfiles" is a partition on a second, larger HDD, mounted as a directory.

If you have any ideas, I'd really like to get this working.  Thanks in advance.

---

### Post by kennsj on 2009-02-26
I have tweaked my smb.conf some more, but still get exactly the same result.  Here are the active lines from my smb.conf...

```
[global]
	workgroup = ICTROOM
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Entersnews*spassword:* %nn *Retypesnews*spassword:* %nn *passwordsupdatedssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u
	logon script = logon.bat
	logon drive = H:
	logon home = \\ictroomserver\studentfiles\home\%U
	domain logons = Yes
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0700
	directory mask = 0700
	browseable = No

[netlogon]
	comment = Network Logon Service
	path = /srv/samba/netlogon
	guest ok = Yes
	share modes = No

[profiles]
	comment = Users profiles
	path = /home/samba/profiles
	create mask = 0600
	directory mask = 0700
	browseable = No

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

In the log file, I get the following recurring error...
> [2009/02/27 12:00:36,  1] winbindd/idmap_tdb.c:idmap_tdb_alloc_init(371)
  idmap uid range missing or invalid
  idmap will be unable to map foreign SIDs
[2009/02/27 12:00:36,  0] winbindd/idmap.c:idmap_alloc_init(831)
  ERROR: Initialization failed for alloc backend, deferred!

Endless Google and forum searching, and no solution!  I really need some help on this.  Why won't Windows read the logon script??  ](*,)


**SOLUTION:** I had to give read permissions to all users on logon.bat, proving that the most obvious solution is usually the correct one (and the one we usually dismiss or forget about).

---

### Post by jimv on 2009-02-27
I have no idea about your problem, but I have a question.  Why do you guys have a Windows 98 lab?

---

### Post by kennsj on 2009-02-27
Well, problem's solved now, anyway.

The reason we have a Windows 98 lab is because our computers are all hand-me-downs from a bigger school nearby, and they couldn't run anything better.

Thinking of putting Ubuntu on them dual boot, so the students can have a look at an open source OS, but it runs kind of slow.

---

### Post by green91 on 2009-02-27
How fast is your server? You could possibly setup a terminal server and use the 98 machines as clients.. much easier to maintain too!

---

### Post by Thirtysixway on 2009-02-28
You could try using Xubuntu for low-resource machines.  Or if you could get your hands on free licenses, windows 2000.  At least it's still in extended support.

But hey, if windows 98 is what you have, then fine with me.  I just see an issue with viruses and malware.

---

### Post by kennsj on 2009-03-01
Thanks for the suggestions, and your concern.

On the Win98 clients, I've got AVG Free virus protection installed, and now that I've got the Ubuntu domain controller up and running, I will be limiting usage options on the workstations so there's no chance of students installing or running something which may contain malware or viruses.

I will try Xubuntu out on the test client tomorrow.

@green91:
Do you mean having the Win98 machines as software clients (i.e. set them up to load their apps from the server)?  It's something I can try out, but I don't know that it'll make a lot of difference.

The server is a Pentium 4 with 1.9G RAM.  The workstations are P3 Celeron equivalents with 192M of RAM.  Sorry for the vague specs, but I'm not at work right now.

---

