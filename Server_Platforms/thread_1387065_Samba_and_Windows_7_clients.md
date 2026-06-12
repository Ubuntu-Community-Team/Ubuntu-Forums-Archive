---
title: "Samba and Windows 7 clients ?"
date: 2010-01-21
forum: Server Platforms
---

### Post by yesrno on 2010-01-21
Hello,
Recently I have installed the Ubuntu 9.10 server edition, i'm really happy about the functionality and just wanted to say good job and thanks to everyone here. 
However.. I do have some problem with creating file shares, with Samba.

I created the following share in Samba:
```

[share]
    comment = share
    writeable = yes
    path = /share
    guest ok = no
    read only = no

```However when I try to connect to it with a Windows 7 client I get the following error:
```

\\server\share is not accessible.
You might not have permission to use this network resource.
Contact the administrator of this server to find out if you have access permissions.

Multiple connections to a server or shared resource by the same user, 
using more then one user name, are not allowed.
Disconnect all previous connections to the server or shared resource and try again.

```I really tried alot of options and different settings but just can't seem to figure it out. Here some things that might help.

I'm sure all the users i'm trying to connect with are samba users.
Already tried the "Send LM & LTLM - use NTLMv 2 option in secpol
Does however work if I put "Guest ok = yes" instead of no.
Using Samba 3.4.0-3ubuntu5.3
Mmm if you need any more info just post!

 I was hoping someone here could help me.
Thanks in advance!

---

### Post by gobbledigook on 2010-01-21
Hi, you may get better troubleshooting if you post your whole smb.conf file :)

i checked mine and my share section looks like:
```
[server]
path = /media/server
browseable = yes
writeable = yes
public = yes
executable = yes

```

was wondering if you need the browseable option? plus is the dir you want to share in your root dir?
```
 path = /share
```

cause i'm sharing whole disks mounted in /media? so was wondering if maybe your path was incorrect

---

### Post by yesrno on 2010-01-21
Hello,
Yes the browseable option is handy thank you, however.. It doesn't fix it.
And yea the /share is on the root. I was just testing some things with it thats why the place if you're wondering :p
Underneath is my full config, the share is at the bottom. Hope it helps!


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
   netbios name = MissUbuntu    
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


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[share]
    comment = share
    writeable = yes
    path = /share
    guest ok = no
    read only = no

```

---

### Post by Xianath on 2010-01-21
yesrno: Looks like you have another share on the same server accessed as guest or another user who doesn't have access to this share. Windows caches your password(s) on a per-server basis. It's also possible that you need to specify the username as WORKGROUP\username.

From the command prompt, you can use "net share ..." to view and disconnect active shares, or store a password for a server/share, make a permanent mount etc. You also have these options in your profile folder but I've seen it fail to work for some people in W7, probably because of tightened security settings around passwords. Plus, with an administrator shell, you can do system-wide mounts.

gobbledigook: Shares do not have to be browseable and they can also be hidden and Windows can still access them. A lot of people stake their dignities on that fact :)

HTH,
Peter

---

### Post by Morbius1 on 2010-01-21
Have you done a:

**sudo smbpasswd -a *username***

corresponding to the client user that's trying to access the server share?

---

### Post by yesrno on 2010-01-21
Morbius1 Yes I did, without any luck tho because the error remains.
And Xianath I did created some public shares on the server and connected to them as a "guest", yes. You think that might be a problem ? I couldn't really find a quick way to disconnect shares with net use.

---

### Post by Xianath on 2010-01-21
I believe "net show" is what you're looking for but let me get back home to my Windows box and I'll check the exact syntax for you. Until then, "net help" is your friend.

Cheers,
Peter

---

### Post by yesrno on 2010-01-21
Okay well I restarted the Windows 7 thinking that would certainly disconnect the network shares. After the reboot everything worked fine and I could just enter the share with my correct username and password. So seems it is fixed :)

Thanks alot everyone, really appreciate it!

---

### Post by Xianath on 2010-01-22
Sorry I couldn't reply earlier but glad you figured it out. It's Windows, rebooting usually helps :) For a more permanent solution, try this: Open your profile (in the start menu, click your user icon). From there, go to "Manage your credentials" and store your SAMBA password there. It's per host, so this should solve your problems. You can also mount a drive permanently and remember the credentials, either through the UI or through "net use" on the command line, which basically does the same in terms of saving your password.

Regards,
Peter

---

### Post by waygooder on 2010-10-25
> **Xianath said:**
> yesrno: Looks like you have another share on the same server accessed as guest or another user who doesn't have access to this share. Windows caches your password(s) on a per-server basis. It's also possible that you need to specify the username as WORKGROUP\username.

From the command prompt, you can use "net share ..." to view and disconnect active shares, or store a password for a server/share, make a permanent mount etc. You also have these options in your profile folder but I've seen it fail to work for some people in W7, probably because of tightened security settings around passwords. Plus, with an administrator shell, you can do system-wide mounts.

gobbledigook: Shares do not have to be browseable and they can also be hidden and Windows can still access them. A lot of people stake their dignities on that fact :)

HTH,
Peter

Dude I went through about 5 pages of google searches before I found this. This solved my problem. Deleted my drive mapping of the other share on this server and it worked. Thanks!!

---

### Post by Vegan on 2010-10-25
I have several Windows machines connected to my Linux box, never a problem, but I did notice a bad NIC today when I upped my new server. Replaced it and now its back up to speed. Surprised as its rare to have a dodgy NIC.

I do suggest if you have lots of SAMBA clients (users), get lots of RAM for the server.

---

### Post by luvshines on 2010-10-25
> **yesrno said:**
> Okay well I restarted the Windows 7 thinking that would certainly disconnect the network shares. After the reboot everything worked fine and I could just enter the share with my correct username and password. So seems it is fixed :)


You can also use ```
## To delete all network mapped shares
net use * /delete
```

For deleting a particular mapping, use net use <mapdevice: network-path> /delete
[http://technet.microsoft.com/en-us/library/bb490717.aspx](http://technet.microsoft.com/en-us/library/bb490717.aspx)

---

### Post by Vegan on 2010-10-25
I have several servers but only one on all the time.

Each has its own unique name on the network and Windows XP and up all see the servers fine.

If there is a problem recognizing servers, make sure your servers are setup properly.

---

