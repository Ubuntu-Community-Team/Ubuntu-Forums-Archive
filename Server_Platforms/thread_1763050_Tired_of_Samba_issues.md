---
title: "Tired of Samba issues"
date: 2011-05-19
forum: Server Platforms
---

### Post by Ghosthaven on 2011-05-19
I've been fighting with Samba for two days now and I'm about
ready to give up.

I have it setup, used system-config-samba to configure it and it
still messes up.

All I want is for it to act exactly like a normal windows XP
share.
I don't want it to only work on some computers.
I don't want it to require any form of username or password.
I don't care in any way about security as long as its not visible
beyond my LAN.

All I want is for all files shared to be visible on my entire
network... just like a windows share.

Is there any way I can do this without a huge hassle?

I'm about at the end of my rope... I'm actually considering
making a windows VM just to share my files :(

---

### Post by arrrghhh on 2011-05-19
I have exactly what you describe setup - no users/passes, everyone can access the box, and it's not accessible outside my LAN.

Post your samba configuration file.  I configured with Webmin cuz I'm lazy, and had issues with samba at first myself - perhaps you should try that...?

---

### Post by Ghosthaven on 2011-05-20
Thank you so much for your help. This is driving me insane...
You'd expect the process to be very simple nowadays.

I haven't manually changed my smb.conf file at all so hopefully
its not too much of a mess.

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
	workgroup = mygroup

# server string is the equivalent of the NT Description field
	server string = %h (Samba, Ubuntu)

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
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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
;	printing = cups
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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	security = share
;	guest ok = no
;	guest account = nobody

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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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

[Public]
	path = /home/andy/Public
	writeable = yes
;	browseable = yes
	guest ok = yes

[Download]
	path = /home/andy/Downloads/Torrents/Download
	writeable = yes
;	browseable = yes
	guest ok = yes


```

---

### Post by volkswagner on 2011-05-20
One thing to help visibility is to add your servers hostname under workgroup name.

```
 netbios name = fileservername
```

To get your hostname run

```
hostname
```

You can also try adding the following to share definitions:

```
guest ok = yes
```


Can you see your shares from windows?  What happens when you try to connect?  Is file sharing working in windows already, can you share windows to windows?

---

### Post by Morbius1 on 2011-05-20
The [global] section of your smb.conf looks factory fresh so I don't think that's the problem. You have two shares defined:
> [Public]
    path = /home/andy/Public
    writeable = yes
;    browseable = yes
    guest ok = yes

[Download]
    path = /home/andy/Downloads/Torrents/Download
    writeable = yes
;    browseable = yes
    guest ok = yesThe only way that's going to work is if you make sure that Linux file permissions match the samba authorization of guest access:
```
sudo chmod 777 /home/andy/Public
sudo chmod 777 /home/andy/Downloads/Torrents/Download
```OR, you can leave the permissions alone and add a line to each share definition: force user = andy ( which will also take care of another problem you haven't yet but will experience):
> [Public]
    path = /home/andy/Public
    writeable = yes
;    browseable = yes
[COLOR=Blue]     foce user = andy[/COLOR]
    guest ok = yes

[Download]
    path = /home/andy/Downloads/Torrents/Download
    writeable = yes
;    browseable = yes
[COLOR=Blue]      force user = andy[/COLOR]
    guest ok = yesAfter making any changes to smb.conf you must restart samba:
```
sudo service smbd restart
```Beyond this if the problem is browsing to the shares then please post the output of the following command:
```
smbtree
```

---

### Post by arrrghhh on 2011-05-20
Heh, I always forget about that smbtree command.

You're in good hands here Ghosthaven, let us know how it goes.

---

### Post by Ghosthaven on 2011-05-20
Still having problems :(

Volkswagner:
Where do I add the guest ok = yes? Its already under each of the two shared
folders and there are several other places that have guest ok = yes or = no
commented out. Where do I change it?

And yes, I can see the shares from any windows computer I try. Sharing windows
to windows is working fine for four other computers on the network.

Mobius1:
I'm only somewhat comfortable with the CLI, so I tried to setup the permissions
using the GUI. I went into sharing options and set everything there, then it
said it needed to change the permissions so I assumed that it was setup ok. I
went ahead and chmoded them to 777 though.

I also added the force user lines.

Running smbtree (I had to install the smbclient package to get it) did
reveal something that doesn't look right... in the section about the server
(I called it server, how original, right?) it has:

```

    \\SERVER                 server (Samba, Ubuntu)
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

```Unfortunately its all greek to me. Any clue what that error means?

Finally I wanted to thank you all for your help. After Unity came out I
considered trying to find another distro, but the Ubuntu community is more
than worth staying for. Thank you.

---

### Post by arrrghhh on 2011-05-20
> **Ghosthaven said:**
> Running smbtree (I had to install the smbclient package to get it) did
reveal something that doesn't look right... in the section about the server
(I called it server, how original, right?) it has:

```

    \\SERVER                 server (Samba, Ubuntu)
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

```Unfortunately its all greek to me. Any clue what that error means?

Paste the **entire** output from smbtree please...

---

### Post by Morbius1 on 2011-05-20
You should not be getting a lanman error from any modern samba server. Go back into your smb.conf and find the following line:
> # Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
**[COLOR=Blue]    security = share[/COLOR]**
;    guest ok = no
;    guest account = nobodyAnd put a # in front of it so that it looks like this:
> # Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
**[COLOR=Blue]#    security = share[/COLOR]**
;    guest ok = no
;    guest account = nobodyThen restart samba:
```
sudo service smbd restart
```

**EDIT: Then run smbtree again and post the output**

---

### Post by Ghosthaven on 2011-05-20
Well we're a lot closer to what I'd like, I can log on to the server from almost any computer on the network
now and actually transfer files back and forth, but before I can get a shared list I have to put in my username and password (for the andy account). This is new by the way, I didn't have to do this before.
While its not exactly what I hoped for, I can manage with this.

I'd still like to get it completely password free if possible though.

Also, the lanman error disappeared with the change Morbius1 suggested.

Here is the complete contents of the smbtree command:
```

MYGROUP
    \\XPMEDIA                
cli_start_connection: failed to connect to XPMEDIA<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
    \\X                      X
        \\X\Shared Music       
        \\X\setup              
        \\X\IPC$               Remote IPC
        \\X\filesharing        
    \\STARDUST               
        \\STARDUST\IPC$               Remote IPC
        \\STARDUST\filesharing           
    \\SERVER                 server (Samba, Ubuntu)
        \\SERVER\IPC$               IPC Service (server (Samba, Ubuntu))
        \\SERVER\Download           
        \\SERVER\Public             
        \\SERVER\print$             Printer Drivers
    \\ROBERT-DESKTOP         Robert's Computer
cli_start_connection: failed to connect to ROBERT-DESKTOP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
    \\HAVEN                  haven server (Samba, Ubuntu)
        \\HAVEN\homes              Home Directories
        \\HAVEN\print$             Printer Drivers
        \\HAVEN\IPC$               IPC Service (haven server (Samba, Ubuntu))

```I'm assuming the NT_STATUS_BAD_NETWORK_NAME is a result of
those two systems being shutdown. Not sure why they'd still be in this
list if offline though.

and here is an updated copy of my smb.conf file:
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
    workgroup = mygroup
# My change 1
netbios name = server
# server string is the equivalent of the NT Description field
    server string = %h (Samba, Ubuntu)

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
;    encrypt passwords = yes

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
#    security = share
;    guest ok = no
;    guest account = nobody

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

[Public]
    path = /home/andy/Public
    writeable = yes
;    browseable = yes
    force user = andy
    guest ok = yes

[Download]
    path = /home/andy/Downloads/Torrents/Download
    writeable = yes
;    browseable = yes
    force user = andy
    guest ok = yes

```I'm just curious, but why am I having so many problems? This is an almost completely fresh install
of ubuntu on a fully functional home network... did I do something wrong and not realize it? I'd like to
know what so I can avoid this problem in the future.

---

### Post by Morbius1 on 2011-05-21
If you're getting a listing of hosts in smbtree from machines that are no longer on the network then something is truly wrong somewhere. Asking for authentication before getting the list of shares indicates there's still something wrong with passwords and authentication. 

Let's start with permissions along the entire path to the shared directory and let's start with the easier path:
```
ls -al /home/andy
```The first two lines of the output should look something like this:
> drwxr-xr-x 71 andy andy    4096 2011-05-21 06:44 .
drwxr-xr-x  9 root  root     4096 2011-05-12 07:08 ..

The first line with the single "." at the end represents /home/andy.
The second line represents /home itself.

Further down the output should be the Public folder and it should look like this:
> drwxrwxrwx  2 andy andy    4096 2011-05-11 15:22 PublicIs this what you see?

---

### Post by volkswagner on 2011-05-21
```
Error NT_STATUS_BAD_NETWORK_NAME
```

The above error is a DNS issue.

Check this tread for some very [helpful hints on SAMBA]("http://ubuntuforums.org/showthread.php?t=1169149")

Follow the steps related to install winbind and /etc/nsswitch.

Local DNS can be a pain.  I personally use my router as DNS server.  In doing this I setup static ip's using the router mapping MAC address to an ip.  Then use DHCP in /etc/network/interfaces... this approach seems to help resolve host names locally for me. It also allows static ip's for wireless devices, without issue when the laptop travels to other networks!

---

### Post by Morbius1 on 2011-05-21
Well, it's curiouser than that since he's getting that error messages from systems that are not on the lan.
> I'm assuming the NT_STATUS_BAD_NETWORK_NAME is a result of
those two systems being shutdown. Not sure why they'd still be in this
list if offline though.
The winbind / nsswitch boogabooga-witchcraft thing is supposedly to resolve browsing issues but:
> Well we're a lot closer to what I'd like, I can log on to the server from almost any computer on the network
now and actually transfer files back and forthAnd besides he can see them all in smbtree.

It's possible I suppose that he is part of an Active Directory or other complex network that would make winbind part of the solution but it sure does sound like some kind of password encryption / pam / file permissions problem to me.

But, hey if installing say ... Gimp resolves this problem then why not try it. On the other hand I can show you how purging the system of winbind has resolved samba issues: [http://ubuntuforums.org/showthread.php?t=1749823](http://ubuntuforums.org/showthread.php?t=1749823)

---

### Post by volkswagner on 2011-05-21
I say winbind only because I had the same exact issue, which was rectified simply by installing winbind.

```
eric@fileserver:~$ smbtree
Enter eric's password: 
WAGNERHOUSE
	\\TABLET         		
cli_start_connection: failed to connect to TABLET<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\SERVER2008     		Server 2008 VirtualMachine XenServer
cli_start_connection: failed to connect to SERVER2008<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\MINI           		Mini server (Samba, Ubuntu)
		\\MINI\backup-mini    	
		\\MINI\downloads      	
		\\MINI\IPC$           	IPC Service (Mini server (Samba, Ubuntu))
		\\MINI\print$         	Printer Drivers
	\\LANDISK        		LinkStation
cli_start_connection: failed to connect to LANDISK<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\HPMCE          		masterbedroom
cli_start_connection: failed to connect to HPMCE<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\FILESERVER     		fileserver server (fileserver)
		\\FILESERVER\eric           	Home Directories
		\\FILESERVER\IPC$           	IPC Service (fileserver server (fileserver))
		\\FILESERVER\print$         	Printer Drivers
		\\FILESERVER\mymedia        	All Users
		\\FILESERVER\public         	All Users
	\\ACER           		
cli_start_connection: failed to connect to ACER<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
eric@fileserver:~$ sudo apt-get install winbind
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  winbind
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,408kB of archives.
After this operation, 12.2MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main winbind 2:3.4.7~dfsg-1ubuntu3.5 [4,408kB]
Fetched 4,408kB in 7s (570kB/s)                                                
Selecting previously deselected package winbind.
(Reading database ... 50577 files and directories currently installed.)
Unpacking winbind (from .../winbind_2%3a3.4.7~dfsg-1ubuntu3.5_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up winbind (2:3.4.7~dfsg-1ubuntu3.5) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 

eric@fileserver:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 709
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:13:46:8e:04:4f
Sending on   LPF/eth0/00:13:46:8e:04:4f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:13:46:8e:04:4f
Sending on   LPF/eth0/00:13:46:8e:04:4f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.21 from 192.168.1.1
DHCPREQUEST of 192.168.1.21 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.21 from 192.168.1.1
bound to 192.168.1.21 -- renewal in 841502137 seconds.
ssh stop/waiting
ssh start/running, process 1206
                                                                         [ OK ]
eric@fileserver:~$ smbtree
Enter eric's password: 
WAGNERHOUSE
	\\TABLET         		
	\\SERVER2008     		Server 2008 VirtualMachine XenServer
		\\SERVER2008\Users          	
		\\SERVER2008\Public         	
		\\SERVER2008\IPC$           	Remote IPC
		\\SERVER2008\C$             	Default share
		\\SERVER2008\ADMIN$         	Remote Admin
	\\MINI           		Mini server (Samba, Ubuntu)
		\\MINI\backup-mini    	
		\\MINI\downloads      	
		\\MINI\IPC$           	IPC Service (Mini server (Samba, Ubuntu))
		\\MINI\print$         	Printer Drivers
	\\LANDISK        		LinkStation
		\\LANDISK\backup         	backup folder mounted on Mini
		\\LANDISK\vivid          	Vivid
		\\LANDISK\iso            	iso files
		\\LANDISK\mydocuments    	MyDocuments on Virtual Machine-Rene
		\\LANDISK\music          	mp3-files
		\\LANDISK\photos         	My Pictures
		\\LANDISK\video          	Video Files and Archive TV
		\\LANDISK\share          	LinkStation Share Folder
		\\LANDISK\info           	LinkStation information
		\\LANDISK\lp             	Network Printer for Windows
	\\HPMCE          		masterbedroom
		\\HPMCE\H              	
		\\HPMCE\C$             	Default share
		\\HPMCE\ADMIN$         	Remote Admin
		\\HPMCE\SD             	
		\\HPMCE\E              	
		\\HPMCE\F$             	Default share
		\\HPMCE\G$             	Default share
		\\HPMCE\SharedDocs     	
		\\HPMCE\D$             	Default share
		\\HPMCE\IPC$           	Remote IPC
		\\HPMCE\videofiles     	
		\\HPMCE\E$             	Default share
		\\HPMCE\Recorded tv    	
	\\FILESERVER     		fileserver server (fileserver)
		\\FILESERVER\eric           	Home Directories
		\\FILESERVER\IPC$           	IPC Service (fileserver server (fileserver))
		\\FILESERVER\print$         	Printer Drivers
		\\FILESERVER\mymedia        	All Users
		\\FILESERVER\public         	All Users
	\\ACER           		
		\\ACER\Ro-Documents   	
		\\ACER\IPC$           	Remote IPC

```

---

### Post by Morbius1 on 2011-05-21
Usually when I encounter that specific problem on someone's machine I fix it by changing the "name resolve order" to have have bcast first:
```
name resolve order = bcast host lmhosts wins
```
It's not so important that it's first as it is that it's prior to wins. bcast is the only one of the options that's functional out of the box and sometimes "win" leaves the network and goes to the users ISP's DNS servers in a valiant attempt to find a WINS server to resolve a machine name and never comes back to try bcast. It seems to happen a lot when the users ISP uses "DNS Redirect".

---

### Post by volkswagner on 2011-05-21
> **Morbius1 said:**
> Usually when I encounter that specific problem on someone's machine I fix it by changing the "name resolve order" to have have bcast first:
```
name resolve order = bcast host lmhosts wins
```
It's not so important that it's first as it is that it's prior to wins. bcast is the only one of the options that's functional out of the box and sometimes "win" leaves the network and goes to the users ISP's DNS servers in a valiant attempt to find a WINS server to resolve a machine name and never comes back to try bcast. It seems to happen a lot when the users ISP uses "DNS Redirect".

Thank you...

Not to hijack but changing the resolve order in /etc/samba/smb.conf is sufficient to fix the nt error.  I purged winbind and performed the edit and no longer get the error.  I was sure that I tried it int the past, but must have done it wrong!

EDIT:  This approach was not a fix all form my Laptop running 10.04 Desktop.

```

	\\LANDISK        		LinkStation
cli_rpc_pipe_open_noauth: rpc_pipe_bind for pipe \srvsvc failed with error NT_STATUS_UNSUCCESSFUL
```

LANDISK is a NAS which has mounted shares in /etc/fstab.  The above still happens even after reboot.  The shares mount fine and are accessible via Nautilus.

Sorry for the somewhat hijack, but I hope it is all relevant.

Getting the same thing now on my server with no shares mounted... looks like for me, I'm back to winbind.

PS:  I get the following for machine in poweroff state.

```

\\LX366          		
cli_start_connection: failed to connect to LX366<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE

```

---

### Post by headvampyre@hotmail.co.uk on 2011-05-21
For name resolution, try changing:

dns proxy = no
wins support = no

to:

dns proxy = yes
wins support = yes

After this, make sure you uninstall Ubuntu's winbind packaes, as they WILL break Samba's winbind server.

---

### Post by capscrew on 2011-05-21
> **headvampyre@hotmail.co.uk said:**
> For name resolution, try changing:

dns proxy = no
wins support = no

to:

dns proxy = yes
wins support = yes

After this, make sure you uninstall Ubuntu's winbind packaes, as they WILL break Samba's winbind server.

From your perspective; what is a* winbind server*?  How do you see winbind's relationship to hostname or COMPUTER NAME resolution.  Could you provide some examples and references to your thoughts?

Why are you suggesting this? ```

dns proxy = no
wins support = no

to:

dns proxy = yes
wins support = yes
```

---

### Post by Ghosthaven on 2011-05-22
I'm going through each of your suggestions, with no success yet.

I'm seriously considering just wiping everything and installing a fresh copy of 10.10 (not a big fan of 11.04).
From that point on I'll just follow the instructions at [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

Do you guys think that'll fix my problems? I've spent so much of both my and your time fighting samba,
that it almost seems not worth the struggle. I can't believe I'm considering installing Windows instead :(

If I do wipe it, is that guide still up to date enough to work?

---

### Post by Morbius1 on 2011-05-22
If your going to reinstall I would suggest setting up a samba share in the easiest way possible and that's using Nautilus - exactly ( almost ) the way you would set up a simple share in WinXP:

Open Nautilus
Right click a folder you own say ... Documents
Select "Sharing Options"
At this point if you don't have Samba installed it will ask you if you want to install it ( it calls it windows networking ) - you do.
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

Do it before you do anything with a firewall or any thing else.

The method above called usershare or nautilus-share does everything for you. It will install Samba on first use, it will modify permissions automatically so you don't have to bother with it, it will set up a share that does not require usernames or passwords, and you'll set up a share in 15 seconds.

---

### Post by Morbius1 on 2011-05-22
In the mean time why not post the make and model of whatever router you're using so we can see if it can assign static ip address to all your machines. It's called "DHCP Reservation" but it can go by other names. Static ip address are your friend in networks with the kind of problems you seem to be having.

---

### Post by Ghosthaven on 2011-05-22
Alright... I guess I'll backup what I have and start towards
a reinstall.

As far as my router, I'll go ahead and layout my entire LAN:
```

Fiber Optic -> Vonage device -> Linksys WRT54G -> 2 comps+server
                                       |
                                       v
                               Netgear WGT624 -> 2 comps+old server

```

All "comps" are win XP machines, the old server is an ancient
pentium with ubuntu server 10.04 and the new server is the one
I'm having problems with.

The Netgear router has both DHCP and wireless disabled so it
acts like a normal network switch.

I usually edit /etc/network/interfaces to assign a static ip to
any ubuntu box. Is this a bad choice over using my router to do
it?

I just had a thought... running two ubuntu boxes as Samba hosts
wouldn't cause any of these problems, would it?

---

### Post by capscrew on 2011-05-22
> **Ghosthaven said:**
> Alright... I guess I'll backup what I have and start towards
a reinstall.

As far as my router, I'll go ahead and layout my entire LAN:
```

Fiber Optic -> Vonage device -> Linksys WRT54G -> 2 comps+server
                                       |
                                       v
                               Netgear WGT624 -> 2 comps+old server

```

All "comps" are win XP machines, the old server is an ancient
pentium with ubuntu server 10.04 and the new server is the one
I'm having problems with.

The Netgear router has both DHCP and wireless disabled so it
acts like a normal network switch.
More importantly are all the machines on the same subnet?> 

I usually edit /etc/network/interfaces to assign a static ip to
any ubuntu box. Is this a bad choice over using my router to do
it?

This is absolutely the most stable way.  I have machines that have had no networking problems in 5+ years.  I have uptimes of greater than 1 year.> 

I just had a thought... running two ubuntu boxes as Samba hosts
wouldn't cause any of these problems, would it?

Multiple hosts running Samba is fine, just as file sharing on multiple Windows hosts.

You really don't have to reinstall just to reconfigure Samba.  All the configuration is in just a few files.  The main configuration file is /etc/samba/smb.conf.  The other files are at /var/lib/samba/usershares.

You should have a good understanding of TCP/IP networking and local LAN nameservies (e.g DNS and NetBIOS).  Without proper nameservices you will never have satisfactory network share browsing.

See [**_[COLOR="Blue"]here [/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1749823&highlight=atomicben")for my thoughts.  The answers are from post #6 on.

---

### Post by Morbius1 on 2011-05-23
I can usually hold my own with anyone concerning Samba but capscrew knows more about the network than I do. The two are related but not the same. I run the risk of being corrected by capscrew on this but these are my thoughts:

As capscrew stated you need to make sure that all of the ip addresses on this network are on the same subnet for the default host identification mechanism to work. You can make it work if they are not but it can get involved. So if you have some machines in the 192.168.0.xxx range and some in the 10.0.0.xx range then let us know.

> I usually edit /etc/network/interfaces to assign a static ip to
any ubuntu box. Is this a bad choice over using my router to do
it?I'm going to deviate a bit from capscrew on this one. If most of your assets are fixed ( i.e., desktops ) then you can assign the address your way as long as the ip address is still in the same subnet but outside the range of the routers DHCP pool. If the router is set to assign ip addresses from say 192.168.0.100 - 192.168.0.150 then set your ip address to be greater than 192.168.0.150. Otherwise the router may assign the same ip address to some other machine.

With an ever increasing population of mobile devices ( laptops, tablets, etc.. ) it makes more sense to me to keep all machines at the default configuration as a dhcp client and have the router set static ip addresses. This way none of the machines have to be altered and the mobile device can adapt to whatever network environment it finds itself.
> I just had a thought... running two ubuntu boxes as Samba hosts
wouldn't cause any of these problems, would it?                      In a home LAN these machines are more in a peer-to-peer configuration - every machine is both a server and a client to everyone else - so it doesn't matter.

If you have static ip addresses on all your machines you no longer need to browse to their locations. You can set up lookup tables ( hosts files ) or simply bookmark them is nautilus - the way you would set up a "mapped drive" in Windows.

---

### Post by Morbius1 on 2011-05-23
Well, all this talk about DHCP reservation is irrelevant. The Linksys WRT54G does not seem capable of doing that. The Netgear WGT624 can but it's configured as a Wireless Access Point and not a DHCP server.

---

### Post by arrrghhh on 2011-05-23
> **Morbius1 said:**
> Well, all this talk about DHCP reservation is irrelevant. The Linksys WRT54G does not seem capable of doing that. The Netgear WGT624 can but it's configured as a Wireless Access Point and not a DHCP server.

To the OP - is this the issue?  I've tried following the thread, but I never saw the answer - if you only have issues with machines on the Netgear WAP, then you need to get them on the same subnet as was previously suggested...  IF they're not on the same subnet, you'll need to setup routing between the devices so they can be aware of eachother's network.

Please correct me if I'm wrong, but it seems like you have two routers with different subnets - basically you have two LAN's.

---

### Post by Ghosthaven on 2011-05-23
First, replies:
All computers on the network were on the same subnet, the second
router was configured to disable DHCP, wireless (because it was
faulty, which is the reason why I got the linksys router in the
first place) and had its ip assigned to within the subnet mask
(but outside of the linksys router's dhcp list).

In other words, the second router is configured to be absolutely
nothing more than a normal "smart" switch (as opposed to a "dumb"
switch that broadcasts traffic instead of routing it).

As far as assigning the static IP, I didn't know it had to be
outside of the normal DHCP list, I had just assumed that the
router wouldn't assign double if it detected a system with that
IP. So thanks for letting me know, you most likely saved me a ton
of frustration :)

Second: It works!
I decided to go ahead and wipe and start over to avoid any
frustration. I'm not sure where I messed everything up, it could
have been because I installed Ubuntu server first and then the
ubuntu-desktop package on top of it (I wanted the pre-configured
LAMP setup from server because I know jack about setting it up.).

Or it could have been because I had re-installed Samba after I
first had it ask for a password (most likely cause I had it
incorrectly configured).

Either way, it works perfectly now. All I had to do was use
nautilus to set everything up (As Mobius1 suggested) then edit
smb.conf by hand to enter the correct workgroup name (is there
any way to do that in a more GUI-ish way without installing any
other configuration software?)

I also checked smbtree and its completely clean of errors :)

Thank you all for suffering with me through this. Its been a real
learning experience!

---

### Post by arrrghhh on 2011-05-23
> **Ghosthaven said:**
> Either way, it works perfectly now. All I had to do was use
nautilus to set everything up (As Mobius1 suggested) then edit
smb.conf by hand to enter the correct workgroup name (is there
any way to do that in a more GUI-ish way without installing any
other configuration software?)

Server's don't have a GUI, so I don't think there is (short of installing other config software, which you seemed against).

There's also some web-UI based config software that works fairly well - lookup webmin and ebox.

---

### Post by Morbius1 on 2011-05-23
arrrghhh, He's using Gnome on top of his Server which is how he created the samba share in Nautilus.

Ghosthaven, I don't know of any GUI utility that can change the hostname without literally turning your smb.conf into an incoherent mess.

---

### Post by arrrghhh on 2011-05-23
> **Morbius1 said:**
> arrrghhh, He's using Gnome on top of his Server which is how he created the samba share in Nautilus.

My condolences.

---

