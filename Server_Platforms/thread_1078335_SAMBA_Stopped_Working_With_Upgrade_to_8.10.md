---
title: "SAMBA Stopped Working With Upgrade to 8.10"
date: 2009-02-23
forum: Server Platforms
---

### Post by Paul41 on 2009-02-23
I have a home server (server version of Ubuntu installed) set up and it was sharing files through SAMBA fine with 8.04 but as soon as I upgraded to 8.10 it stopped working. I am still able to use FTP and CUPS is working because I am able to print but I can not map to the SAMBA shares. When I try to map a drive it tells me permission is denied so I tried to re-add the users to SAMBA but it still doesn't work. I am having the same problem with both my wife's Windows computer and my Ubuntu computer (my laptop). I can connect my Ubuntu computer fine with SSH but that obviously doesn't help with Windows computer.

My smb.conf file hasn't changed at all since it was working fine with 8.04 but I am including it here anyway just in case it helps someone figure out what is going on.

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
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = sanders_net

# server string is the equivalent of the NT Description field
   server string =

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = host wins bcast

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

   map to guest = bad user
   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printig = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups
   security = share

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   guest only = yes
   guest account = smbprint
   use client driver = yes

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

# Added by Paul to share drives
[sanders share]
comment = Public Folder
path = /mnt/storage
writable = yes
create mask = 0777
directory mask = 0777
force user = nouser
force group = nogroup
browseable = yes

```

---

### Post by HermanAB on 2009-02-23
Debug it with smbclient:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by Paul41 on 2009-02-23
I get this error when I try to connect with smbclint but I don't know what it means.

> Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0

---

### Post by Paul41 on 2009-02-23
OK, so I found in the smb.conf file where it was setting the security was set to share (I accidentally overrode my original later in the file). So took that out (set it back to user) and now I get this error with smbclient.

> tree connect failed: NT_STATUS_BAD_NETWORK_NAME


---

### Post by Paul41 on 2009-02-23
I think I had the share name in wrong before and fixed that but here is my latest error.

```
tree connect failed: NT_STATUS_NO_SUCH_USER

```

---

### Post by bomber32 on 2009-02-23
try this one. look for 

"security = user"

try to delete it or just add " # " on the fist 

hope this help you ^_^

---

### Post by Paul41 on 2009-02-24
> **bomber32 said:**
> try this one. look for 

"security = user"

try to delete it or just add " # " on the fist 

hope this help you ^_^

I tried this and still get the no such user error.

---

### Post by Paul41 on 2009-02-24
I have been searching on this for hours but have gotten nowhere. I ran testparam on the server and here was the output. It all looks fine to me

> Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Global parameter guest account found in service section!
Processing section "[print$]"
Processing section "[sanders share]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = SANDERS_NET
	server string = 
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = host wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	dns proxy = No
	wins support = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	guest only = Yes
	guest ok = Yes
	printable = Yes
	use client driver = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[sanders share]
	comment = Public Folder
	path = /mnt/storage
	force user = nouser
	force group = nogroup
	read only = No
	create mask = 0777
	directory mask = 0777


And here is what I get when I run it from the client

> Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


---

### Post by Paul41 on 2009-02-27
bump

---

### Post by VictorR on 2009-02-27
I have had same issue since upgrade to 8.04. Everything seemed to be working fine, except I couldn't see any windows shares in the Nautilus and had to connect using smb://123.456.789.123/share-name way.

I have resolved this adding the following lines into /etc/samba/smb.conf file:
```

under **global** section
local master = yes
domain master = yes
preferred master = yes

```

I guess the default values for these options were YES in older versions of Samba, but they became NO in a new one.

---

### Post by Paul41 on 2009-02-28
> **VictorR said:**
> I have had same issue since upgrade to 8.04. Everything seemed to be working fine, except I couldn't see any windows shares in the Nautilus and had to connect using smb://123.456.789.123/share-name way.

I have resolved this adding the following lines into /etc/samba/smb.conf file:
```

under **global** section
local master = yes
domain master = yes
preferred master = yes

```

I guess the default values for these options were YES in older versions of Samba, but they became NO in a new one.

Thanks for the info. I gave it a try but still no luck.

---

### Post by VictorR on 2009-02-28
Yes, I was wrong. This allowed me to see the computers in the network, but still no ways to  connect to them. Maybe this is because of the bug
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/320547](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/320547)
as I can easily connect using smbclient.

---

### Post by Paul41 on 2009-02-28
I am not even able to connect with smbclient.

---

### Post by Paul41 on 2009-03-04
bump

---

### Post by Paul41 on 2009-03-07
bump

---

### Post by Paul41 on 2009-03-10
bump

---

### Post by Paul41 on 2009-03-12
bump

---

### Post by Paul41 on 2009-03-14
bump

---

### Post by sepia-shots on 2009-03-15
Sorry to ask a dumb question, but do you have ufw running? I've suddenly got problems with Samba in 8.10 and at least part of it was down to the ufw rules. Now if only I can persuade Samba to start on boot (it's fine if I sudo /etc/samba start) I'm laughing.

Regards

Pete

---

### Post by Paul41 on 2009-03-15
I looked into the UFW and I have it off.  I'm still getting the tree connect failed: NT_STATUS_NO_SUCH_USER error with smbclient.

---

### Post by Paul41 on 2009-03-17
bump

---

### Post by Paul41 on 2009-03-21
bump

---

### Post by maclenin on 2009-03-22
I wonder if your issue is realated - in some way - to this bug...

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/283811](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/283811)

...I have a hunch that it might be (though yours is not solely a printer issue - it does involve SAMBA, permission denial and authorization issues) - I cannot test my hunches at the moment, as the windows machine through which I had been printing (via CUPS/SAMBA) has just gone the way of the dodo....

Good luck!

---

### Post by Paul41 on 2009-03-23
For me printing works fine, but I can't share files.

---

### Post by lisati on 2009-03-23
I'm having trouble too, with 8.10. I finally got round to setting up samba using the "Howto" at[ http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605") which worked great with Feisty..... Going to Places->Network sometimes shows up "Unable to mount location" - I've changed routers and might hook up the old one some time.....

EDIT: Investigation continues: replugged router gear, added old router into the mix, my XP box now sees my Ubuntu laptop.......
EDIT 2: Got it so that both my ubuntu machines see my XP machine & viceversa, plus shared files. Making progress, so I won't clutter up this thread again unless asked. Part of the answer in my case seems to be making the workgroup name lowercase in the smb.conf file.

---

### Post by Paul41 on 2009-03-26
bump

---

### Post by tospo on 2009-03-26
> **Paul41 said:**
> I get this error when I try to connect with smbclint but I don't know what it means.
I also got this error from the samba client when trying to connect to the server on a new Kubuntu 8.10 install. I could actually see the samba share in the Dolphin file browser and it showed the top level folders correctly but after logging in and trying to access the folders, Doplhin complained with a "File doesn't exist' error.
The solution turned out to be simple:
edit /etc/samba/smb.cnf to add the following lines in the "global" section
> client lanman auth = yes
lanman auth = yes
after restart it all worked fine.

---

### Post by Paul41 on 2009-03-26
Thanks for the suggestion. I tried and I am still getting this error.
> 
Domain=[SANDERS] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_NO_SUCH_USER


---

### Post by Paul41 on 2009-03-28
bump

---

### Post by Paul41 on 2009-03-31
bump

---

### Post by Paul41 on 2009-04-02
bump

---

### Post by agustkara on 2009-04-04
Try change "security = user" to "security = share" in /etc/samba/smb.conf
Might fix your problem.

---

### Post by Paul41 on 2009-04-04
> **agustkara said:**
> Try change "security = user" to "security = share" in /etc/samba/smb.conf
Might fix your problem.

No luck with that :-(

---

### Post by Paul41 on 2009-04-04
OK I finally got it. I was looking through my log files again and say this:
> auth/auth_util.c:create_token_from_username(814)
  lookup_name_smbconf for nouser failed

So I went into my smb.conf file and removed:
```
force user = nouser
force group = nogroup
```

Now things are working fine. I am not sure why it worked with no problems before and then stopped though.

---

### Post by mlinux on 2009-04-13
> **Paul41 said:**
> OK I finally got it. I was looking through my log files again and say this:


So I went into my smb.conf file and removed:
```
force user = nouser
force group = nogroup
```

Now things are working fine. I am not sure why it worked with no problems before and then stopped though.

I have the same problem when first setup 8.10. I follow the howto from this forum and with the above 2 lines, xp pc alway ask for the user name and password to login but always fail even with correct entries.

When I # out the 2 lines, it works again.

Can someone explain what is the purpose of the 2 lines:
force user
force group

---

### Post by bab1 on 2009-04-13
From [Samba.org]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")> [Is a] smb.conf parameter called force user that changes the user accessing a share from the incoming user to whatever user is defined by the smb.conf variable.

You wouldn't notice anything if you were viewing files, but if you create or modify anything it is the "forced user" that owns the file.  The "force group" variable in the smb.conf file works the same for groups.

**Edit:** Just a hunch, but if there is no user created called "nouser", then the force user directive will error with the following: > auth/auth_util.c:create_token_from_username(814)
lookup_name_smbconf for nouser failed 

Did you create a user named "nouser"?

---

### Post by mlinux on 2009-04-13
> **bab1 said:**
> From [Samba.org]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

You wouldn't notice anything if you were viewing files, but if you create or modify anything it is the "forced user" that owns the file.  The "force group" variable in the smb.conf file works the same for groups.

**Edit:** Just a hunch, but if there is no user created called "nouser", then the force user directive will error with the following: 

Did you create a user named "nouser"?

For my case, as I uses same username and password for both Pc and samba, when ";" out the "force" lines, I don't even need to enter any password for samba. Could it be the "WORKGROUP" problem. Here is part of the working smb.conf file
> 
[Share]
    path = /media/samba
    browseable = yes
    writable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
 ;   force user = mlinux
;    force group = WORKGROUP 

---

### Post by bab1 on 2009-04-14
> For my case, as I uses same username and password for both Pc and samba, when ";" out the "force" lines, I don't even need to enter any password for samba. Could it be the "WORKGROUP" problem. Here is part of the working smb.conf file

```
[Share]
path = /media/samba
browseable = yes
writable = yes
read only = no
guest ok = yes
create mask = 0644
directory mask = 0755
; force user = mlinux
; force group = WORKGROUP [COLOR="Red"]**<--Wrong type of group!**[/COLOR]

```

The group used with force group is a user group not a Windows type workgroup.  These user groups hold linux users not computers.

But you are correct; If you are the only user then you do not need to force users or user groups at all.

If you have added the yourself as a smbuser (smbpasswd -a) then you are good.

---

### Post by mlinux on 2009-04-14
lesson learned. Always keep a working conf file before upgrade.

Cheer.

---

