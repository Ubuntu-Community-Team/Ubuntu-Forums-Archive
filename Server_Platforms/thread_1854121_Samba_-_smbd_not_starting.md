---
title: "Samba - smbd not starting"
date: 2011-10-03
forum: Server Platforms
---

### Post by sobgtp on 2011-10-03
Looking for some help, 

ubuntu Server 10.04 

OpenSSH and Samba set up as this will be a media server/file storage

I have run into a snag with samba , my Win 7 workstation does not see my network share. I have created a user in Samba and have two shares setup.  Both machines are part of the same workgroup.  

My machine is setup as "mediaserver" and I can ping the server on the Win 7 machine, however the server does not show up in network places and I can not directly navigate to the share //mediaserver/MEDIA 

it looks like nmbd is running correctly, however when I check the status of smbd it indicates the service is stopped/waiting.  When I sudo start it indicates the process has started, however when I check status again it shows the stopped/waiting again. 

smbtree gives me:
cli_start_connection: failed to connect to 192.168.0.12<20> (192.168.0.12). Error NT_STATUS_CONNECTION_REFUSED
cli_start_connection: failed to connect to MEDIASERVER<20> (192.168.0.12). Error NT_STATUS_CONNECTION_REFUSED

Any ideas on how I can get the share running for my network

---

### Post by kleverbear on 2011-10-03
Do you have any firewalls running?

can you see your server in windows networks?

---

### Post by Chrus on 2011-10-03
Can you get to the share via IP address? ie \\192.168.0.12\MEDIA

---

### Post by sobgtp on 2011-10-03
No firewall running , zonealarm is installed on Win 7 machine but I have it shutdown as I suspected that maybe the problem (On/off makes no difference), Windows Firewall is disabled.

The server does not show up in the network section on the Windows 7 machine

---

### Post by kleverbear on 2011-10-03
Can you post your smb.conf?
Ill putmone up as an example in a few.



Can you ping your server From your win7 ??

---

### Post by sobgtp on 2011-10-03
Well, I seem to have made some progress 

I re-created the smb.conf file and the service seems to start and stay running however the server still is not showing up in the windows network. 

I did retest connecting from the command line on the windows machine and I now get a response with //mediaserver/MEDIA  telling me that I am not authorized which I would expect since I did not enter login credentials.  When I try to map the share as a network drive it tells me that the network name can not be found, trying with IP fails as well. 
 
Here is my smb.conf

```

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
   encrypt passwords = no

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



[MEDIA]
comment = MEDIA Files
path = /media
valid users = servershare shawn
writable = yes
browseable = yes


```

EDIT:
Yes I can ping "mediaserver" and it returns a response

---

### Post by capscrew on 2011-10-03
The easiest way to see of the server (daemons) are running this command from the CLI```
pgrep -l mbd
```

Mine looks this```
cap@ubuntu:~$ **pgrep** -l mbd
950 smbd
1071 nmbd
1084 smbd

```

There should be at least 2 *smbd* and 1 *nmbd* daemons running.

Sometimes the nmbd daemon won't launch and then you have no name services.

---

### Post by sobgtp on 2011-10-03
Once I re-created the smd.conf file I now see the same before it only listed nmbd

```


shawn@mediaserver:~$ pgrep -l mbd
3572 nmbd
3580 smbd
3583 smbd

```

---

### Post by capscrew on 2011-10-03
> **sobgtp said:**
> Once I re-created the smd.conf file I now see the same before it only listed nmbd

```


shawn@mediaserver:~$ pgrep -l mbd
3572 nmbd
3580 smbd
3583 smbd

```
Is everything working now?

What (if any) problems do you still have?

Did you add a smbuser?```
smbpasswd -a
```

---

### Post by kleverbear on 2011-10-03
Add this line under global settings for browsing identification (first part)

#Windows 7 support for mounting samab shares
  client ntlmv2 auth = yes

I had to add this to enable win 7 support. Also consider uncommenting 
[#   security = user]

Oh and don't forget to restart samba after writing changes to conf.


```
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = FOREST

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

#Windows 7 support for mounting samab shares
  client ntlmv2 auth = yes

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
[Media]
	comment = Media Share
	path = /folder/media
	browsable = yes
	guest ok = yes
	read only = no
	create mask = 0766
	hide dot files = yes
[Public]
	comment = public
	path = /home/folder/Public
	browsable = yes
	guest ok = no
	read only = no
	create mask = 0644
	hide dot files = yes
```

---

### Post by capscrew on 2011-10-03
> **kleverbear said:**
> Add this line under global settings for browsing identification (first part)

#Windows 7 support for mounting samab shares
  client ntlmv2 auth = yes


I believe this allows ONLY ntlmv2 authentication.  The default now (v3.5) will allow all Windows clients to authenticate.

The description is poorly written, but at least it is available to peruse [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

---

### Post by sobgtp on 2011-10-03
I tried adding the line and removing the commenting on the other and I am still unable to connect to the share in Win 7. 

So basically: 

I can connect to the server with Putty using the server name, I can transfer files with winSCP , Win 7 can ping the server but I can not browse or connect to the share with Samba

---

### Post by capscrew on 2011-10-03
> **sobgtp said:**
> I tried adding the line and removing the commenting on the other and I am still unable to connect to the share in Win 7. 

So basically: 

I can connect to the server with Putty using the server name, I can transfer files with winSCP ,
 Win 7 can ping the server but I can not browse or connect to the share with Samba
This sounds like ssh is working (sshd) and DNS seems to be working too.  Lets confirm that.  Post the output of ```
cat /etc/hosts

```
Also lets see what the full config of Samba really is.  Post the output of ```
testparm -v
```

Edit: Does the Ubuntu host have a static or dynamic IP address

---

### Post by kleverbear on 2011-10-03
Are you both your server and pc on the same workgroup? This can prevent your win machine from seeing the server since its still on the default workgroup.

---

### Post by capscrew on 2011-10-03
> **kleverbear said:**
> Are you both your server and pc on the same workgroup? This can prevent your win machine from seeing the server since its still on the default workgroup.

Workgroups are irrelevant.  You can have as many workgroups as you wish.  They only associate the shares visually.  All will be available to any working client.

---

### Post by sobgtp on 2011-10-04
Both systems are configured as "WORKGROUP"

EDIT:

Thanks for the help guys, I wont have access to the system until this evening. I will post the results of etc/hosts and the output of testparm , I ran it yesterday however without the -v option and it only returned a generic error related to "rmax 1024" or something like that, based on what I have read it does not appear to be an issue

---

### Post by sobgtp on 2011-10-04
OK contents of hosts file

```

shawn@mediaserver:/etc/mediatomb$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       mediaserver.phub.net.cable.rogers.com   mediaserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Results of testparm -v

```

shawn@mediaserver:/etc/mediatomb$ sudo testparm -v |more
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[MEDIA]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
[global]
        dos charset = CP850
        unix charset = UTF-8
        display charset = LOCALE
        workgroup = WORKGROUP
        realm =
        netbios name = MEDIASERVER
        netbios aliases =
        netbios scope =
        server string = %h server (Samba, Ubuntu)
        interfaces =
        bind interfaces only = No
        security = USER
        auth methods =
        encrypt passwords = No
        update encrypted = No
        client schannel = Auto
        server schannel = Auto
        allow trusted domains = Yes
        map to guest = Bad User
        null passwords = No
        obey pam restrictions = Yes
        password server = *
        smb passwd file = /etc/samba/smbpasswd
        private dir = /etc/samba
        passdb backend = tdbsam
        algorithmic rid base = 1000
        root directory =
        guest account = nobody
        enable privileges = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n     *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd chat debug = No
        passwd chat timeout = 2
        check password script =
        username map =
        password level = 0
        username level = 0
        unix password sync = Yes
        restrict anonymous = 0
        lanman auth = No
        ntlm auth = Yes
        client NTLMv2 auth = Yes
        client lanman auth = No
        client plaintext auth = No
        preload modules =
        dedicated keytab file =
        kerberos method = default
        map untrusted to domain = No
        log level = 0
        syslog = 0
        syslog only = No
        log file = /var/log/samba/log.%m
        max log size = 1000
        debug timestamp = Yes
        debug prefix timestamp = No
        debug hires timestamp = No
        debug pid = No
        debug uid = No
        debug class = No
        enable core files = Yes
        smb ports = 445 139
        large readwrite = Yes
        max protocol = NT1
        min protocol = CORE
        min receivefile size = 0
        read raw = Yes
        write raw = Yes
        disable netbios = No
        reset on zero vc = No
        acl compatibility = auto
        defer sharing violations = Yes
        nt pipe support = Yes
        nt status support = Yes
        announce version = 4.9
        announce as = NT
        max mux = 50
        max xmit = 16644
        name resolve order = lmhosts wins host bcast
        max ttl = 259200
        max wins ttl = 518400
        min wins ttl = 21600
        time server = No
        unix extensions = Yes
        use spnego = Yes
        client signing = auto
        server signing = No
        client use spnego = Yes
        client ldap sasl wrapping = plain
        enable asu support = No
        svcctl list =
        deadtime = 0
        getwd cache = Yes
        keepalive = 300
        lpq cache time = 30
        max smbd processes = 0
        paranoid server security = Yes
        max disk size = 0
        max open files = 16384
        socket options = TCP_NODELAY
        use mmap = Yes
        hostname lookups = No
        name cache timeout = 660
        ctdbd socket =
        cluster addresses =
        clustering = No
        load printers = Yes
        printcap cache time = 750
        printcap name =
        cups server =
        cups connection timeout = 30
        iprint server =
        disable spoolss = No
        addport command =
        enumports command =
        addprinter command =
        deleteprinter command =
        show add printer wizard = Yes
        os2 driver map =
        mangling method = hash2
        mangle prefix = 1
        max stat cache size = 256
        stat cache = Yes
        machine password timeout = 604800
        add user script =
        rename user script =
        delete user script =
        add group script =
        delete group script =
        add user to group script =
        delete user from group script =
        set primary group script =
        add machine script =
        shutdown script =
        abort shutdown script =
        username map script =
        logon script =
        logon path = \\%N\%U\profile
        logon drive =
        logon home = \\%N\%U
        domain logons = No
        init logon delayed hosts =
        init logon delay = 100
        os level = 20
        lm announce = Auto
        lm interval = 60
        preferred master = No
        local master = Yes
        domain master = Auto
        browse list = Yes
        enhanced browsing = Yes
        dns proxy = No
        wins proxy = No
        wins server =
        wins support = No
        wins hook =
        kernel oplocks = Yes
        lock spin time = 200
        oplock break wait time = 0
        ldap admin dn =
        ldap delete dn = No
        ldap group suffix =
        ldap idmap suffix =
        ldap machine suffix =
        ldap passwd sync = no
        ldap replication sleep = 1000
        ldap suffix =
        ldap ssl = start tls
        ldap ssl ads = No
        ldap timeout = 15
        ldap connection timeout = 2
        ldap page size = 1024
        ldap user suffix =
        ldap debug level = 0
        ldap debug threshold = 10
        eventlog list =
        add share command =
        change share command =
        delete share command =
        preload =
        lock directory = /var/run/samba
        state directory = /var/lib/samba
        cache directory = /var/cache/samba
        pid directory = /var/run/samba
        utmp directory =
        wtmp directory =
        utmp = No
        default service =
        message command =
        get quota command =
        set quota command =
        remote announce =
        remote browse sync =
        socket address = 0.0.0.0
        homedir map = auto.home
        afs username map =
        afs token lifetime = 604800
        log nt token command =
        time offset = 0
        NIS homedir = No
        registry shares = No
        usershare allow guests = Yes
        usershare max shares = 100
        usershare owner only = Yes
        usershare path = /var/lib/samba/usershares
        usershare prefix allow list =
        usershare prefix deny list =
        usershare template share =
        panic action = /usr/share/samba/panic-action %d
        perfcount module =
        host msdfs = Yes
        passdb expand explicit = No
        idmap backend = tdb
        idmap alloc backend =
        idmap cache time = 604800
        idmap negative cache time = 120
        idmap uid =
        idmap gid =
        template homedir = /home/%D/%U
        template shell = /bin/false
        winbind separator = \
        winbind cache time = 300
        winbind reconnect delay = 30
        winbind enum users = No
        winbind enum groups = No
        winbind use default domain = No
        winbind trusted domains only = No
        winbind nested groups = Yes
        winbind expand groups = 1
        winbind nss info = template
        winbind refresh tickets = No
        winbind offline logon = No
        winbind normalize names = No
        winbind rpc only = No
        comment =
        path =
        username =
        invalid users =
        valid users =
        admin users =
        read list =
        write list =
        printer admin =
        force user =
        force group =
        read only = Yes
        acl check permissions = Yes
        acl group control = No
        acl map full control = Yes
        create mask = 0744
        force create mode = 00
        security mask = 0777
        force security mode = 00
        directory mask = 0755
        force directory mode = 00
        directory security mask = 0777
        force directory security mode = 00
        force unknown acl user = No
        inherit permissions = No
        inherit acls = No
        inherit owner = No
        guest only = No
        administrative share = No
        guest ok = No
        only user = No
        hosts allow =
        hosts deny =
        allocation roundup size = 1048576
        aio read size = 0
        aio write size = 0
        aio write behind =
        ea support = No
        nt acl support = Yes
        profile acls = No
        map acl inherit = No
        afs share = No
        smb encrypt = auto
        block size = 1024
        change notify = Yes
        directory name cache size = 100
        kernel change notify = Yes
        max connections = 0
        min print space = 0
        strict allocate = No
        strict sync = No
        sync always = No
        use sendfile = No
        write cache size = 0
        max reported print jobs = 0
        max print jobs = 1000
        printable = No
        printing = cups
        cups options =
        print command =
        lpq command = %p
        lprm command =
        lppause command =
        lpresume command =
        queuepause command =
        queueresume command =
        printer name =
        use client driver = No
        default devmode = Yes
        force printername = No
        printjob username = %U
        default case = lower
        case sensitive = Auto
        preserve case = Yes
        short preserve case = Yes
        mangling char = ~
        hide dot files = Yes
        hide special files = No
        hide unreadable = No
        hide unwriteable files = No
        delete veto files = No
        veto files =
        hide files =
        veto oplock files =
        map archive = Yes
        map hidden = No
        map system = No
        map readonly = yes
        mangled names = Yes
        store dos attributes = No
        dmapi support = No
        browseable = Yes
        access based share enum = No
        browsable = Yes
        blocking locks = Yes
        csc policy = manual
        fake oplocks = No
        locking = Yes
        oplocks = Yes
        level2 oplocks = Yes
        oplock contention limit = 2
        posix locking = Yes
        strict locking = Auto
        share modes = Yes
        dfree cache time = 0
        dfree command =
        copy =
        preexec =
        preexec close = No
        postexec =
        root preexec =
        root preexec close = No
        root postexec =
        available = Yes
        volume =
        fstype = NTFS
        set directory = No
        wide links = No
        follow symlinks = Yes
        dont descend =
        magic script =
        magic output =
        delete readonly = No
        dos filemode = No
        dos filetimes = Yes
        dos filetime resolution = No
        fake directory create times = No
        vfs objects =
        msdfs root = No
        msdfs proxy =

[MEDIA]
        comment = MEDIA Files
        path = /media
        valid users = servershare, shawn
        read only = No
        guest ok = Yes



```

---

### Post by capscrew on 2011-10-05
> returned a generic error related to "rmax 1024"

That would be this```
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
```

This is not an error message at all.  It's letting you know that the Samba limit is set well below Windows limit.


Using *netbios name = MEDIASERVER* means you do not have to rely on the hostname to resolve into the netbios name (via the nmbd daemon). 

But you have no way to look for the server or its shares. To locate (browse) shares you need to modify this```
 name resolve order = lmhosts wins host bcast

```

It should be modified to this ```
 name resolve order = bcast host 

```

Putting ***bcast*** first forces Samba to broadcast for the listing of the shares available on the LAN. This is how Windows handles share browsing.  

The next value would look in the /etc/hosts file, but since you have set the netbios name earlier this won't ever happen. The last two are not needed at all. Only a few use lmhosts and you should not run a WINS server (wins) on a single segment LAN.

So if we have the following in you smb.conf file, you should be able to browse to the shares```
netbios name = MEDIASERVER
name resolve order = bcast host 
```

Note: As I have not seen the actual smb.conf file you will need to find the parameter *name resolve order = lmhosts wins host bcast * and modify it accordingly.

---

### Post by sobgtp on 2011-10-05
Thanks for your help I will give this a shot , however when I look in my smb.conf file under /etc/samba/smb.conf I do not see either one of those entries. 

Will I have an issue with the netbios item showing upper case and the server name set as low case? 

Where are the verbose details of smb.conf coming from? 

I just setup Ubuntu desktop as a dual boot so I have been playing around with getting it setup. I will flip back into Win 7 to test these changes once I figure out where to update them. 

Here is my smb.conf
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

# Windows 7 support for mounting samab shares
   client ntlmv2 auth = yes

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
   encrypt passwords = no

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



[MEDIA]
comment = MEDIA Files
path = /media
valid users = servershare shawn
guest ok = yes
read only = no
writable = yes
browseable = yes



```

---

### Post by capscrew on 2011-10-05
> **sobgtp said:**
> Thanks for your help I will give this a shot , however when I look in my smb.conf file under /etc/samba/smb.conf I do not see either one of those entries.

If there is no entry then the default applies.  This means the netbios name not applied (it has none).  The default name resolve order is applied if not explicitly declared (that would be *name resolve order = lmhosts wins host bcast*).  So all you need to do is add these to the  [global] section of the smb.conf file.```

``````
netbios name = MEDIASERVER
name resolve order = bcast host
```>  

Will I have an issue with the netbios item showing upper case and the server name set as low case? 
Not at all.  The host name is not used in this configuration.  The nmbd (naming daemon) is specifically instructed to use the netbios name you provided instead of the hostname.  FYI -- the netbios name is always uppercase.  If the nmbd daemon finds it lowercase it converts it to uppercase. > 

Where are the verbose details of smb.conf coming from?

Samba has many parameters.  All are set to a default even if it is a null (nothing).  The smb.conf file parameters are mostly the typical settings for the average user.  I believe these can be set by the package maintainer.  When you user *testparam -v* it reads all the parameters.  If you use *testparm -s* you only see the parameters that are set by the smb.conf file. > 
 
I just setup Ubuntu desktop as a dual boot so I have been playing around with getting it setup. I will flip back into Win 7 to test these changes once I figure out where to update them. 

Here is my smb.conf

I have added the proper lines (in **[COLOR="Red"]red[/COLOR]**) to the smb.conf file below.  To edit this file you need to use root privileges. You can use gedit as the editor like this ALT-F2 and fill in the box with this:[COLOR="DarkGreen"]**gksudo gedit /etc/samba/smb.conf**[/COLOR].  

Use your password and the editor will come up with the file to be edited.  You are editing as root (Admin) so you should be able to save the file.  

Then you can either reboot the system or just restart the 2 daemons from the terminal like this```
sudo service smbd restart
sudo service nmbd restart
```

You can test to see if both are running with this ```
pgrep -l mbd
```  > 

```


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

[COLOR="Red"]# Set the NetBIOS name and resolve it by broadcast
    netbios name = MEDIASERVER
    name resolve order = bcast host
[/COLOR]

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

# Windows 7 support for mounting samab shares
   client ntlmv2 auth = yes

...



```

---

### Post by sobgtp on 2011-10-06
Thanks for your help capscrew 

Adding those lines has allowed me to map the samba shares on my Windows 7 machine.  The server still did not show up under the network but I was able to map it using the name so that is all I needed. 

I did have to update one additional line 

```
encrypt passwords = yes 
```

Windows was complaining "Account is not authorized to log in to this Station"

---

