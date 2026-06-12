---
title: "Help with making shared folder writeable"
date: 2006-02-07
forum: Server Platforms
---

### Post by Swiss2K on 2006-02-07
I have made a server install. I installed both proftpd and samba. Everything is working, but i can only browse the folders I want to share. How do I make them writable? I want to make the following config. In both proftpd en samba I need read/write in /archive.


**My smb.conf is: **

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Network

# server string is the equivalent of the NT Description field
   server string = %h 

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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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

[archive]
	comment = archive
	path = /archive
	read only = no
	browseable = yes
	writable = yes
	guest ok = no



**My proftpd.conf: **

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

---

### Post by skirkpatrick on 2006-02-07
If you're going to set security=user (I use security=share), then everyone who has an account on that machine needs to be added to a group that has access to that directory.  Then you need to use "chgrp" to change the group ownership of that directory.

---

### Post by Swiss2K on 2006-02-07
Well, i did made samba share instead of user. The problem still exist. Folders can be read but not being written. I'm lost here. Do I forget something here? please help this is driving me nuts for days.

---

### Post by Swiss2K on 2006-02-08
If I understand correctly then I have to make a group, let's say 'smbusers'. To this group I have to add my users. And last I've to give the group permission to /archive dir. Is this correct?? If so can anyone tell which commands to use.

---

### Post by skirkpatrick on 2006-02-08
There is an easier way.  I don't touch my fileserver much but I had messed up one of its shares a while back and had to change it.  This server has been up for several years and some things that I've done may not have been necessary.  Here's what I've got on it:

1) I created a user called smbguest and created a group called smbguest.

2) I created a directory called /home/Public and gave user & group ownership to smbguest using **sudo chown smbguest /home/Public** and **sudo chgrp smbguest /home/Public**.

3) Set my share settings in /etc/samba/smb.conf to:
> 
[Public]
    guest account = smbguest
    force user = smbguest
    create mode = 0777
    writeable = yes
    path = /home/Public


4) Restart Samba.


With these settings, any machine in the house has full access to the Public share.  Now I am behind a router so I'm not worried about security issues.

---

### Post by LordHunter317 on 2006-02-08
[QUOTE=skirkpatrick]If you're going to set security=user (I use security=share),[/quote]**No, bad advice.**  Security=share is deprecated and will be going away eventually.  Don't use it anymore.  Don't suggest for otheres to use it, either.  It breaks the protocol in several ways.

> then everyone who has an account on that machine needs to be added to a group that has access to that directory.  Then you need to use "chgrp" to change the group ownership of that directory.You also need to adjust the samba create and directory masks, and enable the setgid bit on all directories to enforce group propogation.


Your smb.conf is also terrible.  **If your solution involves 777, your solution is wrong.**

The correct procedure is:[list=1][*]Create a group for all users accessing the share.  Call it the name of the share for convience, but it doesn't matter.[*]Add all users to the group via:```
for user in jim bob bill ; do sudo adduser $user archive ; done
```[*]Set the proper permissions and ownership on the share:```
sudo chown -R root.archive /archive
sudo chmod u=rwX,g=rwX,o=
```If you want guest access, then change 'o=' to 'o=rX'.  This command is case-sensitive, so copy as seen.[*]Enable setgid propogation to ensure the ownership is persisted:```
find /archive -type d -print0 | xargs -0 chmod g+s
```[*]Configure Samba to enforce correct permissions and propogation by adding/changing these lines in the share definition:```
create mask = 660
directory mask = 2770
```If you want read-only guest access, change those to:```
create mask = 664
directory mask = 2775
```[/list]Done.

---

### Post by skirkpatrick on 2006-02-08
Well, I said I may not have done things correctly :)

Most of that setup was from 4 or 5 years ago when I set that machine up with RH8.  I had almost no Linux experience and followed recommendations from others at the time.  One of the things on my ToDo list is to tear that server down, install bigger drives and reinstall with Ubuntu.  At that point I'll set everything up the correct way.  Thanks for pointing that stuff out, LordHunter317.

---

### Post by Swiss2K on 2006-02-08
Thanks for your help LordHunter317. It really helped me a lot!

---

