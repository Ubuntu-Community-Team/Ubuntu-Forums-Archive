---
title: "Needs some help with Samba"
date: 2014-05-21
forum: Server Platforms
---

### Post by Rocket J Squirrel on 2014-05-21
Ubuntu 12.04 sharing files to Windows machines with Samba

Getting a lot of errors related to Samba 

"Sorry, Ubuntu 12.04 has experienced an internal error" and the error pertains to /usr/bin/smbd

and Ubuntu has me fill out a error report and requests permission to include the contents of /etc/samba/smb.conf, /var/log/samba/log.smbd and /var/log/samba/log.nmbd -- which I do every time. But the problem persists. 

I wonder if there's someone here who would like to eyeball the files and see if there's anything fishy looking? 


Here is log.nmbd:
```
[2014/05/21 08:21:11,  0] nmbd/nmbd.c:860(main)
  nmbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
```

Here is log.smbd:
```
[2014/05/21 08:21:08,  0] smbd/server.c:1051(main)
  smbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2014/05/21 08:21:09.312365,  0] smbd/server.c:1107(main)
  standard input is not a socket, assuming -D option
[2014/05/21 08:21:12.224942,  0] printing/print_cups.c:110(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2014/05/21 08:21:12.225442,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
```


Here is smb.conf (standard text at top clipped):
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = CCIRCLE

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

# Following is meant to disable browsing this
# computer's printers across network
    disable spoolss = yes

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

[CCD_Staff]
    path = /home/filestation/Documents/CCD_Staff
    writeable = yes
;    browseable = yes
    guest ok = yes

[CCD_Admin]
    path = /home/filestation/Documents/CCD_Admin
    writeable = yes
;    browseable = yes
    valid users = filestation, jacquie, moxford, sysadmin

[scans]
    comment = CCD Scans
    path = /home/filestation/Documents/CCD_Staff/scans
    writeable = yes
;    browseable = yes
    guest ok = yes


```

Any help would be appreciated!

---

### Post by squakie on 2014-05-22
Did you try running testparm to see if your smb.conf file is accepted?

---

### Post by Rocket J Squirrel on 2014-05-22
Squakie, thank you. No I hadn't run testparm. It returns no warnings.

---

### Post by squakie on 2014-05-22
I don't much about this as I've always kept mine pretty simple, "but"......

I noticed your share definitions for printing going to a spool file.  I also notice the smbd.log file mentions it had problems with printers.  Perhaps you should try commenting out that share just to see if it works ok, then go back to finding what *might* be wrong in that share definition.  I don't know if the printer share definition sample further up smb.conf can be of help to you or not.

Wish I could help you more, but I don't want to make a mess of things.

---

### Post by Rocket J Squirrel on 2014-06-09
Squakie, thanks for giving it a shot! I commented out the printer share, as you suggested, and testparms issues an error. 

Can anyone point me to a forum where I can get help with this samba question?

---

### Post by Rocket J Squirrel on 2014-06-10
I posted a question in General Help but the thread seems to have fizzled out.

Thought I'd pop over here in Networking & Wireless to see if anyone has a suggestion. Please take a look at : [http://ubuntuforums.org/showthread.php?t=2225479](http://ubuntuforums.org/showthread.php?t=2225479)

---

### Post by cariboo on 2014-06-10
Please don't create multiple threads on the same subject, I have merged your two threads, and moved it to server platforms, as this is a server problem.

---

### Post by Rocket J Squirrel on 2014-06-10
Thanks, cariboo907. Maybe someone here can eyeball the problem and offer suggestions.

---

### Post by bab1 on 2014-06-11
> **Rocket J Squirrel said:**
> Ubuntu 12.04 sharing files to Windows machines with Samba

Getting a lot of errors related to Samba 

"Sorry, Ubuntu 12.04 has experienced an internal error" and the error pertains to /usr/bin/smbd

and Ubuntu has me fill out a error report and requests permission to include the contents of /etc/samba/smb.conf, /var/log/samba/log.smbd and /var/log/samba/log.nmbd -- which I do every time. But the problem persists. 

Whats the problem?  I don't see any comments from you that indicate a problem.  Is Samba working or not.  If not, how so?  Be specific.

The message "Sorry, Ubuntu 12.04 has experienced an internal error" is an Apport error pop up.  If you google the term "Sorry, Ubuntu 12.04 has experienced an internal error" you will see information about this.
> 

I wonder if there's someone here who would like to eyeball the files and see if there's anything fishy looking? 


I assume you mean of the error generating kind, eh?
> 

Here is log.nmbd:
```
[2014/05/21 08:21:11,  0] nmbd/nmbd.c:860(main)
  nmbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
```

Nothing here that is out of order.
> 

Here is log.smbd:
```
[2014/05/21 08:21:08,  0] smbd/server.c:1051(main)
  smbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2014/05/21 08:21:09.312365,  0] smbd/server.c:1107(main)
  standard input is not a socket, assuming -D option
[2014/05/21 08:21:12.224942,  0] printing/print_cups.c:110(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2014/05/21 08:21:12.225442,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
```

Nothing here either.  The message just states that you have not connected to a CUPS printer.  It won't affect Samba.
> 

Here is smb.conf (standard text at top clipped):
```
#======================= Global Settings =======================
...


```
Nothing that would cause Apport to pop up.

>  ... No I hadn't run testparm. It returns no warnings. 
What returns no warnings?

If all you have is an Apport pop up every once in a while and Samba is working properly, I would think about disabling the pop-up.

---

### Post by Rocket J Squirrel on 2014-06-11
BAB1, thank you.

It's true: Samba is working, and the only indication that there might be a problem is the popup telling me that there is an error. When a trouble light comes on on a car dashboard, it could mean a problem with the engine, or a problem with the trouble-sensing system. I'm not the sort to just disable the trouble-sensing system w/o checking with someone who can take a look at the engine first. It was suggested earlier in the thread (when I started the thread in a different forum) that I run testparm, and it returned no warnings. And since you saw no problems in smb.conf or the two logs, and Samba is working fine, I guess I just have a problem with the trouble-sensing system and can ignore it. Many thanks for taking a look.

---

