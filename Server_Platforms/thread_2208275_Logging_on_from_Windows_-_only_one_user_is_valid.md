---
title: "Logging on from Windows - only one user is valid"
date: 2014-02-27
forum: Server Platforms
---

### Post by david_brown on 2014-02-27
I'm a newbie and trying to set up a home server on my old PC.  There are several PC's that will connect to the server and require read write access to shared folders. I've managed to create the folders I want to share, and all of the family can log on and use the shared folder. The problem comes with password protected folders. I've set up a couple of shares that have password protection but I can't access them. I log on to the server from Windows 7 , but when I want to log on using another user I have set up on the server, the only user it will allow me to log on with is the one we all use for the non protected shares. 

I've tried logging out of the server with net use in windows to log on with the other user, but it wont allow log on.  When I try to log on to the password protected shares, windows gives me the message that multiple connections on shared resource is not allowed.

I've included my smb.conf below. Any ideas please? Thanks.

The share that need password protection is rozzer and davidtest 

Code
> [COLOR=#000000][FONT=Ubuntu Mono]#======================= Global Settings =======================[/FONT][/COLOR]
[global]

## Browsing/Identification 
###
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

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

# What naming service and in what order should we use to resolve host names

# to IP addresses
   name resolve order = lmhosts host wins bcast
#### Networking ####


## The specific set of interfaces / networks to bind to

# This can be either the interface name or an IP address/netmask;

# interface names are normally preferred
;   interfaces = 127.0.0.0/8 
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes

#### Debugging/Accounting ####

## This tells Samba to use a separate log file for each machine
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

## "security = user" is always a good idea. This will require a Unix account
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
; add group script = /usr/sbin/addgroup --force-badname %


########## Printing ##########

#If you want to automatically load your printer list rather
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


########### Misc ############

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
	printable = yes
	writable = no
	path = /var/spool/samba
	guest ok = no
	create mask = 0700
	comment = All Printers


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
;

[cdrom]
;
   comment = Samba server's CD-ROM
;
   read only = yes
;
   locking = no
;   
   path = /cdrom
;  
   guest ok = yes



# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this
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


[David]


 comment=davids file
 path = /files/public
 browseable = yes
 read only = no


[Movies]
writeable = yes
path = /home/movies


[Rozzer]
revalidate = yes
guest account = ross
valid users = ross
writeable = yes
path = /usr/ross


[davidtest]
 comment = testing
 path = /usr/davidtest
 browseable = yes
 valid users = davidtest



[Davidbackup]
 writeable = yes
 path = /usr/davidbackup
 

[Marybackup]
 writeable = yes
 path = /usr/marybackup[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]

---

### Post by TheFu on 2014-02-27
> **david_brown said:**
> Any ideas please? Thanks.

Use ssh and sftp for access to Linux systems.  Local user permissions are honored that way, no convuluted samba non-standard permissions.

* load openssh-server on the linux "server"; existing linux account credentials work or ssh-keys can be used for much better security
* load fail2ban on the "server" to prevent 1M password attempts a day.
* use putty for terminal/ssh access
* use either winscp or filezilla for scp/sftp access to files

ssh / scp / sftp are secure enough for use over the internet too.

Much easier than samba.

---

### Post by SeijiSensei on 2014-02-27
You asked about this in another thread and got what I believe to be the correct answer.

At least with Win7 clients, you cannot log into remote shares and services from a single machine using multiple usernames.  That's a Windows restriction, not Samba's.  If you cannot log into a share with the same username you used to log into Windows, you need to change the permissions on the share either in Linux or Samba or, possibly, both.

---

### Post by TheFu on 2014-02-27
> **SeijiSensei said:**
> You asked about this in another thread and got what I believe to be the correct answer.

At least with Win7 clients, you cannot log into remote shares and services from a single machine using multiple usernames.  That's a Windows restriction, not Samba's.  If you cannot log into a share with the same username you used to log into Windows, you need to change the permissions on the share either in Linux or Samba or, possibly, both.

I don't believe this is true. I have Win7-HP and Ultimate boxes here that access samba3 shares with different userids and passwords. No domain, just simple workgroups.  Or am I misunderstanding?  The GUI actually has a place to enter both the workgroup\userid and password ... and will ask to save them forever or not.

---

### Post by SeijiSensei on 2014-02-27
I only learned about this issue when I searched for the error David reported in the other thread: [Multiple connections to a server using more than one username are not allowed]("http://social.msdn.microsoft.com/Forums/en-US/aeeb452d-0254-4bc2-a598-20f1f57ee8e0/multiple-connections-to-a-server-or-shared-resource-by-the-same-user-using-more-than-one-user-name?forum=biztalkgeneral").  Another poster in David's thread [confirmed]("http://ubuntuforums.org/showthread.php?t=2207740&p=12939814&viewfull=1#post12939814") this behavior.

Since I rarely run Windows I haven't encountered this problem myself; I'm just reporting what I read.  I wonder what i's the difference between your configurations and the ones which cause the "multiple-connections" error.

---

### Post by TheFu on 2014-02-28
I'm using different logins to different servers - NOT the same server with different logins.  It might be a GUI thing too - I've scripted my "mounts" in Windows and don't use the GUI much.  I know that Microsoft has put features into the GUI tools, but not into the file system - like "libraries" which only work from Exploder and GUI file-choosers, not from the cmd.exe or even the powershell CLI interfaces.

---

### Post by SeijiSensei on 2014-02-28
I'm pretty sure it's the same server/different server issue.  From what I read, you'd see the same problems with commands like "net use".

---

