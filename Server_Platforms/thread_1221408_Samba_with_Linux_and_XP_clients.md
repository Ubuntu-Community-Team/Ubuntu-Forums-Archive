---
title: "Samba with Linux and XP clients"
date: 2009-07-23
forum: Server Platforms
---

### Post by paped on 2009-07-23
Hi I have a bit of an odd problem I run a small ubuntu server (8.04 LTS/with generic kernel) and this runs Samba where I have a couple of laptops accessing the shares, one XP, one is eeebuntu3 both can access the shares and create, delete etc. However if I create a folder with XP the eeebuntu pc cant write to it and vice versa.

I think I have worked out the problem but can't work out how to fix it basically the problem appears to be how Nautilus works in that it does not mount the share as such with my user name thus when the file or dir is created its seen as a guest and defaults to the nobody/nogroup and has file permissions that does not allow the group or "others" to write to it. When XP creates a dir/file the detail of the username and group/permissions appear to be correct but with the eeebuntu being a guest with nobody/nogroup permissions as such it can't write to the XP share, thus I constantly have the mismatch.

I have tried various things such as mapping guest user to a valid user, or forcing the user/group but everytime it seems cause more issues than it fixes such as one or the other PC looses access completely...

I think I need to somehow get nautilus to pass my username to the server anybody know how to do this, I have tried added the share to fstab and mounting them in the cli but then the file manager does not seem to see the mount properly..... basically I could do with a "map network drive" feature like in XP but I don't think there is such a thing for Linux from the various forum I have read. 

Any idea or help appreciated basically all I need to do is write to the samba drives with both PC's the only option I cannot really do is to force a lower create/directory mask to say 757 or 777, as 4 of the shares have write permissions for some users and not for others and this would break that, already tried it even though it does fix this posted problem is just not a viable solution....

Thanks

---

### Post by swerdna on 2009-07-24
Can you post here the file smb.conf. It's a permissions problem and not too hard to fix probably.

---

### Post by paped on 2009-07-27
Hi the whole smb.conf file is below.... it a bit on the large size as I have just customised the default one. The Home and "Shared_Files" directories work fine the later presumably because of the 777 masks. The problematic directories are the last 3 at the very end of the file.


##########Start of file###########

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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = homelan

# server string is the equivalent of the NT Description field
   server string = %h 
#  server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

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

   map to guest = bad user
   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

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
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

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
   socket options = TCP_NODELAY

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
[homes]
   comment = Home Directories
   browseable = no
   hide dot file = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
#   writable = yes
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
#   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
#   directory mask = 0700

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
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   printcap name = /etc/printcap
   print command = /usr/bin/lpr -P%p -r %s
   printing = cups

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

# Standard HD shares below

[Shared_Files]
path = /home/storage/Shared_Files
browsable = yes
public = yes
writable = yes
directory mask = 0777
create mask = 777

[Music]
path = /home/storage/Music
browsable = yes
writable = yes
public = yes
write list = paul, lucy, user

[Photos]
path = /home/storage/Photos
browsable = yes
writable = yes
public = yes
write list = paul, lucy, user

[Backup]
path = /home/storage/Backup
browsable = yes
writable = yes
public = no
write list = paul, user

---

### Post by swerdna on 2009-07-27
Hi

This share:
```
[Backup]
path = /home/storage/Backup
browsable = yes
writable = yes
public = no
write list = paul, user
```
Can only be accessed by logging on, not by guests. And it's writeable to two users (a user named "user" and a user named "paul"). Of course, the two users, (paul and user) must be enrolled into the samba user database for this to work. A second requirement for this to work revolves around the ownership/permissions of "backup" directory. ```
sudo chmod -R 777 /path/name
``` should fix it.

For the shares [Music] and [Photos] (same structure):
```
[Photos]
path = /home/storage/Photos
browsable = yes
writable = yes
public = yes
write list = paul, lucy, user
```
Once again, paul, lucy and user must belong to the Samba suer database. I don't understand the problem here. You've got guest access because of the line "public = yes". In theory, a guest should come in as user "nobody" and should be absolutely prohibited from writing by the line "write list = etc". So there should be no problem. That's the way Samba is designed. If users from xp can write without logging in, there's a flaw in xp.

There's also a contradiction in terms: guest access and logon authentication are at odds with each other so generally they're not used together.

So I'm not really understanding the problem. Is it that a user from the eeebuntu3 might really be named e.g. "lucy" but is coming in as "nobody" when you'd prefer her to come in as "lucy" and thus have write permissions? Is that it? 

OR: accept that a Linux machine will not send the username. What do you want of the share [music]. Describe that carefully.

---

### Post by swerdna on 2009-07-27
On reflection, I take this out pending what you say

---

### Post by paped on 2009-07-27
Basically what I am after is for the share to be locked down so only the dominated users can write to the drive but to allow access to everyone to read the files, if possible without a password.

The frustrating thing and why I think that it may be something to do with a recent Samba upgrade that I saw come through on APT, is that the above smb.conf has been on 3 servers and has worked with various Linux distros and XP as clients for about 5 years unchanged. 

What used to happen is that the user name did seem to be passed from both XP and Linux clients and the user:group when a file or directory was created used to be the actual username:group.... As it was the actual user name and group it then used to allow me to create a directory on any PC and access it on any other. But it is like samba is now accepting the windows login file (bat.file using net use) username but from Linux it does not and logs the Linux connection/user to the nobody (guest) user.

Hence my original problem where XP creates a file with paul:users but the nobody user from Linux can't edit/delete it, Linux creates a file with nobody:nogroup and then the paul XP user can't edit/delete it.

Thus from you're response I presume that I need to somehow force each user to login to each share from both XP and Linux to ensure that the correct user:group is assigned rather than for whatever reason the Linux system using the guest account and defaulting to the nobody:nogroup settings? 

Thanks in advance for any help you can give....

---

### Post by swerdna on 2009-07-27
Try this:

```
[Photos_admin]
path = /home/storage/Photos
read only = no
valid users = paul, lucy, user

[Photos]
path = /home/storage/Photos
guest ok = yes
read only = yes
```

and similarly for [Music]

You can add this line to the admin versions if you like your network to be tidy: ```
browseable = no
```

---

### Post by swerdna on 2009-07-27
Here's another one somewhat different:
```
[ShareName]
path = /path_to/shared_directory
read only = no
write list = blah blah
```
You chown the directory to 1777
You chmod it to a normal Linux user (e.g.lucy).
Anyone in the write list can add or create an item and then they own it -- but once created, other network users have read-only rights to files and directories that they don't own.

---

### Post by swerdna on 2009-07-27
And finally:

You can make a Linux user e.g. netguest. Add netguest to the Samba user database with this command:```
sudo smbpasswd -n netguest
```
Make a share like this:
```
[Photos]
path = /home/storage/Photos
write list = blah blah
```
chmod it to 777
For this share the user netguest can log on with no password (null password) but only the write list can add files after a valid logon

More references here: see the segment "[Part II: Defining and Using File Shares (Services)]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")" in this tutorial:
[Samba Server and Ubuntu / Kubuntu: HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html")

---

### Post by doogy2004 on 2009-07-27
I solved this problem by creating a "powerusers" group then chown all the files in the share to have "powerusers" as the group.  I then used chmod g+s -R on the share to force any new files to have the same group permissions and ownership as the folder.

---

### Post by paped on 2009-07-29
Did the changes shown in item 7 above and it's worked a treat,,,, Thanks you very much for you're help in sorting this out. :D

---

### Post by swerdna on 2009-07-29
> **paped said:**
> Did the changes shown in item 7 above and it's worked a treat,,,, Thanks you very much for you're help in sorting this out. :D

You're welcome

---

