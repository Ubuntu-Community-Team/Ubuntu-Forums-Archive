---
title: "apt-get upgrade has broken samba again?"
date: 2016-02-19
forum: Server Platforms
---

### Post by Higgins909 on 2016-02-19
So tonight, I decided to sudo apt-get update and sudo apt-get upgrade.
After it was done, I went to resume working on some game server files.
I found out that my shortcut to my server no longer works, but I can get into my share with \\192.x.x.x and find the share and enter it, but I'm not sure if there is any login or what.
But any folder I try to get into, I get "The handle is invalid" or windows can't access that \\192.x.x.x\share\home.
I went and looked at my config and my little share thing is still there.
I've restarted both my ubuntu server and windows 10 computer, with it still doing it.
How do I regain access to my share?

Last time I did this, samba wouldn't even start and I had to reinstall OS after tons of failure.

Thanks,
    Higgins909

---

### Post by darkod on 2016-02-19
Are you sure the updates did this? Was there a samba update? I am doing regular apt-get dist-upgrade on my home server running 14.04.3 and samba and it has never broken samba (yet).

I think there actually was a samba update I applied little while ago but samba is working fine after it.

PS. How can you not be sure if there is a login or not? Also your share config should show what security settings you have. You can always try to modify the share for guest access too, simply to test.

---

### Post by bab1 on 2016-02-19
> **darkod said:**
> Are you sure the updates did this? Was there a samba update? I am doing regular apt-get dist-upgrade on my home server running 14.04.3 and samba and it has never broken samba (yet).

I think there actually was a samba update I applied little while ago but samba is working fine after it.

PS. How can you not be sure if there is a login or not? Also your share config should show what security settings you have. You can always try to modify the share for guest access too, simply to test.

+1  I can confirm that there is no Samba update that can break Samba currently.  

I think this is a misconfiguration.  But nobody can tell what the problem without seeing your configuration.  The error you state sounds like a SMB service endpoint problem or file system problem.  Check your path in the share definition against the directory structure for starters.

---

### Post by Higgins909 on 2016-02-19
I can't tell if I was logged in, because I'm on windows and set it to auto login and its apparently hard to change that.
I tried to connect to my server to the name, instead of ip like I do.  I logged in, but it still did the same thing.

smb.conf  I like to put my shares at the very bottom.
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
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
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

[Gaming Server]
security = user
encrypt passwords = true
workgroup = workgroup
path = /
read only = no
guest ok = no
browseable = yes
create mask = 775
directory mask = 0755

```
I was messing with my gameserver files about 10 minutes before I decided to update and upgrade.
My file structure has not changed.

---

### Post by darkod on 2016-02-19
Sharing the whole / can be an issue in samba. Not sure how big because I've never tried it. But I see it more and more on the forum lately. Personally I would never understand why would anyone share the whole /, on top of the fact it's poor security practice.

Have you tried sharing only the part/folder you need?

---

### Post by bab1 on 2016-02-19
> **darkod said:**
> Sharing the whole / can be an issue in samba. Not sure how big because I've never tried it. But I see it more and more on the forum lately. Personally I would never understand why would anyone share the whole /, on top of the fact it's poor security practice.

Have you tried sharing only the part/folder you need?
+1 to not sharing the entire server file system.  Can you share a subdirectory of /?  One that users have permissions to use?  Maybe something like /data/ or /srv/?

Some other thoughts regarding your share```

[Gaming Server]
security = user  [COLOR="#FF0000"]<-- this goes in the [global] section[/COLOR]
encrypt passwords = true [COLOR="#FF0000"]<-- this also goes in the [global] section[/COLOR]
workgroup = workgroup [COLOR="#FF0000"]<-- and this does too[/COLOR]
path = /  [COLOR="#FF0000"]   <-- this is what darkod and I are talking about.  This path should be to a RW subdirectory of /[/COLOR]
read only = no
guest ok = no
browseable = yes
create mask = 775
directory mask = 0755
```

[COLOR="#0000CD"]**Edit:** On the other hand there was a bug reported over a month ago regarding sharing /.  You can read about that [/COLOR][**here**]("http://askubuntu.com/questions/717610/access-denied-to-samba-share-after-update").
[COLOR="#0000FF"]I still think that you should not share the entire file system. If you need to admin this host you should use SSH to access the system files.[/COLOR]

---

### Post by darkod on 2016-02-19
On top of the above comments, the create mask parameter should not be 775 either (but this is not a problem for the share to work right now). The create mask is applied to files (and the directory mask to folders) and for files you don't need all of them to be created as executable. 775 will give you execute for all. For files you would want something like rw-rw-r-- according to your setting, so that would mean create mask of 664. Simply speaking it works like subtracting -1 from the directory mask.

In fact in linux you very rarely need file to be executable. And definitely not all created files in a share, especially when that share is the whole /.

---

### Post by Higgins909 on 2016-02-19
I started off by trying to change just the share location to /home/the-admin and it seems to have worked, but it does have about a 50% chance to fail.
After changing the smb.conf I went to go restart it.  This Happened.  I tried to do sudo systemctl daemon-reload but that didn't work then restarted and it's back. (the little msg is back)
```

admin-ben@LangweilerG:~$ sudo service samba status
&#9679; samba.service
   Loaded: masked (/dev/null)
   Active: inactive (dead)
Warning: samba.service changed on disk. Run 'systemctl daemon-reload' to reload units.
admin-ben@LangweilerG:~$ sudo service samba restart
Failed to restart samba.service: Unit samba.service is masked.
admin-ben@LangweilerG:~$ sudo systemctl daemon-reload
admin-ben@LangweilerG:~$ sudo service samba status
&#9679; samba.service
   Loaded: masked (/dev/null)
   Active: inactive (dead)
admin-ben@LangweilerG:~$ sudo service samba start
Failed to start samba.service: Unit samba.service is masked.
admin-ben@LangweilerG:~$ sudo service samba status
&#9679; samba.service
   Loaded: masked (/dev/null)
   Active: inactive (dead)
admin-ben@LangweilerG:~$

```

---

### Post by Higgins909 on 2016-02-19
> **bab1 said:**
> 
Some other thoughts regarding your share```

[Gaming Server]
security = user  [COLOR=#FF0000]<-- this goes in the [global] section[/COLOR]
encrypt passwords = true [COLOR=#FF0000]<-- this also goes in the [global] section[/COLOR]
workgroup = workgroup [COLOR=#FF0000]<-- and this does too[/COLOR]
path = /  [COLOR=#FF0000]   <-- this is what darkod and I are talking about.  This path should be to a RW subdirectory of /[/COLOR]
read only = no
guest ok = no
browseable = yes
create mask = 775
directory mask = 0755
```

[COLOR=#0000CD]**Edit:** On the other hand there was a bug reported over a month ago regarding sharing /.  You can read about that [/COLOR][**here**]("http://askubuntu.com/questions/717610/access-denied-to-samba-share-after-update").
[COLOR=#0000FF]I still think that you should not share the entire file system. If you need to admin this host you should use SSH to access the system files.[/COLOR]

I'm not sure if I've ever done a update+upgrade before on this server, as it became a bit of a fear after that happened.
What is RW subdirectory?  

```

[Gaming Server]
security = user  [COLOR=#FF0000]<-- this goes in the [global] section[/COLOR]
encrypt passwords = true [COLOR=#FF0000]<-- this also goes in the [global] section[/COLOR]
workgroup = workgroup [COLOR=#FF0000]<-- and this does too
[/COLOR]
```
I've done a quick look and so far have only found something about masks and workgroup under [global] (will look more later, not enough time atm)
Now I wonder, if there are masks or anything else under a share, it must override the [global]?
I kinda just found some stuff on the internet about samba shares and it looked decent enough to use and it seems to have worked for a little bit anyways.

I know its a bad habit to set shares to the / directory, but sometimes I like to go and read files if I can, with notepad ++ instead of ssh with nano (VI looks super hard to use and the tutorials don't seem to cover basics of how to use in 5 mins)

---

### Post by bab1 on 2016-02-19
> **Higgins909 said:**
> I started off by trying to change just the share location to /home/the-admin and it seems to have worked, but it does have about a 50% chance to fail.
After changing the smb.conf I went to go restart it.  This Happened.  I tried to do sudo systemctl daemon-reload but that didn't work then restarted and it's back. (the little msg is back)
```

admin-ben@LangweilerG:~$ sudo service samba status
&#9679; samba.service
   Loaded: masked (/dev/null)
   Active: inactive (dead)
Warning: samba.service changed on disk. Run 'systemctl daemon-reload' to reload units.
admin-ben@LangweilerG:~$ sudo service samba restart
Failed to restart samba.service: Unit samba.service is masked.
admin-ben@LangweilerG:~$ sudo systemctl daemon-reload
admin-ben@LangweilerG:~$ sudo service samba status
&#9679; samba.service
   Loaded: masked (/dev/null)
   Active: inactive (dead)
admin-ben@LangweilerG:~$ sudo service samba start
Failed to start samba.service: Unit samba.service is masked.
admin-ben@LangweilerG:~$ sudo service samba status
&#9679; samba.service
   Loaded: masked (/dev/null)
   Active: inactive (dead)
admin-ben@LangweilerG:~$

```

If you are running a stand alone server (you do have it configured that way)```
   server role = standalone server
```...you need to restart the smbd daemon, not the samba service.  The samba service is for AD-DC on Samba and not the file sharing component.


On Ubuntu 14.04 you restart smbd like this```
sudo service smbd restart
```...I get this as a response```
smbd stop/waiting
smbd start/running, process 19640
```

You can see the processes running with this```
ps -ef | grep mbd
```

---

### Post by bab1 on 2016-02-19
> **Higgins909 said:**
> I'm not sure if I've ever done a update+upgrade before on this server, as it became a bit of a fear after that happened.

How will you ever learn if you don't overcome your fear?
> 
What is RW subdirectory?  
[QUOTE]A subdirectory that the user has read and write (rw) permissions to.
```

[Gaming Server]
security = user  [COLOR=#FF0000]<-- this goes in the [global] section[/COLOR]
encrypt passwords = true [COLOR=#FF0000]<-- this also goes in the [global] section[/COLOR]
workgroup = workgroup [COLOR=#FF0000]<-- and this does too
[/COLOR]
```
I've done a quick look and so far have only found something about masks and workgroup under [global] (will look more later, not enough time atm)
Now I wonder, if there are masks or anything else under a share, it must override the [global]?
I kinda just found some stuff on the internet about samba shares and it looked decent enough to use and it seems to have worked for a little bit anyways.
[/QUOTE]
But you have no way of knowing, do you?  Why not just read the documentation from Samba.org.  See [**here**]("https://www.samba.org/samba/docs/").  I recommend you read [**this one **]("https://www.samba.org/samba/docs/man/Samba3-ByExample/").  The same processes are used in Samba v4 for file sharing.
> 

I know its a bad habit to set shares to the / directory, but sometimes I like to go and read files if I can, with notepad ++ instead of ssh with nano (VI looks super hard to use and the tutorials don't seem to cover basics of how to use in 5 mins)  If you are just reading the text I would use the command **most** as in ```
most <some-file>
```  You need to install most like this```
sudo apt-get install most
```  Then you can read the manual pages about most with this command```
man most
```

Speaking of which; the manual page for smb.conf is available too.  Try this```
man smb.conf
```

---

