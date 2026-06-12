---
title: "Couple of samba shares not accessible from Windows"
date: 2011-01-28
forum: Server Platforms
---

### Post by calif99x on 2011-01-28
Hi:

I am running Ubuntu 10.10 and have 5 shares that I have setup for Samba (assume names of share1, ..., share5).  I find that shares(2,3,4) are accessible from my MS Windows system, but the share1 and share5 are listed but Windows gives an error accessing them that I may not have permissions.

I have reviewed the shares, all have the same owner, group, and permissions.

Is this a known Samba bug or configuration issue?  I have gone through the smb.conf file multiple times as well as examining the directories and do not see what the issue might be.

Any suggestions or guidance would be appreciated.

Thanks
Sandeep

---

### Post by CharlesA on 2011-01-28
posting yer smb.conf would help immensely.

---

### Post by calif99x on 2011-02-08
Sorry about the delay; having some weird CPU usage problem that delayed responding.

smb.conf file is attached;

Thanks
Sandeep

---

### Post by CharlesA on 2011-02-08
Just copy/paste it in code tags.

---

### Post by calif99x on 2011-02-09
The file itself is pretty vanilla; I added a workgroup and configured this using Webmin.


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
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	public = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = HOME
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


[Completed1]
	path = /media/Completed/Completed1

[Completed7]
	path = /media/Completed7/completed7

[Completed6]
	path = /media/Completed6/Completed6

[completed5]
	path = /media/completed5/Completed5

[completed3]
	path = /media/Completed3/Completed3
```

---

### Post by kevinthecomputerguy on 2011-02-09
Looks like shares 5 and 7 have upper-case \ lower-case mixups. (capital c's versus lower c's)
 
Lower-case and Upper case counts, try that, and reboot.
 
-Kev

---

### Post by calif99x on 2011-02-10
Shares 3, 5, 6 are accessible without any problem.  It is 1 & 7 that fail to work.  Is there a samba log or other diagnostic that provides more information on why these two fail but the other 3 work fine :confused:?

Thanks
Sandeep

---

### Post by CharlesA on 2011-02-11
Do those folders actually exist?

If they don't exist, you'll get errors.

---

### Post by Morbius1 on 2011-02-11
Sorta sounds like a permissions problem rather than a Samba problem.

Post the output of :
```
ls -al /media/Completed
```And
```
ls -al /media/Completed7
```Either that or you are also using Nautilus-share and the two share definitions conflict. Post the output ( if any ) of the following command:
```
net usershare info --long
```

---

### Post by calif99x on 2011-02-14
The shares were originally created using "share folder" property from Nautilus.  A friend suggested using Webmin as it would be easier to admin and I have been using it since 8.04 without a problem until now.

/media shows the drive names (e.g. apt sdb1  sdc1  sdd1  sde1  sdf1  sdg1  sdh1  sdi1  Ubuntu 10.10 amd64 ) along with the share names.

The output of the commands is:

Sandeep:/media$ ls -al /media/Completed
total 36
drwx------  6 sandeep sandeep  4096 2010-07-31 10:50 .
drwxr-xr-x 19 root    root     4096 2011-02-14 09:37 ..
drwxr-xr-x  6 sandeep sandeep  4096 2010-10-30 00:14 Completed
drwxr-xr-x  6 sandeep sandeep  4096 2010-07-24 20:15 Disk Dump
drwx------  2 root    root    16384 2010-05-17 20:38 lost+found
drwx------  5 sandeep sandeep  4096 2010-05-22 16:57 .Trash-1000


Sandeep:/media$ ls -al /media/Completed7
total 32
drwx------  5 sandeep sandeep  4096 2010-07-03 11:52 .
drwxr-xr-x 19 root    root     4096 2011-02-14 09:37 ..
drwxr-xr-x 30 sandeep sandeep  4096 2010-07-31 14:26 completed7
drwx------  2 root    root    16384 2010-05-17 20:37 lost+found
drwx------  5 sandeep sandeep  4096 2010-07-03 13:24 .Trash-1000


Sandeep:/media$ net usershare info --long
[completed3]
path=/media/Completed3/Completed3
comment=
usershare_acl=Everyone:R,
guest_ok=y

[orig music]
path=/media/Completed2/Backups/orig music
comment=
usershare_acl=Everyone:R,
guest_ok=y

[completed]
path=/media/Completed/Completed
comment=
usershare_acl=Everyone:R,
guest_ok=y

[completed5]
path=/media/completed5/Completed5
comment=
usershare_acl=Everyone:R,
guest_ok=y

[completed4]
path=/media/completed1/Completed4
comment=
usershare_acl=Everyone:R,
guest_ok=y

[completed6]
path=/media/Completed6/Completed6
comment=
usershare_acl=Everyone:R,
guest_ok=y

[completed7]
path=/media/Completed7/completed7
comment=
usershare_acl=Everyone:R,
guest_ok=y

[my pictures]
path=/home/sandeep/Pictures/Photos/My Pictures
comment=
usershare_acl=Everyone:R,
guest_ok=y


Thanks
Sandeep

---

### Post by CharlesA on 2011-02-14
Sounds like you are using a mix between Nautilus share and classic Samba. Can't do that as they conflict.

Use one or the other.

Also the errors you are getting say that there is no directory at the target location.

---

### Post by Morbius1 on 2011-02-14
First, What CharlesA said. Take an example:
Nautilus-share:
> [completed7]
path=/media/Completed7/completed7
comment=
usershare_acl=Everyone:R,
guest_ok=yClassic-share in smb.conf:
> [Completed7]
    path = /media/Completed7/completed7Nautilus share allows read access to guests where Classic-share allows read access only to those who provide a username and password. I'm not sure who wins this battle. Get rid of one or the other.

You do have another problem I think and that's your permissions:
> ls -al /media/Completed7
total 32
drwx------  5 sandeep sandeep  4096 2010-07-03 11:52 .
drwxr-xr-x 19 root    root     4096 2011-02-14 09:37 ..
drwxr-xr-x 30 sandeep sandeep  4096 2010-07-31 14:26 completed7The only user who will ever get access to that folder is sandeep.
```
drwxr-xr-x 30 sandeep sandeep  4096 2010-07-31 14:26 completed7
```That one is OK since it allows others or guests to open the directory.
> drwxr-xr-x 19 root    root     4096 2011-02-14 09:37 ..This one represents /media and it's OK since it also allows everyone access to /media subfolders.
>  drwx------  5 sandeep sandeep  4096 2010-07-03 11:52 .This one represents /media/Completed7 and it is not OK since it prevents anyone other than sandeep to even open the directory to see what's inside.

You need to change permissions on that one:
```
chmod 0755 /media/Completed7
```

---

### Post by calif99x on 2011-02-14
Hi:

I followed the above information and the problem is solved ):P.

I deleted the shares information in smb.conf; updated the permissions on the two problem shares and restarted the smbd.

The Windows system can now access the files.

Thanks for the help; Kudos to all who responded.

Cheers
Sandeep

---

