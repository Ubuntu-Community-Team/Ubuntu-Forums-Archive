---
title: "Noob help with writing to folders in Samba Share"
date: 2013-05-17
forum: Server Platforms
---

### Post by chrisavfc93 on 2013-05-17
Hi,
I am a bit of a noob with using Ubuntu to be honest, but I've managed to set up a server containing all our videos, music and pictures and streaming it to various Raspberry Pi's running XBMC and they have been working great. Previously for all the media I've been using Media Companion on windows to download all the relevant information such as thumbnails and espisode info, now I want to continue to do that as I ensure I get the information and pictures I want, but as all the media is on the server I now need to point Media Companion to a network location. 
That all works fine, I can find all the media, only problem is I can't actually write to the folders, as apparently I don't have the write permissions.
I would have thought I have the correct permissions as when trying to access the server from my Windows PC I am asked to log in, I log in with my normal details.
It says root access is needed, which I usually achieve through the sudo command when I'm using VNC or Putty, but I don't know how to do the equivalent on Windows.

I'm struggling to understand why it can't be wrote to as my normal user anyway as I'm using webmin to set up the Samba share and I've set all the folders to 'Read/Write to everyone', so to me that suggests I should be able to write them.

Where am I going wrong?

Thanks,
Chris.

---

### Post by rubylaser on 2013-05-17
Can you provide the output of these two commands?
```
cat /etc/samba/smb.conf
```
and
```
ls -la /path/to/share
```

This will allow us to see the samba share permissions as well as the folder permissions.

---

### Post by prodigy_ on 2013-05-17
> **chrisavfc93 said:**
> It says root access is needed
Samba doesn't care about root (or system accounts in general). So, exactly what error message do you get? Also please post **/etc/samba/smb.conf** from your server.

---

### Post by chrisavfc93 on 2013-05-20
> **rubylaser said:**
> Can you provide the output of these two commands?
```
cat /etc/samba/smb.conf
```
and
```
ls -la /path/to/share
```

This will allow us to see the samba share permissions as well as the folder permissions.

The smb.conf is:
```
 ## Sample configuration file for the Samba suite for Debian GNU/Linux.
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
    read raw = no
    name resolve order = bcast host lmhosts wins
    write raw = no
    socket options = TCP_NODELAY
    workgroup = WORKGROUP
    os level = 20
    encrypt passwords = yes
    winbind trusted domains only = yes
    winbind use default domain = yes
    wins support = true


[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    socket options = TCP_NODELAY
    obey pam restrictions = yes
    map to guest = bad user
    encrypt passwords = true
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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom






[Movies]
    writeable = yes
    create mode = 777
    public = yes
    path = /mnt/sdb/Movies
    directory mode = 777


[TV Shows]
    writeable = yes
    create mode = 777
    public = yes
    path = /mnt/sdb/TV Shows
    directory mode = 777


[Music]
    writeable = yes
    create mode = 777
    public = yes
    path = /mnt/sdb/Music
    directory mode = 777


[Pictures]
    writeable = yes
    create mode = 777
    public = yes
    path = /mnt/sdb/Pictures
    directory mode = 777
```

The share bit is here:
```
 ls: cannot access /path/to/share: No such file or directory
```

Which doesn't look good...

> **prodigy_ said:**
> Samba doesn't care about root (or system accounts in general). So, exactly what error message do you get? Also please post **/etc/samba/smb.conf** from your server.

Posted the smb.conf above.
I can't find the exact error message anywhere that is copyable but the first line says. System.UnauthorisedAccessException.AccessToThePath ... IsDenied.


Sorry about the delay in getting back to you, I've been away, thanks for the help though!

---

### Post by Morbius1 on 2013-05-20
Post the output of this command please:
```
ls -al /mnt/sdb
```

Side question: You seem to be using every possible way there is to make your machine a member of the network:
> name resolve order = bcast host lmhosts wins
wins support = Yes
winbind use default domain = Yes
winbind trusted domains only = Yes
Is this just a home network and if so why have you enabled the winbind directives?

---

### Post by chrisavfc93 on 2013-05-23
> **Morbius1 said:**
> Post the output of this command please:
```
ls -al /mnt/sdb
```

Side question: You seem to be using every possible way there is to make your machine a member of the network:

Is this just a home network and if so why have you enabled the winbind directives?

Here are the results of the command:

```

total 428
drwxr-xr-x  8 root root   4096 Apr  8 20:16 .
drwxr-xr-x  5 root root   4096 Apr 18 20:02 ..
drwx------  2 root root  16384 Sep 16  2012 lost+found
drwxr-xr-x  3 root root  69632 May 14 20:54 Movies
drwxr-xr-x  2 root root 323584 Apr  4 14:20 Music
drwxr-xr-x  3 root root   4096 Mar 30 11:30 Pictures
drwx------  4 root root   4096 Oct 27  2012 .Trash-0
drwxr-xr-x 47 root root   4096 May 14 20:56 TV Shows



```

I'll be honest I don't really know why anything is enabled and disabled I just followed a guide and worked my way through it to get it working.

---

### Post by Morbius1 on 2013-05-23
Um .... If I remember correctly the problem you originally posted was that you couldn't get write access to any of your shares.

All of your shares look like this one:
> [Movies]
    writeable = yes
    create mode = 777
    public = yes
    path = /mnt/sdb/Movies
    directory mode = 777
Yet the permissions look like this:
> drwxr-xr-x  3 root root  69632 May 14 20:54 Movies
Only root can write to that folder regardless of how samba defines the share.

You have to change permissions on the folder to gain write access by a samba guest user:
```
sudo chmod 0777 /mnt/sdb/Movies
```

You can also change ownership to someone other that root and then force the guest to become that user. Or a half dozen other ways but the point is that this is a Linux permissions problem not a Samba problem.

---

### Post by chrisavfc93 on 2013-05-23
> **Morbius1 said:**
> Um .... If I remember correctly the problem you originally posted was that you couldn't get write access to any of your shares.

All of your shares look like this one:

Yet the permissions look like this:

Only root can write to that folder regardless of how samba defines the share.

You have to change permissions on the folder to gain write access by a samba guest user:
```
sudo chmod 0777 /mnt/sdb/Movies
```

You can also change ownership to someone other that root and then force the guest to become that user. Or a half dozen other ways but the point is that this is a Linux permissions problem not a Samba problem.


Ah that did the trick for editing using Windows Explorer, meaning I can edit the names and move stuff easily now.

Thank you very much!

Doesn't solve the problem for scaping the media with the program Media Companion though, still get an error.

For example I get this error
"!!! An error was encountered while trying to add a scraped Actor
Access to the path '\\CORBETTSERVER\Movies\.actors\Christopher_Meloni.tbn' is denied."

All the errors are of this type, they are for each detail, so I guess I need to give this specific Windows program permissions to access and write to the data on the server?

---

