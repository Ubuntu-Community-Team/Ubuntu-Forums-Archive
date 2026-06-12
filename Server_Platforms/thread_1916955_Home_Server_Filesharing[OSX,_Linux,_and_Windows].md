---
title: "Home Server Filesharing[OSX, Linux, and Windows]"
date: 2012-01-29
forum: Server Platforms
---

### Post by FaceTheDream on 2012-01-29
Hey,
So I'm new to the forum, so I apolgize if this is in the wrong section, or there is a similar topic. 

I recently purchased a machine, and now its running Ubuntu 11.10 [64 bit] anyways, I want to basically host all my files on there so my family can access the files based on their privileges. I have 4 machines with 4 users, one is running OSX, and the other 3 are windows. The server is Linux obviously. Now I'm having trouble picking a file transfer format that will suit the three operating systems. I have AFP for my mac and it runs flawlessly so far (Netatalk + Avahi). But the other 3 users, I want there to be restrictions, so lets say my children don't have access to admin stuff, and sensitive documents(work related). Regardless, I've tried PFTD i believe it was and I'm still trying to grasp how to configure it, so on the windows machines its basically another drive where they can Upload/Download to the files. 

If anyone can help that would be most appreciated. 

FaceTheDream.

---

### Post by TheFu on 2012-01-29
To share files with Windows PCs on a secure LAN, the best answer is probably SAMBA.  Install this on your Linux system and setup local userid/passwords that match the passwords their accounts have on Windows. In this way you can provide each user with access to a "HOME" on the Linux machine separate from each other.  There are many sets of instructions for setting up and using samba.    [https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html) may help. 

Further, OSX can access this same file sharing.

You can setup sharing where everyone has access to the same file area(s) and/or each user has private file areas. Both are possible and available simultaneously.

---

### Post by FaceTheDream on 2012-01-29
Okay,

I should have said that I had tried Samba before using the GUI interface & tried just the command-line version too. So I set up my music folder to be accessed by two people in the network, and so when I access it on Win 7 Pro, I get the credentials popping up, so I log in with the account I let access the account with the password supplied. So now heres where it starts to act up, so I get access to the server and I see the 3 folders that I allowed to be shared, only one accessible by the user. So when he tries to open the Music folder, after a terribly long wait, he gets an 'access denied' and diagnose and close, both of which don't help. I also tried accessing with my 'admin' account and it gave me the same error. 



I'm not sure what I'm doing wrong do create this error.

Thanks In advance,

EDIT: so after trying this again, when accessing with the account only allowed to access music, i get a cannot find network path. when trying to log in as my admin account, i get a open file error and it says its unaccessible. 

FaceTheDream

---

### Post by codmate on 2012-01-29
Post the contents of /etc/samba/smb.conf and we can try to help more easily.

Thanks.

---

### Post by Morbius1 on 2012-01-29
All of this sounds like Linux permissions problems to me and not Samba problems but more information is needed to find out.

To start with we need to know how your shares are set up. Please post the output of each of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by FaceTheDream on 2012-01-29
Alright I have attached the smb.conf file
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
    workgroup = heavenlyrealm

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
    encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

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
;    printing = cups
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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
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


#This is the Music Folder 
[FLAC Music]
    path = /media/Download/FLAC Music
    writeable = yes
;    browseable = yes
    valid users = adminh, fouad, omar, sireen

[Chat Logs & Old Documents]
    comment = Old Files
    path = /media/Download/Chat Logs & Old Documents
    writeable = yes
;    browseable = yes
    valid users = adminh

[Download]
    path = /media/Download
    writeable = yes
;    browseable = yes
    valid users = adminh

```

---

### Post by Morbius1 on 2012-01-29
Since codmate answered first this is more of an interruption but you might want to post the output of the following command so the permissions of the entire path to the shared folders can be determined:
```
ls -al /media/Download
```

---

### Post by FaceTheDream on 2012-01-29
Alright so after inputing the ```
ls -al /media/Download
``` this is what i get:
```
adminh@Dreamer-Server:~$ ls -al /media/Download
total 217
drwx------ 1 adminh adminh 110592 2012-01-29 13:11 .
drwxr-xr-x 3 root   root     4096 2012-01-29 12:30 ..
-rw------- 2 adminh adminh   6771 2012-01-24 19:28 AlbumArtSmall.jpg
drwx------ 1 adminh adminh    464 2012-01-29 13:10 .AppleDB
drwx------ 1 adminh adminh      0 2012-01-29 13:10 .AppleDesktop
drwx------ 1 adminh adminh    712 2012-01-29 13:11 .AppleDouble
drwx------ 1 adminh adminh   4096 2012-01-29 13:10 Chat Logs & Old Documents
drwx------ 1 adminh adminh   4096 2012-01-29 13:10 Documents
-rw------- 1 adminh adminh  12292 2012-01-29 13:11 .DS_Store
drwx------ 1 adminh adminh  16384 2012-01-29 13:10 FLAC Music
-rw------- 1 adminh adminh  30399 2012-01-24 19:28 Folder.jpg
drwx------ 1 adminh adminh      0 2012-01-29 13:10 Games
drwx------ 1 adminh adminh   4096 2012-01-29 13:10 John Williams - Greatest Hits (1969-1999) [2CD]
drwx------ 1 adminh adminh      0 2012-01-29 13:10 Network Trash Folder
drwx------ 1 adminh adminh   4096 2012-01-29 13:10 non-FLAC MUSIC
drwx------ 1 adminh adminh   4096 2012-01-29 13:10 Old School Related Material
drwx------ 1 adminh adminh      0 2012-01-29 13:10 Pictures
drwx------ 1 adminh adminh   4096 2012-01-29 13:10 Program Files (x86)
drwx------ 1 adminh adminh   4096 2012-01-29 13:10 Program Files(x86)
drwx------ 1 adminh adminh      0 2012-01-29 13:10 Programs
drwx------ 1 adminh adminh      0 2012-01-29 13:10 $RECYCLE.BIN
drwx------ 1 adminh adminh      0 2012-01-29 13:10 System Volume Information
drwx------ 1 adminh adminh      0 2012-01-29 13:10 Temporary Items
drwx------ 1 adminh adminh      0 2012-01-29 13:10 UADL
drwx------ 1 adminh adminh   4096 2012-01-29 13:10 Videos & Movies

```Also to be noted, this was a Windows HDD used as storage if that clears anything up.

Also for the other two commands respectively here is what i got:
```
adminh@Dreamer-Server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[FLAC Music]"
Processing section "[Chat Logs & Old Documents]"
Processing section "[Download]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    workgroup = HEAVENLYREALM
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[FLAC Music]
    path = /media/Download/FLAC Music
    valid users = adminh, fouad, omar, sireen
    read only = No

[Chat Logs & Old Documents]
    comment = Old Files
    path = /media/Download/Chat Logs & Old Documents
    valid users = adminh
    read only = No

[Download]
    path = /media/Download
    valid users = adminh
    read only = No

```And  the ```
net usershare info --long
``` doesn't seem to display anything. 

Thanks In Advance as you guys can probably tell I'm no Linux guru by far.

FaceTheDream.

---

### Post by Morbius1 on 2012-01-29
This is an NTFS formated partition isn't it. If it is then as you can see from the output of ls -al that the only person who can access the /media/Downloads directory is "adminh" regardless of what you told samba to do.

It only affects one share so one way around this problem is to change this share:
> [FLAC Music]     
path = /media/Download/FLAC Music     
valid users = adminh, fouad, omar, sireen     
read only = NoTo this:
> [FLAC Music]     
path = /media/Download/FLAC Music     
valid users = adminh, fouad, omar, sireen     
[COLOR=Blue]force user = adminh[/COLOR]
read only = NoThen restart samba:
```
sudo service smbd restart
```What should happen is that the "valid users" line will restrict who has access to the share but once they are allowed in the "force user" will convert them all to adminh and thus have access to the folder.

---

### Post by FaceTheDream on 2012-01-29
Wow, thanks. That one line solved all the problems. :) 

Yeah It works pretty well now.

FaceTheDream.

---

