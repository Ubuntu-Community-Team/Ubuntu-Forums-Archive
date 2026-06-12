---
title: "need samba.conf file that comes with 14.04 64 bit"
date: 2014-02-25
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-25
I purged mine and have ziltch.
Maybe I can get things working like they were before I installed samba and uninstalled samba and now reinstalled samba.

here is my samba.conf, nothing

Or I dont know, I have no idea.

miniDLNA was working till I did all the above. Now no client can get access.

---

### Post by sdowney717 on 2014-02-25
doing this as it should do it.

sudo apt-get purge samba samba-common
sudo apt-get install samba

---

### Post by sdowney717 on 2014-02-25
I dont know, caused a serious ubuntu error, which automatically reported.

And no more sharing option tab.

reboot needed?

---

### Post by sdowney717 on 2014-02-25
lost all sharing options in properties.
It used to say local share options

tab is gone away.

---

### Post by sdowney717 on 2014-02-25
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

I followed this guide, but not working.
I tried viewing a share from win7, but get a login window and it asks for a password.
And I dont know what password as the samba password does not work.
Would the 'network password' that win7 wants be the smb password from this guide???
Who knows!

here is my smb.conf

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

---

### Post by sdowney717 on 2014-02-25
I figure it is foobared. Easiest thing is to reinstall OS later date when it is more ready.
I dont absolutely have to have file sharing working.

Several ubuntu Os's ago I also had this problem and it took dedicated multi day help from one of the guru's on the network forum to make it work.
Back then I realized samba is just too hard and today is not any better.

---

### Post by sparker256 on 2014-02-25
I had to add this above the  #### Networking #### line to get my file sharing working.
> 
# What naming service and in what order should we use to resolve host names
# to IP addresses
name resolve order = lmhosts wins bcast host

#### Networking ####


Bill

---

### Post by sdowney717 on 2014-02-26
Some thing still wrong.
I added the line and 

```


scott@scott-P5QC:~$ sudo restart smbd
[sudo] password for scott: 
smbd start/running, process 14292
scott@scott-P5QC:~$ sudo service smbd restart
smbd stop/waiting
smbd start/running, process 14408
scott@scott-P5QC:~$ 

```

And still get no access from win7 to this ubuntu pc

Since I lost the sharing tab in file manager completely gone away, I assume my system is foobar.

---

### Post by rtalcott on 2014-02-26
I too am having Samba file sharing problems...running Xubuntu 13.10 and 14.04....no problems with 13.10 or 14.04 to 13.10 but no luck from 14.04 to anything...13.10 or 14.04 on multiple machines...it dropped for me from when I installed 14.04....I check all the usual suspects....accounts, passwords, encryption and all seemed well.

---

### Post by philhughes on 2014-02-26
In the section [homes] under share definitions, *everything* is normally commented out in the default smb.conf. Try commenting out the lines:

   read only = yes
   create mask = 0700
   directory mask = 0700
   valid users = %S

though I think the valid users = %S is the critical one.

Since [homes] is itself commented out, this makes the entry global. I *think* this means that a share named Videos can only be accessed by a user named Videos, though others more knowledgeable about samba may care to comment. I guess if this was the default, it may be a bug?

---

### Post by Mr Fat Bat on 2014-03-16
Did anyone manage to resolve this??  I also have had the sharing tab disappear from nautilus!  

Tried purging/re installing samba & samba-common, also tried by smb.conf from 13.10 and 13.04, as well as all the comments above!

Any luck with anyone?

Cheers, J

---

### Post by sdowney717 on 2014-03-16
yes, you need to install nautilus share
here are my sambas

---

### Post by Mr Fat Bat on 2014-03-16
**sudo apt-get install nautilus-share** solved this for me!!!

Thanks mate!!!

---

