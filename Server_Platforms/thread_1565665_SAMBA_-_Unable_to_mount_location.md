---
title: "SAMBA - Unable to mount location"
date: 2010-09-01
forum: Server Platforms
---

### Post by Funkey Monkey on 2010-09-01
Q: I want to Share a Folder to my LAN (Mother, Father)

**_Further Requirements:_**
[LIST=1]
[*]Guest (No Password or Username needed to access)
[*]Read-Only
[*]No other files accessible (without me sharing them)
[/LIST]

**_Steps I Have Done:_**
[LIST=1]
[*]Nautilus Sharing -DOES NOT WORK - Right Click <FileToBeShared>
[*]Editing SAMBA Config file - gksu gedit /etc/samba/smb.conf
[/LIST]

**_Testing Setup:_**
[LIST=1]
[*]2 x Ubuntu 10.4 Computer
[LIST]
[*]walter-desktop (Server to Share)
[*]peter-laptop (Client to acces files on the server)
[/LIST]
[*]No Firewalls
[*]Able to Ping each other
[/LIST]

**_My smb.conf file:_**
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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = walter-desktop

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
   guest account = nobody

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
   usershare allow guests = yes

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

wins support = no
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


[public]
        comment = Public Share of Walter
        path = /home/walter/Public
        browsable = yes
        read only = no
        guest only = yes
        guest ok = yes

```

**_Permisson of the File to be Shared:_**
```
walter@walter-desktop:~$ ls -l
drwxrwxrwx 3 walter walter  4096 2010-09-01 14:59 Public
```

**_Resources I have consulted:_**
[LIST]
[*][https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba#Private%20and%20public%20shares%20in%20same%20config")
[*][http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")
[/LIST]

**_The Error I still receive:_**
Unable to Mount Location - Failed to mount Windows share
[ATTACH]168151[/ATTACH]

[SIZE="5"][COLOR="Blue"]**Please be so kind as to help me, I don't know what I am doing wrong!!!**[/COLOR][/SIZE]

---

### Post by Funkey Monkey on 2010-09-12
BUMP with Hope. Please help me share some files to guests on my lan.

---

### Post by Morbius1 on 2010-09-12
What is the output of the following command please:
```
net usershare info
```

---

### Post by kgatan on 2010-09-12
If i understood correctly the share is working but you cant mount it from the other machine?

If so the i think the problem is usage permission. You dont have access on the using machine to make mounts.

Try mounting from command line instead using this,

```

sudo mount -t cifs //netbiosname/public /media/sharename -o guest,iocharset=utf8 

```Where netbiosname is ip of sharing machine and /media/sharename is your moint point.

---

### Post by Artyom7 on 2010-09-13
Hi,
I have had the same problem for quite some time now. I tried troubleshooting it myself for two weeks, with no luck.
i kept getting this error in my smbd log file (/var/log/samba/log.smbd):
```

[2010/09/10 20:27:35,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service library, path /media/home/shared

```

So i decided to reinstall everything from scratch, thinking that might solve my problem.
I had posted here before reinstalling the server:
[http://ubuntuforums.org/showpost.php?p=9829610&postcount=441]("http://ubuntuforums.org/showpost.php?p=9829610&postcount=441")


I have a simple home network setup with DHCP. IP addresses are being assigned by the router.
I have one desktop running ubuntu server 10.04 64 bit.
I have 3 laptops which connect to the network using wifi. Two of the laptops are running on ubuntu 10.04 64 bit, and the third one is windoze 7.

I want to be able to access certain folders on my server so that  can schedule automatic backups.

I started off with a clean install, and no updates ( the last time i ran updates, i could not longer login to my box ).

this is my current smb.conf file:

```

[global]

workgroup = WORKGROUP
netbios name = shamrock
security = share
name resolve order = lmhosts wins bcast host
smb ports = 139

[library]
comment = media library
path = /media/ext320/home/shared
browseable = yes
read only = yes
guest ok = yes

```

When i try accessing the share, i am presented with a password dialog box. This is a problem, since the security is set to share, and guest ok = yes.
Even then, I added a user named pria using useradd and smbpasswd. 
the user is a member of the group homeuser.
the share ownership has been set to 0755 to pria:homeuser.

i cannot login with the user pria. The password does not get accepted. when i log in with the administrator account, i get the error " unable to mount windows share ".

when i check the log, i see the same line: 
```

canonicalize_connect_path failed for service library, path /media/ext320/home/shared

```

what is canonicalize_connect_path? why does it fail?
Why am i being asked for a login / password ?

Thank you.

---

### Post by Morbius1 on 2010-09-13
Artyom7, you have a completely different problem than the original poster or at least you are running in a completly different mode.
> [global]  
workgroup = WORKGROUP
netbios name = shamrock 
security = share 
name resolve order = lmhosts wins bcast host 
smb ports = 139The standard smb.conf has security set to USER, the "smb ports = 139" should be commented out, and if that's the extent of your [global] section you have at a minimum no way of allowing guest access because the following line is missing:
```
map to guest = bad user
```You have also rearranged the name resolve order to put "wins" higher up on the resolve order. You either have a WINS server on your network ( but you havent specified where the wins server is in smb.conf ) or you have winbind installed which implies you are part of a Windows Active Directory network.

All in all I think your best bet is to start another topic in the Server portion of the forums.

---

### Post by Artyom7 on 2010-09-13
thanks for your response morbius.
i will go through the documentation for smb.conf once again and see what im missing. I thought keeping it simple will make it easier to figure out what's going on.



> **Morbius1 said:**
> You have also rearranged the name resolve order to put "wins" higher up on the resolve order. You either have a WINS server on your network ( but you havent specified where the wins server is in smb.conf ) or you have winbind installed which implies you are part of a Windows Active Directory network.


i do have winbind installed but i have no idea what it is or what it does ( time for google ).

A new thread? So is this a samba problem or a server problem?

---

### Post by Artyom7 on 2010-09-14
hey!
i am glad to inform everyone that i managed to solve the whole sharing issue.

Its such a stupid thing that i feel really dumb for not having noticed it.
The path to the shares was /media/ext320/home/share
the directory ext320 had permissions set to 0700!!  ](*,)
so i set it to 755 and now its working!

I didnt even bother to check it cos i thought that all one had to worry about was the permissions on the actual shared folder, and not the entire path.

anyways, its all working now, so i guess no need for a new thread
phew....

---

### Post by Funkey Monkey on 2010-09-14
> **Morbius1 said:**
> What is the output of the following command please:
```
net usershare info
```

```
walter@walter-desktop:~$ net usershare info
[music_walter]
path=/home/walter/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

walter@walter-desktop:~$
```

> **kgatan said:**
> ```

sudo mount -t cifs //netbiosname/public /media/sharename -o guest,iocharset=utf8 

```Where netbiosname is ip of sharing machine and /media/sharename is your moint point.

```
peter@peter-laptop:~$ sudo mkdir /media/sharetest
[sudo] password for peter: 
peter@peter-laptop:~$ sudo mount -t cifs //10.0.0.11/public /media/sharetest/ -o guest,iocharset=utf8
mount: wrong fs type, bad option, bad superblock on //10.0.0.11/public,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

peter@peter-laptop:~$ sudo mount -t cifs //10.0.0.11/home/walter/Music /media/sharetest/ -o guest,iocharset=utf8
mount: wrong fs type, bad option, bad superblock on //10.0.0.11/home/walter/Music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

peter@peter-laptop:~$ sudo mount -t cifs //walter-desktop/home/walter/Music /media/sharetest/ -o guest,iocharset=utf8
mount: wrong fs type, bad option, bad superblock on //walter-desktop/home/walter/Music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

peter@peter-laptop:~$
```


> **Artyom7 said:**
> ```
...error in my smbd log file (/var/log/samba/log.smbd):
[CODE]
[2010/09/10 20:27:35,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service library, path /media/home/shared

```

```
[2010/09/13 18:39:10,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/13 18:39:10,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/09/13 18:39:10,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/09/13 18:39:11,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/13 18:39:13,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/13 18:39:13,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
```

[SIZE="5"][COLOR="Blue"]**Still no luck.**
Any other ideas, I can try?[/COLOR][/SIZE]

---

### Post by robsablah on 2010-09-19
bump - same issue - also tired chmod 755 

net user share info - nothing

im at my end ...please help


robert@WATTSRV:~$ net usershare info
robert@WATTSRV:~$ sudo net usershare info
robert@WATTSRV:~$ net usershare info
robert@WATTSRV:~$ 

> 
[global]

usershare owner only = false

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
# wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
; interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself. However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
; bind interfaces only = yes

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
# syslog only = no

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

# You may wish to use password encryption. See the section on
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
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supd$

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
map to guest = bad user

============Misc================
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yes

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
; comment = Home Directories
; browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
; read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
; create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
; directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
; valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yes
; guest ok = yes
; read only = yes
; share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700

[printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0777
writeable = yes

#[Print drivers]
# comment = drivers for the printers
# browseable = yes
# path = /media/Elements/software/drivers/printers
# guest ok = yes
# read only = yes

[software]
comment = software
browseable = yes
path = /media/Elements/software
guest ok = yes
read only = yes
write list = robert

[recently downloaded]
comment = recently downloaded
browseable = yes
path = /media/5/recently downloaded
guest ok = yes
read only = yes
write list = robert

[dropbox]
comment = your change to contribute - put stuff here!
browseable = yes
path = /media/5/dropbox
guest ok = yes
read only = no
writable = yes
create mask = 0777

[New Music]
comment = Music
browseable = yes
path = /media/Elements/music
guest ok = yes
read only = yes
write list = robert

[Music]
comment = Music
browseable = yes
path = /media/5/music
guest ok = yes
read only = yes
write list = robert

[drives]
comment =
browseable = no
path = /media/
guest ok = no
read only = yes
write list = robert 



---

### Post by delphini on 2010-09-19
Hmm... was having similar problems with my samba server, fiddled with it for a long time and am not exactly sure what got it working in the end. 

My net usershare info output was exactly the same as FunkyMonkey's. 
But anyway some differences in my smb.conf file to the posted ones (this are just main parts of it):
```

[global]

## Browsing/Identification ###

    netbios name = UBUNTU-SERVER
# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
    username map = /etc/samba/smbusers
    name resolve order = lmhosts host bcast wins

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
    interfaces = lo, wlan0, eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
    bind interfaces only = yes

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
    security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
  ; encrypt passwords = true
  ; suppose you wouldn't need it for your guest access?
    null passwords = true

 *#the equivalent of your 'public' folder*
[MyFiles]  
    path = /media/samba/
    read only = no
    create mask = 0644
    force user = MyCurrentLoginUsername

```You can also install the useful system-config-samba GUI tool and check your permissions & visibility there (after right-clicking on the relevant folder to enable sharing under properties)
> 
sudo apt-get install system-config-samba
I think maybe the last step which helped get it working for me might also be changing my firewall settings,
i.e. had to allow for SMB ports 137, 138, 139, 445 
Or it might have been a spurious ' typo I missed for hours :)

---

### Post by robsablah on 2010-09-20
also - if it helps

reenabled the auth share
 - attempted to login - password box appears - does not auth
reset auth smb password
 - sudo smbpassword USER
auth shares work
guest does not work

new issue
 - guest not able to access shares
lol

---

