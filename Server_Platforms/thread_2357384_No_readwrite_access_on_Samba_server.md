---
title: "No read/write access on Samba server"
date: 2017-04-01
forum: Server Platforms
---

### Post by liam0102 on 2017-04-01
Hi,

I'm trying to setup my raspberry pi as an all purpose media server/file server, and having gotten Plex running the only remaining issue is remote file access.
I have installed Samba and can access the files from another machine but I cannot write to the drive (Delete files or create new ones).

Here is my config file for samba:
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


[homes]
   comment = Home Directories
   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0777


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0777


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
[usb]
comment = USB Share
path = /mnt/library
writeable = Yes
only guest = Yes
create mask = 0777
directory mask = 0777
browseable = Yes
read only = no
public = yes
force user = pi
force group = users
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


```

---

### Post by mikewhatever on 2017-04-01
Take a look at the permissions of /mnt/library:
```

ls -d /mnt/library

```

---

### Post by liam0102 on 2017-04-01
That command just returns this:
```

/mnt/library

```

But I believe these are the permissions:
```

drwxr-xr-x 1 root root 131072 May 29  2016 Films
drwxr-xr-x 1 root root 131072 Aug  6  2016 $RECYCLE.BIN
drwxr-xr-x 1 root root 131072 Aug  6  2016 System Volume Information
-rwxr-xr-x 1 root root   9432 Apr  1 18:09 t.conf
drwxr-xr-x 1 root root 131072 Mar 28  2016 TV Shows

```

---

### Post by darkod on 2017-04-01
So if root is the owner of the folders and the permissions for Others are r-x how do you expect to have Write permissions? :)

After creating new folders to be used for shares as root, always change owner and/or group ownership to adjust to how you plan to control your access (by user, by group, all the rest, etc).

Basically you need to add W permissions and be careful how you do it. It's best to use chmod g+w or chmod o+w in my opinion, instead something like chmod 777 because that recursevely will add execute to all files too.

---

### Post by liam0102 on 2017-04-01
I have previously run:
```

chmod -R 777 /mnt/library

```

And have just run:
```

[COLOR=#000000][FONT=Menlo]sudo chmod -R g+w /mnt/library
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Menlo]

But the permissions are the same.

Could this be an issue with how the drive is mounted? Here's my fstab:
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Menlo]proc            /proc           proc    defaults          0       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/mmcblk0p6  /boot           vfat    defaults          0       2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/mmcblk0p7  /               ext4    defaults,noatime  0       1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sda2       /mnt/library    exfat   defaults          0       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# a swapfile is not a swap partition, no line here[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#   use  dphys-swapfile swap[on|off]  for that
[/FONT][/COLOR]
```

---

### Post by darkod on 2017-04-01
Maybe. Looks like sda2 is FAT, which even windows doesn't use these days. If you plan to use it only in ubuntu, better make that ext4. Of course formatting the partition will lose any data on it.

Honestly I don't know if this is the issue because simply I have never tried to use FAT partition mounted in ubuntu. For disks that are planned to be used in the server (not removeable) I always use ext4. And never had issues with permissions ending up different from what I tell them to be.

---

### Post by liam0102 on 2017-04-01
It's an exfat but I can obviously write to the drive locally (From the raspberry pi), but not from a remote machine (In this case a Macbook Pro).

So after playing with the mounting I've managed to get my permissions looking like this:
```

[COLOR=#000000][FONT=Menlo]drwxrwxr-x 1 pi pi 131072 May 29  2016 Films[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x 1 pi pi 131072 Aug  6  2016 $RECYCLE.BIN[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x 1 pi pi 131072 Aug  6  2016 System Volume Information[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rwxr-xr-x 1 pi pi   9432 Apr  1 18:09 t.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x 1 pi pi 131072 Mar 28  2016 TV Shows

```

But I'm still unable to write to the folders[/FONT][/COLOR]

---

### Post by mikewhatever on 2017-04-01
I'd try to chown only the mount point, just unmount the partition first, and then remount:
```

sudo umount /dev/sda2
sudo chown pi:users /mnt/library
sudo mount -a

```
Then check permissions again with ls -l.
The idea is that files and folders under the mount point should inherit its permissions. I am not familiar with exfat, and do not know if commands like chmod work.

---

### Post by liam0102 on 2017-04-01
Having just tried that file permissions seem unchanged:
```

[COLOR=#000000][FONT=Menlo]drwxrwxr-x 1 pi pi 131072 May 29  2016 Films[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x 1 pi pi 131072 Aug  6  2016 $RECYCLE.BIN[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x 1 pi pi 131072 Aug  6  2016 System Volume Information[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rwxr-xr-x 1 pi pi   9432 Apr  1 18:09 t.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxr-x 1 pi pi 131072 Mar 28  2016 TV Shows

```[/FONT][/COLOR]

---

### Post by mikewhatever on 2017-04-01
Check if it works over samba now. The pi:pi permissions are ok, since you use <force user = pi>.

---

### Post by liam0102 on 2017-04-01
WOOHOO! It works now :D
Thank you to everyone helped!

---

### Post by darkod on 2017-04-01
It might be worth restarting samba, or in fact the whole Pi, to make sure all is loaded fresh again. Otherwise I agree, with using force user pi it should work because now owner is pi : pi. And double check if that ownership is inherited below. It's not worth much if only /mnt/library owner is pi : pi but not the folders below.

---

### Post by darkod on 2017-04-01
Ah, ok, great. You can mark it Solved in Thread Tools above the first post.

---

### Post by liam0102 on 2017-04-01
Yeah, I restarted samba after every config change and the permissions appear to be inherited.

---

### Post by mikewhatever on 2017-04-01
It should work, but check if you can create files over samba and what are their permissions. Also, I am not sure under which user Plex is run, and what permissions it needs, but that could be tuned in due course.

---

### Post by liam0102 on 2017-04-01
All seems to be ok. I can write and read remotely and consequently delete any newly added files, so all seems to be in order now.

---

