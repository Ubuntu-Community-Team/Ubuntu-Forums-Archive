---
title: "Ubuntu 14.04 MS Word Doc Read Only in shared &quot;Home&quot; folder"
date: 2015-08-05
forum: Server Platforms
---

### Post by Curt_Smock on 2015-08-05
Hello -

I have been pulling my hair out to try this what I would think would be a simple issue. I have been doing some searching online and have come across similar problems and have applied those solutions to no avail. Here is what I have going on:


[LIST=1]
[*]Dell Poweredge 830 Server
[*]Ubuntu 14.04 LTS installed and working
[*]Shared folder called "Public" in the Home folder in the "Curt" user login on the server
[*]From my laptop using Windows 7 (also User "Curt"), I can see the folder and contents without any issues.
[*]I use a password in Windows 7 to log onto my laptop
[*]I create a document on my laptop and save it in this Public folder
[*]Another user logs onto the server from this or a different computer without a login password and can see this folder and the contents
[*]They are unable work on this document and save, as it is marked [Read Only].
[*]If they create a document in this same folder, they can open it and save it without issue.
[*]I cannot be sure (I am not at the server right now), but I think that when they create a document, it is marked [Read Only] to me.
[/LIST]

What do you need from me to help me diagnose this behavior? I have checked the smb.conf file, but I don't see anything obvious. Do you need to see this?

Strangely enough, this behavior does not occur with a plain text notepad document. It seems to be only affecting MS Word and Excel documents.

---

### Post by Bucky Ball on 2015-08-05
*Thread moved to **Server Platforms**.*

You have a better chance of support here. You are new but we're a friendly bunch here so people will be gentle(ish). :)

---

### Post by SeijiSensei on 2015-08-05
MS Office programs use their own proprietary file-locking methods.  Read this [discussion]("https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/locking.html") about "oplocks;" they may be the source of the problem.  For a quick possible solution, read this: [http://www.linuxquestions.org/questions/linux-software-2/cannot-open-any-file-with-ms-office-on-my-centos-6-samba-share-4175446711/](http://www.linuxquestions.org/questions/linux-software-2/cannot-open-any-file-with-ms-office-on-my-centos-6-samba-share-4175446711/)

---

### Post by Curt_Smock on 2015-08-06
Thank you for your input. I will follow up and check out the articles a bit further. I tried adding the "oplocks" text as outlined in the article to my smb.conf file, but it did not seem to help. I also have  adobe acrobat documents that experience the same behavior. I'll have to experiment a bit more and find out if there are other types of files that do the same thing. I have noticed that it is only between my user and another user, not between other users. Mine is the only password protected login also.

---

### Post by volkswagner on 2015-08-07
How did you share the folder (are you using SAMBA or did you right click folder in GUI and share)? What are folder/file permissions?

```
ls -al /home/curt/public
```

---

### Post by Curt_Smock on 2015-08-07
> **volkswagner said:**
> How did you share the folder (are you using SAMBA or did you right click folder in GUI and share)? What are folder/file permissions?

```
ls -al /home/curt/public
```

VW, Here is my smb.conf file.

Are you asking me to execute in terminal your line of code and post the results? Yes, I have been using Samba to set up shares. Right now I have the folders in the "Curt" group and they are read/write.

I hope this is the way I am supposed to post it...

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
##
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
# - When such options are commented with ";", the proposed setting
# differs from the default Samba behaviour
# - When commented with "#", the proposed setting is the default
# behaviour of Samba but the option is considered important
# enough to be mentioned here
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
# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes
# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z
# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no
# What naming service and in what order should we use to resolve host names
# to IP addresses
name resolve order = lmhosts host wins bcast
usershare owner only = false
kernel oplocks = no
nt acl support = no
strict locking = no
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
; passdb backend = tdbsam
obey pam restrictions = yes
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
unix password sync = yes
# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n
*password\supdated\ssuccessfully* .
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
#; domain logons =
yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
; logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
# logon path = \\%N\%U\profile
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
; logon drive = H:
# logon home = \\%N\%U
# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
; logon script = logon.cmd
# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe. The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
# This allows machine accounts to be created on the domain controller via the
# SAMR RPC pipe.
# The following assumes a "machines" group exists on the system
; add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s
/bin/false %u
# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.
; add group script = /usr/sbin/addgroup --force-badname %g
########## Printing ##########
# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
# load printers = yes
# lpr(ng) printing. You may wish to override the location of the
# printcap file
; printing = bsd
; printcap name = /etc/printcap
# CUPS printing. See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups
############ Misc ############
# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m
# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
# socket options = TCP_NODELAY
# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
# domain master = auto
# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash
# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
; winbind enum groups = yes
; winbind enum users = yes
# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
# Maximum number of usershare. 0 (default) means that usershare is disabled.
; usershare max shares = 100
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yes
username map = /etc/samba/smbusers
#======================= Share Definitions =======================
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home director as \\server\username
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
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
; valid users = %S
# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; read only = yes
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
browseable = no
path = /var/spool/samba
printable = yes
; guest ok = no
; read only = yes
create mask = 0700
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
; browseable = yes
; read only = yes
; guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
; write list = root, @lpadmin
# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; read only = yes
; locking = no
; path = /cdrom
; guest ok = yes
# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom
[Data]
comment = Data
path = /data/data
; browseable = yes
guest ok = yes
writeable = yes
directory mask = 0777
oplocks = no
acl check permissions = false
level2 oplocks = no
locking = no
strict locking = no
share modes = no
[Public]
path = /home/curt/public
writeable = yes
; browseable = yes
guest ok = yes
comment = Public Directory
oplocks = no
acl check permissions = false
level2 oplocks = no
locking = no
strict locking = no
share modes = no
```

I'm definitely a Ubuntu newb. I am using the Ubuntu 14.04 LTS Desktop version as a server platform. The whole Linux process is still Greek to me, but I am trying to stumble around to figure things out.

Hope you see some obvious things wrong in the file and can guide me in the right direction.

---

### Post by TheFu on 2015-08-08
*Please* use "code tags" when posting config or log files.  **Adv Reply** has a button. Makes things easier to read for the old-timers.  You can edit post #6 to fix that.

---

### Post by volkswagner on 2015-08-08
Yes, please post the output of the following command.

```
ls -al /home/curt/public
```

---

### Post by Curt_Smock on 2015-08-08
TheFu - Thanks for the advice...as I said, a bit of a newb...:D

---

### Post by Curt_Smock on 2015-08-08
Here is the output:

```
curt@FS1:~$ ls -al /home/curt/public
total 36
drwxrwxrwx  9 curt curt 4096 Aug  7 22:57 .
drwxrwxrwx 24 curt curt 4096 Aug  8 08:21 ..
drwxrwxrwx 12 curt curt 4096 Jun 26 21:14 Drivers
drwxrwxrwx 52 curt curt 4096 Jun 27 07:27 Gaming
drwxrwxrwx 26 curt curt 4096 Dec 16  2014 Manufacturers
drwxrwxrwx  2 curt curt 4096 Dec 16  2014 Network
drwxrwxrwx 62 curt curt 4096 Jul 27 18:45 Programs
drwxrwxrwx  4 curt curt 4096 Aug  7 22:59 Temp
drwxrwxrwx  7 curt curt 4096 Aug  8 08:24 Windows Setup

```

---

### Post by volkswagner on 2015-08-08
I guess I should have been more descriptive.

Please post the output for a directory that contains the files you're have trouble with.

---

### Post by TheFu on 2015-08-08
777 permissions on /home/curt/public is completely unnecessary. Please don't leave it that way.
Sooner or later you will need to learn and understand file and directory permissions on Unix since it is a multiuser OS. Sooner is better than later, BTW.  Ubuntu has a tutorial for this - google it.

BTW - "Curt" is not a group.  Group names are lowercase.  Unix is case sensitive, so you need to be extremely careful when using different case for anything. It matters.  Generally, it is best to go all lowercase for everything, except files and directories. For those, Just use whatever case you desire - always.  You'll get used to this - OSes that don't care about case will bother you, eventually.

smb.conf - the "domains" section has an error. Is that really the file?  Run **testparm** to see what samba knows.

---

### Post by Curt_Smock on 2015-08-08
VW -

I hope this is what you were looking for...

```
-rwxrw-rw-  1 curt curt  376832 Aug  8 21:02 Test Database.accdb
-rwxrw-rw-  1 curt curt   38259 Aug  8 20:56 Test Document-Adobe Acrobat.pdf
-rwxrw-rw-  1 curt curt    8703 Aug  8 20:55 Test Document-MS Excel 2010.xlsx
-rwxrw-rw-  1 curt curt   13849 Aug  8 20:54 Test Document-MS Word 2010.docx
-rwxrw-rw-  1 curt curt 1115232 Aug  8 20:58 Test Photoshop Document.psd
-rwxrw-rw-  1 curt curt   97792 Aug  8 21:03 Test Publication Document.pub



```

These documents all cannot be saved when opened by another user after being created by me.

Curt

---

### Post by Curt_Smock on 2015-08-08
TheFu -

I didn't think that I had a 777 mask set for public, only the data folder? In any case I will look at the tutorials that you mentioned. Here is the result of testparm...

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Data]"
WARNING: The "acl check permissions" option is deprecated
Unknown parameter encountered: "share modes"
Ignoring unknown parameter "share modes"
Processing section "[Public]"
WARNING: The "acl check permissions" option is deprecated
Unknown parameter encountered: "share modes"
Ignoring unknown parameter "share modes"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

```

---

### Post by volkswagner on 2015-08-08
Can you show an example of permissions with a folder containing both files created by you and files created by user other than you?

---

### Post by SeijiSensei on 2015-08-09
I'd like to suggest another test.  Install LibreOffice on the Windows machines.  If you use that on both the Windows and Linux machines, do you have the same file-locking problems?

I still think your problem has something to do with MS Office and not Samba or Linux, since you wrote in your first post:
> Strangely enough, this behavior does not occur with a plain text notepad document. It seems to be only affecting MS Word and Excel documents. 

---

### Post by Curt_Smock on 2015-08-09
SeijiSensei -

OK, I loaded up LibreOffice on my Windows machine and got the following error. I created the ODT file on my user and then switched to another user and tried to access it. I have not tried installing LibreOffice on another machine yet. That will be the next step. It looks like it's not only MS Office products that are affected, unfortunately.

[ATTACH=CONFIG]263742[/ATTACH]
Strangely, I am getting random times that the MS Word/Excel and Acrobat documents are editable by all users from time to time. Let me do some more research and get back to the group. The ODT file has remained uneditable to everyone but me, however.

Curt

---

### Post by SeijiSensei on 2015-08-10
Did you close the document on the machine it was created on before trying to edit it from another machine?  That's exactly what file-locking is designed to prevent.  Even on an all-Linux system like mine, if I open a document in LO, it will be locked on other machines.

---

### Post by Curt_Smock on 2015-08-11
SeijiSensei -

Sorry for the long pause in replying...just took my oldest down to college today. I just tried top open the ODT file while logged in as another user and no joy, same error. The ODT file was attempted to be opened only by the other logged in user. Could this be a Windows 7/Linux compatibility issue? I still need to find some time to install LO on another machine. I will report back once that has been achieved.

---

### Post by Curt_Smock on 2015-08-23
SeijiSensei -

Well, I could not figure it out, although I have a suspicion it had to do with the fact that I had a group called "curt" on the Ubuntu Server and my password was the same to log onto the server as it was to log onto my laptop, plus my Windows user was "curt" as well, so maybe some conflict existed there. In any case, I ended up re-loading my laptop with Win 7 (It needed it anyways) and created a new user name and a different password for my login. The problem went away. Funny thing is on a couple of password protected excel documents, I had to save a copy of the document before I could work on them. The problem seems to have corrected itself with me deleting my login and user off of my laptop. Thanks for everyone's help.

Curt

---

