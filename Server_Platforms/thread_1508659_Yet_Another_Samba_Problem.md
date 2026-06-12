---
title: "Yet Another Samba Problem"
date: 2010-06-13
forum: Server Platforms
---

### Post by Jester2109 on 2010-06-13
Am having issues with setting up Samba shares on my Ubuntu Server that are accessible by Windows computers.

I've followed just about every Samba guide and troubleshooting threads I can find (and there are literally hundreds of them), but still cannot access the Samba shares.

smb.conf reads as:

[global]
  netbios name = Ubuntu-Server
  workgroup = TREGOF
  socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
  
  interfaces - lo, eth0
  bind interfaces only = true

  passdb backend = tdbsam
  security =  user
  null passwords = true
  username map = /etc/samba/smbusers
  name resolve order = hosts wins bcast

  wins support = yes

  printing = CUPS
  printcap name = CUPS

  syslog = 1
  syslog only = yes

[print$]
  path = /var/lib/samba/printers
  browseable = yes
  guest ok = yes
  read only = yes
  write list = root
  create mask = 0664
  directory mask = 0775

[printers]
  path = /tmp
  printable = yes
  guest ok = yes
  browseable = no

[sdb1 public hard disk]
  comment = Public Folder
  path = /media/store1
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = Family
  force group = no group

[sdc1 public hard disk]
  comment = Public Folder
  path = /media/store2
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = Family
  force group = no group



The two hard disks that I am trying to share (as seen in smb.conf above) are mounted and I have also run the 'chmod 0777' command on both.

I have added a user called 'Family' both as a Linux user and a Samba user. I have also given both a password (the same password actually).

The Windows computers (currently I am trying to enable just an XP Professional and a W7 Ultimate PC to connect to the shares, but I do also have some Vista PC's in the house that will eventually need to connect) have been set to be members of the workgroup TREGOF and also both know that the Ubuntu server is acting as a WINS server.

I can clearly see the shares in a network browse, but when I try to access either of the shares, regardless whether from the XP or W7 PC, I get the dreaded extended error failure.

The two shared hard drives are both NTFS drives (they came from an old Windows 2000 Server that I am retiring as the hardware is starting to fail). They are both fully readable (I can read them fine on the Ubuntu server itself).

I have disabled the firewall on the server so that can be discounted as the issue.

I am completely flummoxed now as to what the problem may be other than to surmise that it is something to do with Linux privileges (rather than Samba) that is stopping me accessing these shares.

I don't know if this helps at all, but doing  the   ls -dl command on both hard drives I am looking to share gives the following results:

drwxrwxrwx  1  root  root  4096  2010-05-15  13:03  /media/store1
drwxrwxrwx  1  root  root  4096  2010-05-15  13:04  /media/store2

Now I am aware that both hard drives are owned by root from what the above shows me, but I don't see why that should stop me being able to access the shares.

I also eventually want to share the HP Printer that is attached to the server, but I've not even looked into that yet.

Any pointers greatly appreciated as I have been trying to resolve this for the past two days.

Cheers

---

### Post by Ryan Dwyer on 2010-06-13
Your Samba is configured to log to the syslog, so check it to see what's going on.

grep samba /var/log/syslog

---

### Post by Jester2109 on 2010-06-13
Interesting. Message in log file states:

Can't open username map /etc/samba/smbusers. Error no such file or directory.


...and it is correct. It doesn't exists. The question is, where is it ?

---

### Post by Ryan Dwyer on 2010-06-13
It's specified in your username map option.

[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP)

You can probably just remove that from your config.

---

### Post by Jester2109 on 2010-06-13
Cheers for that. Removed the username map. Now I get an error that my shares do not exist in the usershares directory - which they don't as it happens (though I don't understand why). Guess a bit more reading is in order.

---

### Post by Jester2109 on 2010-06-14
Grrrr...getting annoyed with this now. Am actually getting an 'invalid group' error returned when I try to access these Samba shares - despite the fact that I have actually specified 'no group' in the config.

Have even changed to 'security = share' to get around the authentication problem for the moment.

As much as I am keen to learn the workings of Linux, this seems to be an almighty faff just to enable Windows PC's to be able to access the shares !!

Feel I have mastered Linux Desktop quite well, but Linux Server is a completely different kettle of fish !!

---

### Post by Ryan Dwyer on 2010-06-14
Where did you get this config from? It's not relevant to your system. You should consider running apt-get purge samba then apt-get install samba. That will remove the config and replace it with fresh working config from the repo.

I don't think you can use force group = no group either. Just remove or comment the option.

---

### Post by Jester2109 on 2010-06-14
Hi Ryan,

I appreciate your patience and guidance. As I have stated, I am really learning Linux and have been playing with several different distros (CentOS, Fedora, Ubuntu etc etc) to help my understanding. I settled on Ubuntu Server as I am already used to the Desktop Version (have been using it for about 2 months now).

I got the main bones of the Samba config from here   

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Obviously, I have changed some aspects to reflect my set-up as I think it needed to be adapted. I am getting better with the finer points of Linux but (as someone who has used MS products for more than 20 years), I am finding it a little frustrating at times. I will get there but constantly find myself having to check on 'how-to' commands to get things done. The biggest problem is that many things seem '***-backward' to how it would be done in Windows.

But bear with me, hopefully as I learn more and more I will get better and more knowledgable and be able to help others much in the same way as you have helped me so far.

Cheers

---

### Post by Ryan Dwyer on 2010-06-14
I wouldn't follow that guide due to the fact they never mention the smbusers file yet have it in their config. Also, the post was made in 2006. Things tend to change quickly in the Linux world and guides written more than about 2 years ago tend to be outdated.

Here's a fresh smb.conf, which should be usable:

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
# to enable the default home directory shares. This will shae each 
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

```

You should change the workgroup to whatever your client machine is using. Then it's just a case of creating the shares at the bottom of the file.

By the way, this page is awesome for configuring Samba: [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)
It contains every config there is. Use Ctrl + F to find it.

If you run into issues, cd to /var/log/samba/ and read the log files that appear there.

---

### Post by Jester2109 on 2010-06-14
Cheers Ryan.

Given the time difference, I assume you are probably asleep by now. I shall give this a go when I get home from work tonight and let you know.

---

### Post by Jester2109 on 2010-06-14
Well slap me senseless with a cocktail sausage !!

It works !!

Rather than use the smb.conf example you gave me, I just thought I would try removing  the lines:

force user = Family
force group = no group

              first from the shares, and lo and behold it allowed me to browse and access the shares without logging in - which is what the ultimate aim was anyway. Anyone not on my home network should not be able to access the shares as I have restricted to the local network only.

Now onward to printing ...


Cheers Ryan

---

