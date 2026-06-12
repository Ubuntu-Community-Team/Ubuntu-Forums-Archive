---
title: "New folders read only in Samba file share"
date: 2016-11-30
forum: Server Platforms
---

### Post by alka5eltzer on 2016-11-30
Hi All,

Running Ubuntu Server as a fileserver.

When users create new folders in a directory, others users can not save to it. Its read only. 
As a work around, I'm having to Chmod the new directory.

I use Webmin to look after this fileserver.

Here is my smb.conf file... can a modify this in any way to get it to work?:

```
#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	force directory mode = 777
	map to guest = bad user
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	netbios name = fileserver
	writeable = yes
	server string = Linux Fileserver
	path = /home
	unix password sync = yes
	force create mode = 777
	workgroup = WORKGROUP
	os level = 20
	security = user
	syslog = 0
	create mode = 777
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes
	directory mode = 777

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


[homes]
	writeable = yes








[PaulsDrawings]
	write list = shay,Paul,Brian,Eamonn,Joe,Trevor,Tracy,Colin,carol,David,Mark,PaulS,Terry,derek,jp,@users
	path = /home/PaulsDrawings
	force directory mode = 777
	force create mode = 777
	valid users = shay,Paul,Brian,Eamonn,Joe,Trevor,Tracy,Colin,carol,David,Mark,PaulS,Terry,derek,jp,@users
	public = yes
	create mode = 777
	directory mode = 777

[backup]
	comment = 
	writeable = yes
	path = /backup
	available = yes



[PST]
	comment = 
	writeable = yes
	public = yes
	path = /home/PST
	available = yes

[ToolRoom]
	comment = 
	writeable = yes
	public = yes
	path = /home/ToolRoom
	available = yes









[iso]
	writeable = yes
	valid users = shay,Paul,Brian,Eamonn,Joe,Trevor,"Tool Room",Tracy,Jim,Colin,carol,unity,David,jack,claire,Mark,@users,@sambashare
	create mode = 777
	write list = shay,Paul,Brian,Eamonn,Joe,Trevor,"Tool Room",Tracy,Jim,Colin,carol,unity,David,jack,claire,Mark,@users,@sambashare
	path = /home/iso
	directory mode = 777

[BTU_Archive_7_3_16_SG]
	public = yes
	path = /home/BTU_Archive_7_3_16_SG

[Projects]
	valid users = Brian,Colin,David,Eamonn,Mark,Joe,Joe,Paul,PaulS,Terry,Tracy,carol,shay,derek,jp,@users,@root
	path = /home/Projects
force directory mode = 777
	force create mode = 777
	valid users = shay,Paul,Brian,Eamonn,Joe,Trevor,Tracy,Colin,carol,David,Mark,PaulS,Terry,derek,jp,@users
	public = yes
	create mode = 777
	directory mode = 777

[generalinfo]
	path = /home/generalinfo

```

---

### Post by howefield on 2016-11-30
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by volkswagner on 2016-11-30
Ah, fun with file and share permissions (it can grow very complex in a hurry).

It may be best for you to explain your desired outcome, but I can offer some general advise.

Webmin hasn't been supported by Ubuntu for nearly ten years. I can say from experience, you may
get unexpected results. You are much better off managing via ssh and text editor such as nano.

The short answer is, you're needing "force group" directive. The force group will set group owner
to your specified group, regardless of the users actual default group.

Additionally, it's best to keep your modifications at the share level. When experimenting (trial and error), it's a
good idea to simply create a couple shares and try modifying them with minor changes, restart smbd test, rinse, repeat...

Anyway, I did a fresh install of Ubuntu 16.04 and installed samba. I made a test share and modified little else. Since you
have several mods to your global section, it may be worthwhile to start fresh.

Backup your current file and create a new one with basic info.
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

Copy basic info into a new smb.conf (notice I left out the special share [homes] as I'm not sure how you want to access it.
```
sudo nano /etc/samba/smb.conf
```

```
# Global parameters
[global]
	workgroup = WORKGROUP
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[share]
   comment = test share
   path = /home/samba/test
   valid users = @sambashare, cara
   force group = +sambashare
   write list @sambshare
   read only = no
   guest ok = no
   browseable = yes
   create mask = 0664
   directory mask = 0775

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

```

I'll explain my test share example: "force group = +sambashare" means if a user is part of the group, the created files and folders will be owned by this group.
If the user is not part of the forced group, the users default group will be used (if they have write permissions on the share). If the "@" is substituted for the "+" you
can get users not part of the group and no explicit write permissions with ability to write ([see smb.conf docs]("https://www.samba.org/samba/docs/man/manpages/smb.conf.5.html")) 

I have user eric part of smbusers group. He can read and write to the share and all folders and files created by him will have group set to smbusers.
User cara is not part of smbusers group. She has read access to the share. If I were to manually modify a sub folder with permissions allowing here to write, her default group
would be used when creating new files. Other users part of the smbusers group writing to here same folder would still have smbusers as group owner on new files/folders.

```
eric@ubuntu:/home/samba/test$ ls -alt
total 12
drwxrwxr-x 3 root sambashare 4096 Nov 30 22:26 .
-rw-rw-r-- 1 eric sambashare    0 Nov 30 22:26 docByEric.txt
drwxrwxr-x 2 eric sambashare 4096 Nov 30 22:25 EricWasHere
drwxrwxr-x 3 root sambashare 4096 Nov 30 20:22 ..
```

```
sudo mkdir forCara
sudo chgrp cara forCara
sudo chmod 775 forCara
```

```
eric@ubuntu:/home/samba/test$ ls -al
total 16
drwxrwxr-x 4 root sambashare 4096 Nov 30 22:28 .
drwxrwxr-x 3 root sambashare 4096 Nov 30 20:22 ..
-rw-rw-r-- 1 eric sambashare    0 Nov 30 22:26 docByEric.txt
drwxrwxr-x 2 eric sambashare 4096 Nov 30 22:25 EricWasHere
drwxrwxr-x 2 root cara       4096 Nov 30 22:28 forCara
```

Now log into share as cara and create some stuff...

```
eric@ubuntu:/home/samba/test$ ls -al forCara/
total 12
drwxrwxr-x 3 root cara       4096 Nov 30 22:32 .
drwxrwxr-x 4 root sambashare 4096 Nov 30 22:28 ..
-rw-rw-r-- 1 cara cara          0 Nov 30 22:32 caraDidThis.txt
drwxrwxr-x 2 cara cara       4096 Nov 30 22:32 caraWasHere
```

Notice the group was not as set by force group, but create mask and directory mask are 664 and 775 respectively (as in smb.conf).
Now eric won't be able to write inside \\server\share\forCara due to linux file permissions.

---

