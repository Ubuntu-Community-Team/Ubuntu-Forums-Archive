---
title: "Setting up Samba in 14.04"
date: 2014-03-01
forum: Ubuntu Development Version
---

### Post by Gavin77 on 2014-03-01
I need help setting up samba so that I can access my PC from my android devices.
On Saucy I used this guide which worked perfectly [http://www.maketecheasier.com/install-and-configure-samba-in-ubuntu-for-file-sharing](http://www.maketecheasier.com/install-and-configure-samba-in-ubuntu-for-file-sharing)

I'm currently using Trusty and it doesn't work now, I can't create shares.  The only difference I've noticed in that guide is that it mentions "security = user" but that line is not in the smb.conf here and manually adding it doesn't seem to do anything.

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
   workgroup = HOME-DESKTOP

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


```

---

### Post by Gavin77 on 2014-03-01
For reference, looks like it was a bug in smb.conf [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1261873](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1261873)
I've got it working by using the configuration file from Saucy.

---

### Post by sparker256 on 2014-03-02
I added this just above the #### Networking #### line of the 14.04 smb.conf

```

# What naming service and in what order should we use to resolve host names
# to IP addresses
name resolve order = lmhosts wins bcast host

#### Networking ####

```

Bill

---

### Post by LY6n6fH on 2014-03-26
I had to switch from "valid users = user1 user2 ..." to "username = user1, user2 ..." to get samba working on 14.04

---

### Post by rtalcott on 2014-03-27
@LY6n6fH  THANK YOU! That worked!

---

### Post by sdowney717 on 2014-03-27
I had a line
valid users = %s

I changed to 
username = %s

Is this what your saying to do?

---

### Post by rtalcott on 2014-03-27
That is what I did based on LY6n6fH's instructions above...and it's worked for me...I changed it in the global and specific share definitions...

---

### Post by sdowney717 on 2014-03-27
> **rtalcott said:**
> That is what I did based on LY6n6fH's instructions above...and it's worked for me...I changed it in the global and specific share definitions...

yes, that does work. I shared a folder in file manager.
Then went to a windows PC (using google chrome desktop)
And it shows up in the network.:KS

I suppose a good question is why it works?
And why does 14.04 use 'valid users' which does not work?

---

### Post by rtalcott on 2014-03-27
I suppose a good question is why it works?

I have no clue but I've had the problem for a few months at least...my guess was something in the new smb.conf was the problem but I was thinking maybe password encryption...I would have never figured this out...it appears as if someone made a change without considering the entire downstream impact which makes one wonder about the Quality System that is in place.

---

### Post by Morbius1 on 2014-03-27
It's not that "valid users" does not work. It's because of an incomplete removal of the original Debian [homes] share. From the bug report:
>                         In the "#======================= Share Definitions ======================="  section of smb.conf exists the original [homes] share from Debian which  looks like this but is scattered throughout the section:

 [homes]
   comment = Home Directories
   browseable = no
   read only = yes
   create mask = 0700
   directory mask = 0700
   valid users = %S

 Ubuntu usually comments out this share but in this case it was  incomplete. Only [homes], "comment = Home Directories", and "browseable =  no" were commented out.

 This leaves "read only = yes", "create mask = 0700", "directory mask =  0700" and [COLOR=#0000cd]"valid users = %S"[/COLOR] intact and [COLOR=#0000cd]interpreted by samba as global  parameters[/COLOR] which makes a mess of things. In this particular bug report  having "valid users = %S" interpreted as a global parameter induces the  originally posted error message.
 All of the [homes] share parameters must be commented out.

              


---

### Post by rtalcott on 2014-03-27
Morbius1  THANK YOU!

---

### Post by sdowney717 on 2014-03-27
I commented out [homes] with a # in front of all lines

then ran testparm
username option it says is an old thing.
So what should be used?

```
scott@scott-P5QC:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Videos]"
WARNING: The "username" option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts, wins, bcast, host
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Videos]
	path = /home/scott/Videos
	username = scott
	read only = No
	guest ok = Yes
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2014-03-27
ALSO, how does smb.cnf work with nautilus shares?
Are they written into smb.cnf?

How can I list all my shares?

---

### Post by Morbius1 on 2014-03-27
"username = " was deprecated when Eisenhower was still in Europe so use "valid users = scott". ( That might be a wee bit of an exaggeration ) 

nautilus-shares are controlled by samba ( and smb.conf ) but their share definitions are in /var/lib/samba/usershares. For the shares created through Nautilus you can always see what you shared and how you shared them using the following command:
```
net usershare info --long
```

---

### Post by sdowney717 on 2014-03-27
thanks morbius, so 'valid users'is good to use.

testparm did not show any problems

```
scott@scott-P5QC:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Videos]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts, wins, bcast, host
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Videos]
	path = /home/scott/Videos
	valid users = scott
	read only = No
	guest ok = Yes
scott@scott-P5QC:~$ 

```

---

### Post by Morbius1 on 2015-01-31
Please start your own new topic.

This section was for pre-released Ubuntu, it's marked as [SOLVED], and is unrelated to your situation.

When you do post include the output of:
```
testparm -s
```
And specify which "graphical tool" you used. There are several. Some are benign ( system-config-samba ) and some are dangerous ( gadmin-samba ).

[COLOR=#0000cd]*Note: Don't be too obsessed with things in smb.conf not showing up in testparm. Some items are commented out and despite it's name smb.conf is not THE samba configuration file. It's a set of additions and overrides to the default settings of samba. By default testparm shows you the affect smb.conf has on those default settings.*[/COLOR]

---

### Post by cariboo on 2015-01-31
Thread closed, and christian53's post moved to a thread of it's own in General Help.

---

