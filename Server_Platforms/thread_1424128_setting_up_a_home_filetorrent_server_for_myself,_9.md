---
title: "setting up a home file/torrent server for myself, 9.10"
date: 2010-03-07
forum: Server Platforms
---

### Post by systemchris on 2010-03-07
i've played with ubuntu for quite a while now and i picked up a atom core mini pc for cheap so i thought i'd make a hobby in setting up a simple server to store files on, access files on my xbmc enabled xbox and download torrents whilst i'm at work :) though the torrents can wait for future projects though

i installed ubuntu server 9.10, i'm aware it's CL only, anyway thus far i've managed to set up the ipaddress of it and make it fixed

i'm not sure of what to do with hosts at the moment, reading on it isn't making much sense of it's purpose or layout so i've left it as is

i permenently mounted a fat32 partition to /media/stuff and changed permissions to 0777

only have one user on it, myself

installed samba smbfs smbclient and an openssh server, and can do all the terminal stuff from my normal pc

my current issue lies with samba, with gnome desktop i've never had TOO many problems with sharing folders, however i'm stuck where to proceed in regards to editing smb.conf as there's a lot of options, some of which i'm not sure i need

 - I've changed the workgroup to home
 - under authentication i have security = share
 - i added the following section
```
[media-share];
comment = public folder;
path = /media/stuff;
browsable = yes;
read only = no;
guest ok = yes;

```


anyway on my windows xp pro machine, i can access \\thork which is the machine and i see 'media-stuff' which is a start i guess, but im refuesed access automatically

can anyone help me or just point me to a decent guide as i think i've read everything out there and it's a bit conflicting

can post my smb.conf if you want :)

and sorry if this is wrong section

---

### Post by DestructionsRightHand on 2010-03-07
Most torrent clients have a web admin access in the options you just have to enable

---

### Post by systemchris on 2010-03-07
> **DestructionsRightHand said:**
> Most torrent clients have a web admin access in the options you just have to enable

thank you for the information, sadly i can't actually file sharing across the house network to 'work' at the moment :(

---

### Post by FiveSidedPoly on 2010-03-08
If you want to post your smb.conf here that would be great, we can take a look at it, and see if something isn't right.
 
 
Is your windows box workgroup "home" or "workgroup"?
 
Have you set the directory permissions with something like
 
```
sudo chmod 0770 /media/stuff
```
 
 
You have created an account on the server that is the same as the one on your windows box right? Same username and password and also for samba?
 
```
 
sudo adduser --home /home/username username
 
sudo smbpasswd -L -a username
 
sudo smbpasswd -L -e username
 

```
 
That will create the account on the server, create the samba account, then enable it.
 
 
Try using:
 
 
```
 
[media-share]
    path = /media/stuff/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0770
    directory mask = 0770
    force user = nobody
    force group = nogroup

```
 
Lets see if that can fix your access problems right now. 
 
Also make sure after you save your smb.conf that your restart samba with
 
```
 
sudo /etc/init.d/samba start

```
 
 
I wouldn't recommend using Webmin, I have only had it screw up my config files on Ubuntu Server, since getting rid of it and starting fresh any issues I had had went away.  I am tempted to try eBox but will do it on a test server first.

---

### Post by toMeloos on 2010-03-08
Just a small recommendation based on own experience:

I too run an Ubuntu home server (8.10 LTS in my case) and life has become much easier ever since I use [Ebox]("http://www.ebox-platform.com/") on top of Ubuntu. Handles my firewall/gateway/IDS, file & printer server (samba) and VPN (OpenVPN) needs and provides a nice web-interface for managing it. First time ever I managed to really get Windows filesharing (e.g. samba) working as it should. Has great Ubuntu support and packages.

If you wish to run a Bittorrent client on the server I recommend you read [this thread]("http://ubuntuforums.org/showthread.php?t=1114965").

---

### Post by The Real Dave on 2010-03-08
You can add the following line to your smb.conf to allow non-users to connect. 

```
security=share
```

I'll post up my smb.conf for my server in about 30 minutes. As for torrent programs, I'd advise rTorrent, it's a great CLI torrent program, and [K.Mandla's blog makes it extremely easy to use]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/"). 

One other thing, why are you using fat32 for your drive partition? Fat32 will fragment, and isn't as quick as using, say, ext3. It makes no difference to the client what filesystem is used on the server, so if the drive isn't physically being attached to a Windows box, your probably best off to use ext3.

---

### Post by The Real Dave on 2010-03-08
Here's my smb.conf. Adjust as needed :)

```
[global]
   workgroup = HOME
   server string = %h server 
;   wins server = w.x.y.z
   dns proxy = no
    guest ok = yes
    security = share
        guest account = dave

#======================= Share Definitions =======================
wins support = no
[homes]
   comment = Home Directories
   browseable = no
;   read only = yes
   create mask = 0777
   directory mask = 0777
   guest ok = no

[public]
        comment = Public
        browseable = yes
        writable = yes
        guest ok = yes
        create mask = 777
        directory mask = 777
        path = /home/dave/
        security = share

[elaine$]
	comment = Elaine's Storage
	browseable = no
	writable = yes
	guest ok = yes
	create mask = 777
	directory mask = 777
	path = /home/dave/Elaine
	security = share

#[software]
#        comment = Software
#        browseable = yes
#        writable = yes
#        guest ok = yes
#        create mask = 777
#        directory mask = 777
#        path = /media/Data/Setups
#        security = share
#        public = yes


```

---

### Post by systemchris on 2010-03-08
> **FiveSidedPoly said:**
> If you want to post your smb.conf here that would be great, we can take a look at it, and see if something isn't right.

(cleared bulk text)

thank you :) my workgroup is 'home'

i'm aiming for super simple file sharing so no usernames/passwords required, so security = share is the way forward, or security = user, with a defined guest account and guest ok = yes?

i can see the folder now i just cannot access it for love or money :s

is there anything you think i've missed, like in the OS itself regarding users or folder permissions?

this is my samba smb atm

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
   workgroup = HOME

# server string is the equivalent of the NT Description field
   server string = Morch's Samba Server

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
    security = share	


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

guest account = nobody

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
;[Homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

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
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


[Media]
comment = Crap Store
path = /media/stuff
security = share
browsable = Yes
writable = Yes
guest ok = Yes


```

---

### Post by mk1w86 on 2010-03-08
Your smb.conf looks OK to me, you can run

```
testparm
```

to check for any errors in it. ;)

It could be a folder permissions problem, could you please post the output of:

```
ls -l /media
```

so we can check the stuff directory permissions.  Also using FAT32 (out of interest is there a particular reason you are using FAT32?) which has no concept of permissions could be causing problems, I like others would recommend you use ext3 or ext4.  You could also consider JFS or XFS depending how big the volume is, what you are going to use it for and how big the files will be.

---

### Post by FiveSidedPoly on 2010-03-08
I don't see anything in your smb.conf tat could be stopping it right now, but I may have missed something.
 
I would add a line under the workgroup line that reads
 
```
netbios name = your_servername
```
 
mk1w86, maybe on onto something, but I have never used Samba on a Fat32 partition either. 
 
 
You can use this to change the directory permissions if you need to.
 
```
 
sudo chmod 0777 /media/stuff

```
 
To keep things simple under the Authentication section, leave it as:
 
```
 
security  = user

```
 
Don't worry if you set a share as public it won't matter, but it will allow you to let real users still have more permission, such as yourself.
 
 
Here is an example of a public directory I have on mine:
 
```
 
[Public]
 comment = Public Shares
 path = /Public
 ceate mask = 0777
 directory mask = 0777
 browseable = yes
 read only = no
 writeable = yes
 force user = nobody
 force group = nogroup

```

---

