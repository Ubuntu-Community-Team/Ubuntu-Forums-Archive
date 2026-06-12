---
title: "Samba does not create /etc/samba"
date: 2014-03-14
forum: Server Platforms
---

### Post by Patrick Latour on 2014-03-14
I am running Ubuntu server 12.04.03 and When I install Samba with the following command:

**platour@tech:/$** sudo apt-get install samba

and try to edit /etc/samba/smb.conf to add my own shares, there is no smb.conf and not even a samba directory under /etc, so I looked more closely to the installation info displayed after the command above and here is what I got ( I put in red what flashed me):

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ctdb
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/8,040 kB of archives.
After this operation, 23.4 MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package samba.
(Reading database ... 62050 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.6.3-2ubuntu2.9_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Setting up samba (2:3.6.3-2ubuntu2.9) ...
[COLOR=#ff0000]Generating /etc/default/samba...[/COLOR]
[COLOR=#ff0000]update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.[/COLOR]
smbd start/running, process 3397
nmbd stop/pre-start, process 3432

Then I tried smbstatus.samba3 and the result is:
platour@tech:/etc/samba$ sudo /usr/bin/smbstatus.samba3
Can't load /etc/samba/smb.conf - run testparm to debug it

I ran testparm and:

platour@tech:/etc/samba$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
    No such file or directory
Error loading services.

I deinstalled and reinstalled samba but always got the same result. Any idea ?

Thanks and Regards,

Patrick Latour

---

### Post by dniMretsaM on 2014-03-14
I believe what you're looking for is [font=Courier New]/usr/share/samba[/font].

---

### Post by bab1 on 2014-03-15
> **Patrick Latour said:**
> I am running Ubuntu server 12.04.03 and When I install Samba with the following command:

**platour@tech:/$** sudo apt-get install samba

and try to edit /etc/samba/smb.conf to add my own shares, there is no smb.conf and not even a samba directory under /etc, ...

[Later ???] I deinstalled and reinstalled samba but always got the same result. Any idea ?

Thanks and Regards,

Patrick Latour

The /etc/samba structure is not recreated when you remove it.  I believe (but don't actually know for sure) that if you *purge samba* and then reinstall you will have the /etc/samba structure and the 2 files that are there by default.  The other file is *gdbcommands*.  It's for Samba debuging.  None of the 20+ plus installs i have performed of samba (v3.6) have failed to construct these files and the directory structure.

That being said, @dniMretsaM is correct.  There is a copy of the smb.conf file at */usr/share/samba. *One caveat however.  You need to change this line```
   encrypt passwords = **[COLOR="#FF0000"]no[/COLOR]**
```... to this```
   encrypt passwords = **[COLOR="#0000FF"]yes[/COLOR]**
```

Of course you will need to create the /etc/samba directory if it is not there.  The ownership is root:root and the permissions are 755.

---

### Post by Patrick Latour on 2014-03-16
Ok, thanks. I copied from /usr/share/samba and changed the encrypt passwords = no for yes. I have a first share named [shared] that is open to anyone (guest ok = yes). I can connect to it from Windows without any problem. I have another share named [management], guest ok = no. in my smbusers i placed my username platour = platour sync passwords is at yes and I installed libpam-smbpass to keep my password in sync. When I try to connect to management it asks for a username and a password, I enter platour with my linux password but it is always refusing the access. What the owner of management directory (/srv/samba/management) should be ? nobody:nogroup like the open shared ?, or maybe something like platour:management (I created a group, so other users from that group could access the shared). Sorry for the dumb questions but it is one of my first try at Samba. Thanks again.

---

### Post by cariboo on 2014-03-16
Have you set a samba password by running:

```
sudo smbpasswd -a
```

---

### Post by Patrick Latour on 2014-03-17
Yes I did. I runned: sudo smbpasswd -a platour
Here is my share definition:
[management]
   comment = STE management drive
   path = /srv/samba/management
   browsable = yes
   guest ok = no
   valid users = platour
   read only = no
   create mask = 0755

My smbusers:
platour = platour

platour is a valid user on my linux server and he is member of a group named management

My owner for /srv/samba/management is platour:management

I know that I am doing something wrong somewhere, just need to find where :-)

Thanks for your help

---

### Post by bab1 on 2014-03-17
> **Patrick Latour said:**
> Yes I did. I runned: sudo smbpasswd -a platour
Here is my share definition:
[management]
   comment = STE management drive
   path = /srv/samba/management
   browsable = yes
   guest ok = no
   valid users = platour
   read only = no
   create mask = 0755

My smbusers:
platour = platour

platour is a valid user on my linux server and he is member of a group named management

My owner for /srv/samba/management is platour:management

I know that I am doing something wrong somewhere, just need to find where :-)

Thanks for your help

Let's diagnose this a little.  What OS is the client using Ubuntu or Windows?  From the Ubuntu server Post the output of these commands```

ls -ld /srv
ls -ld /srv/samba
ls-ld /srv/samba/management

smbclient d3 -L ////<SERVERNAME>
```...where <SERVERNAME> is the name you have set for the Ubuntu server.  If this was my server it would look like this: *smbclient -d3 -L ////malibu*

Post the entire smb.conf file that you are using now.

---

### Post by Patrick Latour on 2014-03-17
Thanks BAB1, here are the info you requested:
$: ls -ld /srv
drwxr-xr-x 4 root root 4096 Mar 14 16:55 /srv

$: ls -ld /srv/samba
drwxr-xr-x 5 root root 4096 Mar 14 16:55 /srv/samba

$: ls -ld /srv/samba/management
drwxrw-rw- 2 platour management 4096 Mar 14 16:55 /srv/samba/management

The smb.conf will follow in few minutes...

Thanks to you all...

---

### Post by bab1 on 2014-03-17
> **Patrick Latour said:**
> Thanks BAB1, here are the info you requested:
$: ls -ld /srv
drwxr-xr-x 4 root root 4096 Mar 14 16:55 /srv

$: ls -ld /srv/samba
drwxr-xr-x 5 root root 4096 Mar 14 16:55 /srv/samba

$: ls -ld /srv/samba/management
drwxrw-rw- 2 platour management 4096 Mar 14 16:55 /srv/samba/management

The smb.conf will follow in few minutes...

Thanks to you all...

Don't forget this```
smbclient d3 -L ////<SERVERNAME>
```

---

### Post by Patrick Latour on 2014-03-17
Ok, for that command I got an error:

smbclient d3 -L ////tech

d3: Not enough '\' characters in service
Usage: smbclient [-?EgBVNkPeC] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-m|--max-protocol=LEVEL] [-T|--tar=<c|x>IXFqgbNan]
        [-D|--directory=DIR] [-c|--command=STRING] [-b|--send-buffer=BYTES]
        [-p|--port=PORT] [-g|--grepable] [-B|--browse]
        [-d|--debuglevel=DEBUGLEVEL] [-s|--configfile=CONFIGFILE]
        [-l|--log-basename=LOGFILEBASE] [-V|--version] [--option=name=value]
        [-O|--socket-options=SOCKETOPTIONS] [-n|--netbiosname=NETBIOSNAME]
        [-W|--workgroup=WORKGROUP] [-i|--scope=SCOPE] [-U|--user=USERNAME]
        [-N|--no-pass] [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        [-C|--use-ccache] service <password>

---

### Post by bab1 on 2014-03-17
> **Patrick Latour said:**
> Ok, for that command I got an error:

smbclient d3 -L ////tech

d3: Not enough '\' characters in service
Usage: smbclient [-?EgBVNkPeC] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-m|--max-protocol=LEVEL] [-T|--tar=<c|x>IXFqgbNan]
        [-D|--directory=DIR] [-c|--command=STRING] [-b|--send-buffer=BYTES]
        [-p|--port=PORT] [-g|--grepable] [-B|--browse]
        [-d|--debuglevel=DEBUGLEVEL] [-s|--configfile=CONFIGFILE]
        [-l|--log-basename=LOGFILEBASE] [-V|--version] [--option=name=value]
        [-O|--socket-options=SOCKETOPTIONS] [-n|--netbiosname=NETBIOSNAME]
        [-W|--workgroup=WORKGROUP] [-i|--scope=SCOPE] [-U|--user=USERNAME]
        [-N|--no-pass] [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        [-C|--use-ccache] service <password>

You left out the - in front of d3.  It should look like this```

smbclient [COLOR="#FF0000"]**[SIZE=2]-[/SIZE]**[/COLOR]d3 -L ////tech

```

The dashes and spaces are important.

---

### Post by Patrick Latour on 2014-03-17
And here we go with my complete smb.conf

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
   netbios name = TECH
   workgroup = STE

# server string is the equivalent of the NT Description field
   server string = STE file server on (%L)

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
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
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


# STE common shared drive, open and unsafe.
#==========================================
[shared]
   comment = STE shared drive
   path = /srv/samba/shared
   browsable = yes
   guest ok = yes
   read only = no
   create mask = 0755

# STE sales drive, restricted to sales group.
#============================================
[sales]
   comment = STE sales drive
   path = /srv/samba/sales
   browsable = yes
   guest ok = no
   valid users = platour
   read only = no
   create mask = 0755

# STE management drive, restricted to management group.
#======================================================
[management]
   comment = STE management drive
   path = /srv/samba/management
   browsable = yes
   guest ok = no
   valid users = platour
   read only = no
   create mask = 0755


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

;[printers]
;   comment = All Printers
;   browseable = no
;   path = /var/spool/samba
;   printable = yes
;   guest ok = no
;   read only = yes
;   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
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

---

### Post by Patrick Latour on 2014-03-17
And for the other command (I replaced my external address with X), from what I can see there is something wrong with the permission of the tdb file:

 smbclient -d3 -L ////tech
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::21e:67ff:fe8b:f607%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.110.11 bcast=192.168.110.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter platour's password:
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name tech<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name tech<0x20>
resolve_wins: Attempting wins lookup for name tech<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name tech<0x20>
Connecting to xx.xx.xxx.xx at port 445
Connecting to xx.xx.xxx.xx at port 139
Error connecting to xx.xx.xxx.xx (Connection refused)
Connection to tech failed (Error NT_STATUS_CONNECTION_REFUSED)

---

### Post by bab1 on 2014-03-17
> **Patrick Latour said:**
> And for the other command (I replaced my external address with X), from what I can see there is something wrong with the permission of the tdb file:
```

 smbclient -d3 -L ////tech
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::21e:67ff:fe8b:f607%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.110.11 bcast=192.168.110.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter platour's password:
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name tech<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name tech<0x20>
resolve_wins: Attempting wins lookup for name tech<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name tech<0x20>
Connecting to xx.xx.xxx.xx at port 445
Connecting to xx.xx.xxx.xx at port 139
Error connecting to xx.xx.xxx.xx (Connection refused)
Connection to tech failed (Error NT_STATUS_CONNECTION_REFUSED
```)

That error is a normal occurrence.    The last line is the problem.  It is connecting and the server is refusing the connection.  We need to up the diagnoses level.  Also I want you to post the information inside the code tags like I do.  It will be easier to read.  To do that you just need to click on the [SIZE=4]**#**[/SIZE] icon at the top right of the "advanced" editor screen and paste the date in between the tags.  Let's use -d4.  Post the output of ```
smbclient -d4 -L ////tech
```

As you are using 192.168.110.11 in your LAN there is no security issue that you need xxx out the IP addresses.  Almost every private LAN (192.168.n.n) uses the very same numbers.  You are behind a router that uses NAT so those numbers never directly face the public Internet.  What you shouldn't reveal is the WAN side address.

---

### Post by Patrick Latour on 2014-03-17
Sorry for not using the code tags.

```

platour@tech:/$ smbclient -d4 -L ////tech
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter netbios name = TECH
handle_netbios_name: set global_myname to: TECH
doing parameter workgroup = STE
doing parameter server string = STE file server on (%L)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter encrypt passwords = yes
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface eth0 ip=fe80::21e:67ff:fe8b:f607%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.110.11 bcast=192.168.110.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter platour's password:
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name tech<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name tech<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name tech<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name tech<0x20>
Connecting to xx.xx.xx.xx at port 445
Connecting to xx.xx.xx.xx at port 139
Error connecting to xx.xx.xx.xx (Connection refused)
Connection to tech failed (Error NT_STATUS_CONNECTION_REFUSED)

```

---

### Post by bab1 on 2014-03-17
> **Patrick Latour said:**
> Sorry for not using the code tags.

```

platour@tech:/$ smbclient -d4 -L ////tech
...
resolve_hosts: Attempting host lookup for name tech<0x20>
Connecting to xx.xx.xx.xx at port 445
Connecting to xx.xx.xx.xx at port 139
[COLOR="#FF0000"]Error connecting to xx.xx.xx.xx (Connection refused)
Connection to tech failed (Error NT_STATUS_CONNECTION_REFUSED)[/COLOR]

```

Patrick,

Let's do that again.  Up the debug to -d9.  Just post the last 10 or so lines.  The top part is fine.  I'm trying to see why we get the error ```
Error connecting to xx.xx.xx.xx (Connection refused)
Connection to tech failed (Error NT_STATUS_CONNECTION_REFUSED)
```

---

### Post by Patrick Latour on 2014-03-17
Here we go:


```

Substituting charset 'UTF-8' for LOCALE
added interface eth0 ip=fe80::21e:67ff:fe8b:f607%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.110.11 bcast=192.168.110.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="TECH"
Client started (version 3.6.3).
Enter platour's password: 
Opening cache file at /var/run/samba/gencache.tdb
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/run/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
sitename_fetch: No stored sitename for 
no entry for tech#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name tech<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name tech<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name tech<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name tech<0x20>
namecache_store: storing 1 address for tech#20: xx.xx.xx.xx
Connecting to xx.xx.xx.xx at port 445
Connecting to xx.xx.xx.xx at port 139
Error connecting to xx.xx.xx.xx (Connection refused)
Connection to tech failed (Error NT_STATUS_CONNECTION_REFUSED)

```

---

### Post by bab1 on 2014-03-17
> **Patrick Latour said:**
> Here we go:


```

namecache_store: storing 1 address for tech#20: xx.xx.xx.xx
Connecting to xx.xx.xx.xx at port 445
Connecting to xx.xx.xx.xx at port 139
Error connecting to xx.xx.xx.xx (Connection refused)
Connection to tech failed (Error NT_STATUS_CONNECTION_REFUSED)

```
Well that told us nothing new.  The host should be able to connect and not log you in if you are not authenticated.  This instance is not even allowing connection and it's not telling us why.

I'm attaching a new smb,conf file that you can just add your shares and see if it works.  I have stripped the comments and left only the standard lines. It turns out that the default encrypt line is not needed as the default is yes.  The only lines needed are additions or changes from the default.

Copy the smb.conf you have and substitute the one I have attached.  You will have to rename it as only .txt files are allowed.

This is the attachment [ATTACH]251245[/ATTACH]

---

### Post by Patrick Latour on 2014-03-17
Ok. I uncommented the following lines and now I can map my shares but still does not work. It seems to be a matter of permissions now.

interfaces = 127.0.0.0/8 eth0
bind interfaces only = yes

---

### Post by bab1 on 2014-03-17
> **Patrick Latour said:**
> Ok. I uncommented the following lines and now I can map my shares but still does not work. It seems to be a matter of permissions now.

interfaces = 127.0.0.0/8 eth0
bind interfaces only = yes
Let me look over the share definitions again and the permissions you have sent me already.

Confirm that you have a Linux user and a Samba user with the same name.  Post the output of these 2 commands```
sudo pdbedit -L

getent passwd |grep 100
```

---

### Post by Patrick Latour on 2014-03-18
Ok, for the first command, Samba user seems to be missing (note that user technicien is user without a shell and it is normal):

```

nobody:65534:nobody
lgaucher:1000:Luc Gaucher
robin:1004:Robin Beauregard
mgiard:1003:Melanie Giard
platour:1001:Patrick Latour
technicien:1002:

```

For the second command:

```

libuuid:x:100:101::/var/lib/libuuid:/bin/sh
platour:x:1001:1001:Patrick Latour,,,:/home/platour:/bin/bash
technicien:x:1002:1002::/home/technicien/:/usr/bin/technicien
lgaucher:x:1000:1000:Luc Gaucher,,,:/home/lgaucher:/bin/bash
mgiard:x:1003:1003:Melanie Giard,,,:/home/mgiard:/bin/bash
robin:x:1004:1004:Robin Beauregard,,,:/home/robin:/bin/bash

```

BAB1, thanks for your time, I hope someday I will have the chance to help somebody else like you are helping me right now.

---

### Post by bab1 on 2014-03-18
> **Patrick Latour said:**
> Ok, for the first command, Samba user seems to be missing (note that user technicien is user without a shell and it is normal)

```

nobody:65534:nobody
lgaucher:1000:Luc Gaucher
robin:1004:Robin Beauregard
mgiard:1003:Melanie Giard
platour:1001:Patrick Latour
technicien:1002:

```


There is not supposed to be a user *named *Samba.  The pdbedit command I had you use shows all the users you added to the Samba user database via the use of **smbpasswd**.
> 

For the second command:

```

libuuid:x:100:101::/var/lib/libuuid:/bin/sh
platour:x:1001:1001:Patrick Latour,,,:/home/platour:/bin/bash
technicien:x:1002:1002::/home/technicien/:/usr/bin/technicien
lgaucher:x:1000:1000:Luc Gaucher,,,:/home/lgaucher:/bin/bash
mgiard:x:1003:1003:Melanie Giard,,,:/home/mgiard:/bin/bash
robin:x:1004:1004:Robin Beauregard,,,:/home/robin:/bin/bash

```

This looks good.  At this point we have Linux users and the corresponding Samba users.

When a specific file system branch is dedicated to Samba file sharing I set the ownership and permissions at the root of that file system.  The root of your file shares is */srv/samba*.  You have multiple restricted shares however.  So you would need multiple user groups.  For example the _management share_, I assume is to be available to users in the _management group_ only.  We would then need to set the ownership and permissions differently than the other shares.  So a ownership scheme with permissions of 2775 (rwxrwxr-x) is needed.  Something like this```

File System                 Ownership
=========                    =========
/srv/samba/shared         root:staff  
/srv/samba/mgmt           root:mgmt
/srv/samba/sales            root:sales

```

You would need to make the 3 separate distinct user groups of staff, mgmt and sales.  This allows you to manage access via the user group (staff, mgmt or sales) rather than the owner/creator.  In addition you need to set the sgid bit to provide for group ownership inheritance.

All of this is easily done.  I have a few questions?  Is this a test server?  Is there much data in the various shares?  Are you set on the naming conventions (i.e sales, management, shared etc.)?  What groups are already in use.  Post the output of ```
getent group
```

---

### Post by Patrick Latour on 2014-03-18
Here is the result of the last command:

```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:platour
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:
sudo:x:27:platour
audio:x:29:
dip:x:30:
www-data:x:33:platour
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
mlocate:x:107:
ssh:x:108:
landscape:x:109:
netdev:x:110:
lpadmin:x:111:
sambashare:x:112:
platour:x:1001:
mysql:x:106:
ssl-cert:x:113:
ftp:x:114:
technicien:x:1002:
ntp:x:115:
smmta:x:116:
smmsp:x:117:
bind:x:118:
lgaucher:x:1000:
mgiard:x:1003:
robin:x:1004:
sales:x:1005:lgaucher,mgiard,robin,platour
management:x:1006:lgaucher,mgiard,platour

```

For your questions:

Is this a test server?  
No but it is a brand new server not yet in production. Everything is setup, the Samba is my last part to configure and test.


Is there much data in the various shares?
Each share should be between 0 and 10GB

  Are you set on the naming conventions?
Not at all, I am open to any suggestions that would be logic.

Thanks again.

---

### Post by bab1 on 2014-03-18
> **Patrick Latour said:**
> Here is the result of the last command:

```

...

sales:x:1005:lgaucher,mgiard,robin,platour
management:x:1006:lgaucher,mgiard,platour

```

For your questions:

Is this a test server?  
No but it is a brand new server not yet in production. Everything is setup, the Samba is my last part to configure and test.


Is there much data in the various shares?
Each share should be between 0 and 10GB

Are you set on the naming conventions?
Not at all, I am open to any suggestions that would be logic.

Thanks again.

I want you to create a test share.  Here are the steps:
First the Linux share directory: 
**[SIZE=2]1[/SIZE]**```
sudo mkdir /srv/samba/t
```
**[SIZE=2]2[/SIZE]**```
sudo chown root:users /srv/samba/t
```
**[SIZE=2]3[/SIZE]**```
sudo chmod 2775 /srv/samba/t
```

Now we need to add a user (e.g robin) to the user group *users*.  At this point only root and robin can use this file system (/srv/samba/test) from a local login. 

No we make the share.  Add this to the bottom of your smb.conf file ```

[Test]
        comment = Test Share
        path = /srv/samba/t
        browseable = yes
        guest ok = no
        valid users = @users
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775

```...and reload the Samba daemon with this command```
sudo service smbd reload
```
Now you should be able to browse and see the Test share.  Only robin can access the share and only robin can read, write or delete anything in the share.  

As you can see the name of the share does not need to be the name of the directory that is shared.  The user always sees the share as //SERVER_NAME/share_name.

You can add other users to the user group to provide them with access.  This is how you manage the share access via group membership.  The force group is needed as Windows machines do strange things to the user/group ownership.  We want to insure that the user group is always the group we want.

Tell me again; how much data is already in the subdirectories of /srv/samba?

---

### Post by Patrick Latour on 2014-03-18
Thanks, I will try it in the next 20 minutes. Actually there are only few MB in the /srv/samba since I am just at the test part. Eventually each shares should hold few GB. I will be back after the test.

---

### Post by Patrick Latour on 2014-03-18
Already back and it works !! I noticed some differences in your share definition: First for the valid users parameter, I was not aware that you could specify a group with @ I was always trying to list the users. Second, I was not aware of the force group parameter. I will finalize the setup of my shares and play with the different users to test it, but you put me back on tracks. Thanks for your patience and I will keep you posted of the result later tonight or tomorrow morning.

---

### Post by bab1 on 2014-03-18
> **Patrick Latour said:**
> Already back and it works !! I noticed some differences in your share definition: First for the valid users parameter, I was not aware that you could specify a group with @ I was always trying to list the users. Second, I was not aware of the force group parameter. I will finalize the setup of my shares and play with the different users to test it, but you put me back on tracks. Thanks for your patience and I will keep you posted of the result later tonight or tomorrow morning.

Most folks find all the Samba information sooner or later.  The trick is the setting the Linux file system SGID group permissions.

---

### Post by Patrick Latour on 2014-03-19
BAB1, all my shares are working smoothly. Waiting to perform my last tests and if everything is ok, I will kick this server live. Thanks for your help, a lesson I will remember :-)

---

### Post by bab1 on 2014-03-19
> **Patrick Latour said:**
> BAB1, all my shares are working smoothly. Waiting to perform my last tests and if everything is ok, I will kick this server live. Thanks for your help, a lesson I will remember :-)

If all is working as it should please mark this tread as ***solved***.  Glad I could help.

---

