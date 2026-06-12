---
title: "Remote file managing for ubuntu server."
date: 2008-10-03
forum: Server Platforms
---

### Post by qwerdy on 2008-10-03
Hi,

I'm looking for a way to manage files on my server.
As for now i use putty to move/copy/rename... 
But it's very bothersome.

I dont have X/gui installed, so remote desktop is not a solution.

I'm now using Windows Vista on my desktop pc, but when i used XP i could move files from mounted samba shares to antoher mounted samba share, and it would move it directly on the server. But when i try that in Vista its goes throug my desktop pc, so its going really slow.

Any one have any suggestions for a easy remote file manager solutions?


Thanks,
qwerdy

---

### Post by elvinatom on 2008-10-03
webmin provides a file manager that is java based, you might wanna look into that.

---

### Post by Rich78 on 2008-10-03
If I was you I would learn *nix commands and use ssh over Putty as you have been doing.  

Sure it's not as pretty but it can be a lot quicker once you're used to it.

---

### Post by lykwydchykyn on 2008-10-03
Have you tried winSCP?  I don't work in windows, but it looks like a decent tool for what you want to do.

---

### Post by qwerdy on 2008-10-03
Thanks for the fast replys.

elvinatom: I actually have webmin installed, didnt think to check it. will try it out.

Rich78: I do have som experience in *nix, and have no problem using putty, it's just that i was looking for a more efficient/easier, way.

lykwydchykyn: I have tried that one, it's made for transfer locally to server, not locally on the server. well, not in a easy way. i have to manually enter the move to directory. 


But does anybody know why the samba thing wont work under Vista?
Cause a solution like that would be preferably.

---

### Post by Rich78 on 2008-10-03
Could always shell script an rsync command?  Probably couldn't get much simpler than that after setup?

It would allow you to mirror a directory structure on the remote machine from running one shell script.

---

### Post by windependence on 2008-10-04
You can actually configure WinSCP to have both panes connected to your server.

The real problem is your SAMBA doesn't sound like it's configured right. Can you post your config file here?

-Tim

---

### Post by qwerdy on 2008-10-04
oh, guess i have to check it out a bit more then =)
EDIT: I don't find it :p

here's my samba config:

```

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = webserver
	invalid users = root
	unix password sync = yes
	workgroup = Mshome
	os level = 20
	security = user
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
;   wins support = no

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how nsuccessful authentication attempts are mapped 
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
;   load printers = yes

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



[www]
        path = /var/www
        comment = WWW root
        writable = yes
        public = no
        valid users = joakim

[backup]
	comment = Backup filer
	writable = yes
	valid users = joakim
	public = no
	path = /home/joakim/backup


[Download]
	comment = Nedlasting
	path = /download
	write list = joakim

[Disk]
	comment = Disk
	writable = no
	path = /mnt/disk
	write list = joakim

[Install]
	comment = Install filer
	writable = no
	path = /mnt/install
	write list = joakim

[Serier]
	comment = Serier
	writable = no
	path = /mnt/serier/Serier
	write list = joakim


[Filmer]
	comment = Filmer
	writable = no
	path = /mnt/filmer/Filmer
	write list = joakim

[Film_div]
	comment = Film_div
	writable = no
	path = /mnt/film_div/Film_div
	write list = joakim

```

---

### Post by cariboo on 2008-10-04
I would uncomment two things in your smb.conf file:

> ;   interfaces = 127.0.0.0/8 eth0 

Just remove the semi-colon and change the interface to eth0, or your ip address.

> ;   bind interfaces only = true 

Just remove the semi-colon as it works the same way as a #

Jim

---

### Post by qwerdy on 2008-10-06
okey, fixed them now.
But they dont have to do with the problem i have?

---

### Post by Macchi on 2009-06-10
> **qwerdy said:**
> Hi,

I'm looking for a way to manage files on my server.
As for now i use putty to move/copy/rename... 
But it's very bothersome.

I dont have X/gui installed, so remote desktop is not a solution.

I'm now using Windows Vista on my desktop pc, but when i used XP i could move files from mounted samba shares to antoher mounted samba share, and it would move it directly on the server. But when i try that in Vista its goes throug my desktop pc, so its going really slow.

Any one have any suggestions for a easy remote file manager solutions?



It was long ago anyone posted answers here, but I will mention a solutionjust in case someone else has the same problem.

To access files on your Ubuntu server simply install openssh-server on the server and access your files through an encrypted ssh channel with nautilus in Ubuntu, or with Filezilla in  Windows or Mac OS X. Or any preferred method to access sftp.
 
Use a strong password, so you wont risk getting hacked in a few seconds. For increased security even close the port 22, and redirect ssh to a different (non-standard) port.

I can post a more detailed description of how to accomplish this, please send a message.


PS: By the way if you want to experiment with a remote desktop through internet then you should try Nomachine's NX server, that is available for Linux, Solaris, Mac and Windows.
It is simple, safe and very efficient even on slow and distant lines. I could run a desktop from Brussels on a machine in Stockholm through a slow ADSL line. Unfortunately that software artifact is not free as speech and the free server is only free as beer, having a very low limit of two users, that may be very irritating for most people.

---

