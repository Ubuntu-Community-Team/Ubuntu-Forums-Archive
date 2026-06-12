---
title: "Slow server disk to disk file transfers (samba, sftp)"
date: 2009-01-11
forum: Server Platforms
---

### Post by gogobambi on 2009-01-11
I'm having trouble with slow file transfers between two physical SATA harddrives on the server when using both samba file sharing through Mac OS X Finder and SFTP through Cyberduck. Speeds are normal when using cp through ssh Terminal.

A 120MB file takes under 2 seconds in Terminal cp, but over 7 minutes using samba or sftp. This is from one SATA fixed disc to another.

Any ideas as to how I can fix this? I need to move a *LOT* of files from an external eSATA HDD over to the server, which at 1-2MB/s is about as exciting a prospect as sorting though 300GB of files in cli only.

I'm running Ubuntu 8.10 Server on a D945GCLF2 based system and have been using linux under a week, so cut me some slack if I'm missing something obvious :)

iPerf (Macbook as client, Ubuntu Server as server)
```
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local xxx.xxx.x.xxx port 5001 connected with xxx.xxx.x.xxx port 51373
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  25.5 MBytes  21.4 Mbits/sec
```

smb.conf
```
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
#   security = share

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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

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


[servspace]
	path = /servspace
	public = yes
	writable = yes
	create mask = 0777
	directory mask = 0777
	force user = nobody
	force group = nogroup

[serv]
	path = /serv
	public = yes
	writable = yes
	create mask = 0777
	directory mask = 0777
	force user = nobody
	force group = nogroup

[extusb]
	path = /media/external
	public = yes
	writable = yes
	create mask = 0777
	directory mask = 0777
	force user = nobody
	force group = nogroup
```

hdpram (sda and sdb are internal SATA, sdc is the external eSATA)
```
root@xxxxxx:# hdparm -tT /dev/sd*

/dev/sda:
 Timing cached reads:   974 MB in  2.00 seconds = 486.69 MB/sec
 Timing buffered disk reads:  226 MB in  3.02 seconds =  74.74 MB/sec

/dev/sda1:
 Timing cached reads:   1194 MB in  2.00 seconds = 597.15 MB/sec
 Timing buffered disk reads:  224 MB in  3.01 seconds =  74.35 MB/sec

/dev/sdb:
 Timing cached reads:   1200 MB in  2.00 seconds = 600.08 MB/sec
 Timing buffered disk reads:  186 MB in  3.02 seconds =  61.67 MB/sec

/dev/sdb1:
 Timing cached reads:   1206 MB in  2.00 seconds = 602.69 MB/sec
 Timing buffered disk reads:  186 MB in  3.01 seconds =  61.84 MB/sec

/dev/sdb2:
 Timing cached reads:   1188 MB in  2.00 seconds = 594.35 MB/sec
 Timing buffered disk reads:  188 MB in  3.03 seconds =  62.05 MB/sec

/dev/sdb3:
 Timing cached reads:   1178 MB in  2.00 seconds = 588.80 MB/sec
 Timing buffered disk reads:  186 MB in  3.01 seconds =  61.79 MB/sec

/dev/sdb4:
read(2097152) returned 1024 bytes
 Timing buffered disk reads:  read() hit EOF - device too small

/dev/sdb5:
 Timing cached reads:   1192 MB in  2.00 seconds = 596.01 MB/sec
 Timing buffered disk reads:  186 MB in  3.00 seconds =  61.90 MB/sec

/dev/sdb6:
 Timing cached reads:   1184 MB in  2.00 seconds = 591.47 MB/sec
 Timing buffered disk reads:  186 MB in  3.01 seconds =  61.74 MB/sec

/dev/sdb7:
 Timing cached reads:   1184 MB in  2.00 seconds = 591.93 MB/sec
 Timing buffered disk reads:  186 MB in  3.01 seconds =  61.85 MB/sec

/dev/sdb8:
 Timing cached reads:   1186 MB in  2.00 seconds = 592.59 MB/sec
 Timing buffered disk reads:  186 MB in  3.01 seconds =  61.79 MB/sec

/dev/sdc:
 Timing cached reads:   1184 MB in  2.00 seconds = 592.17 MB/sec
 Timing buffered disk reads:  168 MB in  3.02 seconds =  55.66 MB/sec

/dev/sdc1:
 Timing cached reads:   1190 MB in  2.00 seconds = 594.88 MB/sec
 Timing buffered disk reads:  168 MB in  3.02 seconds =  55.68 MB/sec
```

---

### Post by samosamo on 2009-01-12
Are your running RAID?  What are the hardware specs on the box?  

Also, I would strongly advise you to install netatalk packages so you can use AFP instead of SMB/CIFS.  It increased my speeds 3x to my Mac clients.  No reason to involve shoddy Microsoft technology in your UNIX based environment.

---

### Post by gogobambi on 2009-01-12
No RAID, just regular SATA at the moment running on a [D945GCLF2 board]("http://www.intel.com/products/desktop/motherboards/D945gclf2/D945gclf2-overview.htm")--1.6Ghz dual core, mini-itx. The two drives are both Western Digital, one new 500GB drive from the 'Green Power' series, the other a 250GB SATAI relic from an older box.

Unfortunately there's a windows box that has to be considered, but I barely use it so I'll definitely look into AFP.

Slow network speeds are one thing, but why is it so slow to transfer from one physical disk in the server to another? Am I missing something? When I transfer a file from HDDA is it going from HDDA -> Network -> Macbook -> Network -> HDDB? How do I get it to go straight from HDDA -> HDDB without using Terminal cp?

---

### Post by dudenamedsteve on 2009-01-12
true, doing it from the Macbook by just opening the two separate SMB shares and dragging stuff from A to B IS going to first bring it across the network to your macbook and back.  Is there any way you can log directly into the server to initiate the transfer, either with an attached console or through VNC or the like?  It would be quick like with the terminal copy.  Unless someone else out there knows something better.

---

### Post by HermanAB on 2009-01-13
Just SSH to the server and then use "cp -r whatever wherever" or "rsync whatever wherever".

If you want to be click happy do this:
$ ssh -X -C -c blowfish user@server gnome-panel

Cheers,

Herman

---

### Post by gogobambi on 2009-01-13
Well, I've [set up AFP via netatalk]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") and the speeds are 5x better, so thanks for the tip samosamo!

Guess there isn't a GUI-based alternative to cp, then (on a headless server over LAN using a Macbook). Makes sorting through all these files pretty tedious, but at least it isn't slow.

---

### Post by cariboo on 2009-01-14
I use a program called mc in a terminal to do most of my administration on the server. It works great for copying from one disk to another and editing configuration files. MC is a texted based file manager that is mouse aware, but works much better using the keyboard. MC is available in the repositories. At the prompt type:

```
sudo apt-get install mc
``` 

Jim

---

### Post by gogobambi on 2009-01-14
Thanks for the tip cariboo907, MC is making things a lot quicker!

---

