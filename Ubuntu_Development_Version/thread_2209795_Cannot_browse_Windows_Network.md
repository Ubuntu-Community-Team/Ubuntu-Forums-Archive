---
title: "Cannot browse Windows Network"
date: 2014-03-07
forum: Ubuntu Development Version
---

### Post by kprowell5150 on 2014-03-07
I just installed Ubuntu Gnome 14.04.  So far everything is working perfectly out of the box except I cannot browse Windows Network in Files.  At the command prompt I don't even get any results when I run smbtree.  Samba is installed and the service is running.  I've been away from Linux/Buntu a while but I seem to remember this being an issue before.  I will say that on the same machine it works fine with Mint but I'm not a big fan of it and I am really liking Ubuntu Gnome 14.04 so I prefer to stay here and get it sorted out.  Oh, and as a test I disabled the firewall in case it was blocking it.  Still, nothing.  Looking forward to a quick fix and a lesson on how to handle this in the future.

Thanks

Kevin

---

### Post by sdowney717 on 2014-03-07
my /etc/samba/smb.conf

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
name resolve order = lmhosts wins bcast host
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

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

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

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
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

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# The following parameter makes sure that only "username" can connect
# to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

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


[Videos]
path = /home/scott/Videos
available = yes
valid users = scott
read only = no
browseable = yes
public = yes
writable = yes
```

my smbtree
```
scott@scott-P5QC:~$ smbtree 
Enter scott's password: 
WORKGROUP
	\\SCOTT-P5QC     		scott-P5QC server (Samba, Ubuntu)
	\\LR-PC          		
		\\LR-PC\Users          	
		\\LR-PC\testshare      	
		\\LR-PC\Recorded TV    	
		\\LR-PC\Public         	
		\\LR-PC\IPC$           	Remote IPC
		\\LR-PC\E$             	Default share
		\\LR-PC\C$             	Default share
		\\LR-PC\ADMIN$         	Remote Admin

```

---

### Post by sdowney717 on 2014-03-07
my installed samba packages

---

### Post by kprowell5150 on 2014-03-07
Thanks!  I'll compare settings and packages and let you know;

---

### Post by kprowell5150 on 2014-03-07
No go...  Same packages installed and config is the same.  I can find my storage server using "Connect to Server" and typing in smb://servername  but it cannot just browse the network.

---

### Post by sdowney717 on 2014-03-08
Might be the windows computer blocking LAN access even with firewall off.

I once had an issue where the windows PC had insufficient resources, a reboot made the LAN file sharing work.

---

### Post by cariboo on 2014-03-08
I saw somewhere that using the etc/samba/smb.conf file from 13.10 solves the problem.

---

### Post by Ian_Worrall on 2014-03-09
Have you tried connecting to smb://<IP Address> instead of smb://<Servername> ?

---

### Post by kprowell5150 on 2014-03-09
@Ian_Worrall:  Yes I have tried that and it does work.  I tried a USB boot of Mint and it browses perfectly.  This has happened before with Ubuntu and I just can't remember how to fix it.  If I recall, one of the times it had something to do with gvfs but I may be wrong.

@sdowney717:  I would agree if it didn't work with Mint

@cariboo907:  I may have to grab one and try that.  If it works I will let you know and hopefully it doesn't break on the next update.

---

### Post by sdowney717 on 2014-03-10
try mints samba.cnf

mount a share from commandline using cifs

[http://geekswing.com/geek/linux/mounting-windows-shares-on-linux-using-sambacifssmbfs/](http://geekswing.com/geek/linux/mounting-windows-shares-on-linux-using-sambacifssmbfs/)

---

### Post by philhughes on 2014-03-10
In the section [homes] under share definitions, *everything* is normally commented out in the default smb.conf. Try commenting out the lines:

    read only = yes
    create mask = 0700
    directory mask = 0700
    valid users = %S

though I think the valid users = %S is the critical one.

Since [homes] is itself commented out, this makes the entry global. I *think* this means that a share named Videos can only be accessed by a user named Videos, though others more knowledgeable about samba may care to comment. I guess if this was the default, it may be a bug?

---

### Post by Gavin77 on 2014-03-10
Use the smb.conf file from comment 4 in this bug report [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1261873](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1261873)

I had a problem with samba recently and this fixed it.

---

### Post by Morbius1 on 2014-03-10
> **philhughes said:**
> In the section [homes] under share definitions, *everything* is normally commented out in the default smb.conf. Try commenting out the lines:

    read only = yes
    create mask = 0700
    directory mask = 0700
    valid users = %S

though I think the valid users = %S is the critical one.

Since [homes] is itself commented out, this makes the entry global. I *think* this means that a share named Videos can only be accessed by a user named Videos, though others more knowledgeable about samba may care to comment. I guess if this was the default, it may be a bug?
You are correct. There is a bug report here on this: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1261873](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1261873)
Which talks about this error message:
> 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Access denied.
And that is because of what you said - an incomplete commenting out of the debian [homes] share. In fact the only parameter that matters in this regards is "valid users = %S" which sits in the global section and blocks this "Everyone" character. Of cource the create mask and directory mask should also be commented out since they don't belong in the global section either.

But all of this is for creating shares for others to access not accessing someone else's shares. I just installed the latest build and have no problems browsing and accessing other hosts. Maybe they fixed this part already.

---

### Post by sdowney717 on 2014-03-12
It has died for me too now.
I do not see any shares in file manager

```
scott@scott-P5QC:~$ smbtree
Enter scott's password: 
scott@scott-P5QC:~$ 
```

I did not do anything except updates.:sad::sad::sad:

---

### Post by sdowney717 on 2014-03-13
I restarted, no good.

I copied my samba that worked back over into smb.cnf, 
and restarted, no good.

I compared installed packages, they are the same.

So must be a bug!
It had been working fine and yesterday I noticed it not working.

---

### Post by Morbius1 on 2014-03-13
If smbtree produces no output and you've eliminated the firewall as a culprit it's likely that nmbd isn't started or started too late. Either start it:
```
sudo service nmbd start
```
OR, restart it:
```
sudo service nmbd restart
```
I'm doing an update now so I'll see if something breaks browsing when it's done.

---

### Post by sdowney717 on 2014-03-13
Ok, ran that command, still dead no lan browse.
interesting that I went form working browse to non working browse.
I would like to get it back to working as I do use it. I have to run downstairs with a thumb drive now.

---

### Post by sdowney717 on 2014-03-13
trying to connect to server name gives a connection refused error. However other windows machines can see these window machines the whole time. And browse shares.

---

### Post by sdowney717 on 2014-03-13
Did an update and a little progress. still an error name not unique?
Maybe it will work again soon?

---

### Post by sdowney717 on 2014-03-14
I just did another update.
I can now connect to a windows share but only by connecting to server using for example

```
smb://lr-PC
```

I still can not just click browse network and have it show anything, which used to work.

---

### Post by jerrylamos on 2014-03-14
Looking at /etc/samba/smb.conf I noticed this line was missing:

name resolve order = bcast lmhosts host wins

I put that line just before the networks section and now I can see the XP computers & the shared files.

---

### Post by jerrylamos on 2014-03-17
I had to insert this line into /etc/samba/smb.conf just before Networking:

name resolve order = bcast lmhosts host wins

I also append this to the bottom of smb.conf:

[jerry]
path = /home/jerry
available = yes
browsable = yes
public = yes
writable = no

Then I can access the two XP's on the home network for the sharable folders.  Oh, the printer too.

---

### Post by kprowell5150 on 2014-04-24
Bump...

Anyone else having this issue.  Now that 14.04 has been released it still doesn't work.  I got it to work one time the other day by adding rules in the firewall to allow smb traffic.  Once I did that it worked that day.  The next day.  Nothing.  I even disabled the firewall and still I cannot browse the network.  I can however go straight to a smb share if I connect directly to smb://server/share.  I just can't open Files and browse available shares.

---

### Post by coffeecat on 2014-04-24
Since 14.04 is now released and this forum is for the development version...

Thread closed.

If anyone needs help with 14.04 please start a new thread in one of the regular support sections. @kprowell5150, you will likely get more responses if you start a new thread.

---

