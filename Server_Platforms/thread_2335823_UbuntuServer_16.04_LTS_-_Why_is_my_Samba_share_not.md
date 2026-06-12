---
title: "UbuntuServer 16.04 LTS - Why is my Samba share not readable or writable."
date: 2016-09-01
forum: Server Platforms
---

### Post by wh33t on 2016-09-01
This is the Share block I've added to my samba.

```

[share]
  comment Wh33tServ Samba
  path /home/wh33t/samba
  browsable = yes
  guest ok = yes
  read only = no
  create mask = 0755

```

This is the directory
```

wh33t@wh33tserv:~$ ls -l
total 12
drwxrwxr-x 2 nobody nogroup 4096 Sep  1 11:36 samba

```

Output from ufw 
```

wh33t@wh33tserv:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
Samba (v6)                 ALLOW       Anywhere (v6)

```

Now the issue is that when I browse the samba share via ip from Win7 (\\192.168.0.3 or \\wh33tserv) both bring up a file browsing window as expected but I cannot read or write files to it. I've even created a blank file in the samba directory but it is not visible from windows explorer. What step am I missing? Thanks for any tips!

---

### Post by cariboo on 2016-09-01
Moved to server platforms.

---

### Post by darkod on 2016-09-01
Try not to create shares in home folders. That is the user home and as such has limitations.

Create any folder that you like, for example /shares or /data and then put subfolders in it and use them for shares. Make sure you set needed permissions on linux level too, because samba permissions on its own are not enough. The linux permissions on the folder have to match and give necessary access to the users you want.

---

### Post by wh33t on 2016-09-01
> **darkod said:**
> Try not to create shares in home folders. That is the user home and as such has limitations.

Create any folder that you like, for example /shares or /data and then put subfolders in it and use them for shares. Make sure you set needed permissions on linux level too, because samba permissions on its own are not enough. The linux permissions on the folder have to match and give necessary access to the users you want.

Aye, I think I'm learning that. I'm also having issues with my Apache webroot being in /home/wh33t/www, it's also encrypted via the install and I think that is giving me a lot of grief. 

So you're suggesting that I just make a directory at the root of the file system and set the permissions accordingly? I want to make it so that any windows computer on my LAN can read/write/delete files and create directories in the Samba share. I'm confused how the permissions need to be for this. When coming in across the windows network does linux detect that as "everyone" or "group" or "user", in which case is samba a user? Linux permissions are really challenging to me for some reason. 

Thank you for replying :D

---

### Post by darkod on 2016-09-01
To create the folder and give everyone RW rights, it would be something like:
```
sudo mkdir -p /data/share
sudo chmod a+rw /data/share
```

The a+rw is something like "give ALL RW rights".

After that set the share definition path to /data/share in smb.conf and restart samba.

When a user connects as "guest" (without specific username and password credentials, linux translates it to nobody. But you don't need to worry about that if you do the a+rw because it simply gives RW to all. Doesn't matter which user you connect as.

That will handle linux permissions. As for samba permissions, with the option guest ok = yes you've said it all. You tell it to allow access by guest (no password needed).

See if that works for you.

PS. If the above doesn't work as it is, you might need to add permissions for the parent folder (/data) too. I'm still not clear on that. So try this:
```
sudo chmod a+rw /data
```

---

### Post by wh33t on 2016-09-01
> **darkod said:**
> To create the folder and give everyone RW rights, it would be something like:
```
sudo mkdir -p /data/share
sudo chmod a+rw /data/share
```

The a+rw is something like "give ALL RW rights".

After that set the share definition path to /data/share in smb.conf and restart samba.

When a user connects as "guest" (without specific username and password credentials, linux translates it to nobody. But you don't need to worry about that if you do the a+rw because it simply gives RW to all. Doesn't matter which user you connect as.

That will handle linux permissions. As for samba permissions, with the option guest ok = yes you've said it all. You tell it to allow access by guest (no password needed).

See if that works for you.

PS. If the above doesn't work as it is, you might need to add permissions for the parent folder (/data) too. I'm still not clear on that. So try this:
```
sudo chmod a+rw /data
```

Hrm, still doesn't seem to work. 

Here is my smb.conf

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
   wins support = yes

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

[filedrop]
  comment Filedrop
  path /samba/filedrop
  browsable = yes
  guest ok = yes
  read only = no
  create mask = 0777

```

Here is the new directories I created as you suggested. (removed the extra output from ls to save space)

```
wh33t@wh33tserv:/$ ls -l
drwxrwxrwx   3 root root  4096 Sep  1 15:56 samba

```

And the filedrop directory

```

wh33t@wh33tserv:/$ ls -l samba/
total 4
drwxrwxrwx 2 root root 4096 Sep  1 15:56 filedrop

```

Firewall output
```
wh33t@wh33tserv:/$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
64738                      ALLOW       Anywhere
Samba                      ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
64738 (v6)                 ALLOW       Anywhere (v6)
Samba (v6)                 ALLOW       Anywhere (v6)

```

Windows is still showing me that the samba server is reachable, but it never shows any contents in the filedrop directory, nor can I read / write to it.

Here is some output from some log files.

```
wh33t@wh33tserv:/$ cat /var/log/samba/log.192.168.0.10
[2016/09/01 11:36:43.953087,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 11:38:27.302781,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 11:38:36.905478,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 11:48:41.365885,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 14:14:41.203452,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 14:17:26.695433,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 14:20:53.087174,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 14:22:46.638817,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 14:23:03.222008,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 14:23:36.304427,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 14:24:58.456186,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 14:25:09.965819,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 16:02:06.197561,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service filedrop - making it unavailable!
[2016/09/01 16:03:46.838658,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service filedrop - making it unavailable!

```

```
wh33t@wh33tserv:/$ cat /var/log/samba/log.wb-WH33TSERV
[2016/09/01 13:25:12.919295,  0] ../source3/winbindd/winbindd.c:271(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
[2016/09/01 14:17:39.641524,  0] ../source3/winbindd/winbindd.c:271(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
[2016/09/01 14:29:18.498259,  0] ../source3/winbindd/winbindd.c:271(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
[2016/09/01 16:01:17.108215,  0] ../source3/winbindd/winbindd.c:271(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)

```

**wh33tbox **is the name of my windows machine
```
wh33t@wh33tserv:/$ cat /var/log/samba/log.wh33tbox
[2016/09/01 11:35:46.858326,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!
[2016/09/01 11:35:49.518224,  0] ../lib/param/loadparm.c:966(lpcfg_service_ok)
  WARNING: No path in service share - making it unavailable!

```

---

### Post by darkod on 2016-09-02
Do you have the winbind package installed? I remember something recently that they did a change in samba and maybe it needs it even when you are not trying to use authentication for the shares.

It doesn't hurt to install it anyway. Try installing winbind and restarting samba.

Another possible problem is the client version. With win10 I think people reported some issues when accessing smb shares, but I don't remember what it was about now. The smb version, or something...

Would you have ubuntu desktop to try access to the share?

---

### Post by wh33t on 2016-09-02
> **darkod said:**
> Do you have the winbind package installed? I remember something recently that they did a change in samba and maybe it needs it even when you are not trying to use authentication for the shares.

It doesn't hurt to install it anyway. Try installing winbind and restarting samba.

Another possible problem is the client version. With win10 I think people reported some issues when accessing smb shares, but I don't remember what it was about now. The smb version, or something...

Would you have ubuntu desktop to try access to the share?

I don't have windbind installed. I will install it and give it a shot. I'm using Windows 7 and my all my Windows 7 computers can share files through the WORKGROUP. I could setup a Ubuntu VM fairly easily. I shall try all those and report back!

---

### Post by darkod on 2016-09-02
I probably should have mentioned this right at the start. Try checking out the samba config with:
```
testparm
```

That warning message in the log "No path in service share" has something to do with it. I think that's why it's not working. Try also googling for that warning message and see what comes up.

The config seems to have a mistake in it but I don't know samba in such detail to find it in your smb.conf even though you posted it.

---

### Post by wh33t on 2016-09-02
> **darkod said:**
> I probably should have mentioned this right at the start. Try checking out the samba config with:
```
testparm
```

That warning message in the log "No path in service share" has something to do with it. I think that's why it's not working. Try also googling for that warning message and see what comes up.

The config seems to have a mistake in it but I don't know samba in such detail to find it in your smb.conf even though you posted it.

Got it working! Thanks so much for your help!

Running testparm indicated that I wasn't setting a path, even though I clearly was. Triple checked that I had a path set. 

My path was set to

```
path = /samba/filedrop
```

When I added a trailing slash

```
path = /samba/filedrop/
```

It just started working. Super weird. But whatever. Glad that it's over and working now. You've been a real help. Thank you.

---

