---
title: "Help with shares"
date: 2016-07-12
forum: Server Platforms
---

### Post by imballinger on 2016-07-12
I am a complete novice, and wanted to set up a plex sever. My machine has 4 hard drives plus the one ubuntu is installed on, the other 4 hard drives I want to be accessible over the network, I believe I have set everything up right, I can see the shares from a windows 10 machine but I can't access them.

I hope someone has the patience to help me

---

### Post by howefield on 2016-07-12
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by nerdtron on 2016-07-12
>  I believe I have set everything up right, I can see the shares from a windows 10 machine but I can't access them. 

Hello imballinger,
Welcome to the forums.

How did you setup the share? I assume it is a samba share? Can you post here your samba config? What error are you having on the windows machine? Did you properly setup the user/password allowed for the share?

---

### Post by imballinger on 2016-07-12
This is where i will annoy you as I am a total novice. How do I get my samba config?

To set up the share went into the permission of the hard drive set the group to samba share, then local network share I set allow on everything

when I click on the share on my windows pc I get a error saying windows cannot access, you don't have permission.

And what do you mean setup user/password for the share?

>   

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
```

---

### Post by Morbius1 on 2016-07-12
You created a samba usershare so you will need to post the output of this command as well:
```
net usershare info --long
```

---

### Post by imballinger on 2016-07-12
Ok will do, just a quick update though, I don't know what I did but I can now access the share on the windows P.C but the problem is that whenever I restart the Ubuntu computer my shares all reset then I have to set them up again.

```
ian@Server:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/data31 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/bbb is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Data1]
path=/media/ian/Data1
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/untitled folder is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/data 4 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/data 3 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/data 20 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/data 2 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
ian@Server:~$
```

---

### Post by Morbius1 on 2016-07-12
> but the problem is that whenever I restart the Ubuntu computer my shares all reset then I have to set them up again.         

The forum today is so slow I don't know how much longer I will be in it but my guess is you aren't auto-mounting your partitions that hold the shared folders. If you don't have anything defining the partition in /etc/fstab you aren't automount it. It's not that you have to set up the shares again it's that you didn't mount the partition so go into Nautilus and mount them.

---

### Post by imballinger on 2016-07-12
ok but how do I get them to mount automatically?

Right I have got it to auto mount by using the disks program and selecting auto mount, but now the permissions on the drive has changed the owner to being root, and I can't change permissions

---

### Post by Morbius1 on 2016-07-13
Need to see how the partition was mounted so post the output of this command:
```
cat /etc/fstab
```

---

### Post by imballinger on 2016-07-14
ian@Server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=8f509544-c532-496d-8b06-5654f2d52a82 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8145836a-f16a-4b5d-85f6-85babcaefc4f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/disk/by-uuid/508B26AE21FC3FA0 /mnt/508B26AE21FC3FA0 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/001DC79C2F23DED5 /mnt/001DC79C2F23DED5 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Data%201 0 0
ian@Server:~$

---

### Post by Morbius1 on 2016-07-14
Lordy, I hate the way Disks manges fstab.
> but now the permissions on the drive has changed the owner to being root, and I can't change permissions         
I assume this is the line in question:
>  /dev/disk/by-uuid/001DC79C2F23DED5 /mnt/001DC79C2F23DED5 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Data%201 0 0
Yes it will be owned by root but it will have permissions of 777 throughout because it's NTFS so everyone should have access.

Is the problem that you can't create a usershare of the partition through Nautilus because it's owned by root? If that's that's the problem just run Nautilus as root:
```
sudo -H nautilus
```
If you really want to take ownership of the partition add uid=1000 to the list of options:
> /dev/disk/by-uuid/001DC79C2F23DED5 /mnt/001DC79C2F23DED5 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Data%201[COLOR=#0000cd]**,uid=1000**[/COLOR] 0 0

[COLOR=#0000cd]*Note: I'm assuming your uid is 1000 which is the default. Run this command to find out if yours is different:*[/COLOR]
```
id
```

---

### Post by imballinger on 2016-07-14
> **Morbius1 said:**
> Lordy, I hate the way Disks manges fstab.

I assume this is the line in question:

Yes it will be owned by root but it will have permissions of 777 throughout because it's NTFS so everyone should have access.

Is the problem that you can't create a usershare of the partition through Nautilus because it's owned by root? If that's that's the problem just run Nautilus as root:
```
sudo -H nautilus
```
**_If you really want to take ownership of the partition add uid=1000 to the list of options:_**


[COLOR=#0000cd]*Note: I'm assuming your uid is 1000 which is the default. Run this command to find out if yours is different:*[/COLOR]
```
id
```


And how do I add the 1000, and for all four hard drives?

---

### Post by Morbius1 on 2016-07-14
You don't add "uid=1000" to all 4 hard drives ( they are called partitions in Linux ). You can only add it to the NTFS partitions you listed at the end of fstab.

And you add them by editing fstab as root:
```
sudo -H gedit /etc/fstab
```

I'm guessing you can use Disks to do that as well./

---

### Post by imballinger on 2016-07-14
Thank you so much for all your help :)

One last thing though, How do I add plex as a user so it has permissions to access my drives?

---

### Post by Morbius1 on 2016-07-14
I know nothing about plex and how it works but everyone should have access to your partitions - at least from within that machine.

If your run:
```
ls -dl /mnt/001DC79C2F23DED5
```
It should come back with something like this meaning everyone has access to the partition:
> drwxrwxrwx .....

If "plex" is an actual user name and it has a corresponding group of "plex" you can add that group if you want:
> /dev/disk/by-uuid/001DC79C2F23DED5 /mnt/001DC79C2F23DED5 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Data%201[COLOR=#000000],uid=1000[/COLOR][COLOR=#0000cd]**,gid=plex**[/COLOR] 0 0

---

### Post by TheFu on 2016-07-16
If plex is running on the Linux machine, then you don't need any "shares" to windows or any other plex client/DLNA client.  All that is needed is for plex to have at least read-access to the directories and files with the media laid out in the prescribed plex way.  That is important. If these disks are going to be permanently mounted under Linux, using a Linux file system, not NTFS, would be easier long term. Then the storage permissions could managed with normal, expected, userids and groups.  You can setup samba or just use sftp to move files over from Windows, if you need that.  I find that file management from the shell is much faster than using a GUI. To each their own.

If you have specific questions about plex, I've been running it and Kodi for about 3 yrs. Don't use Windows much and don't have a plex account, so those things I cannot help with. Sorry.

A slight correction.  "Automount" is a specific term used by Unix/Linux people to say that a process manages the mounting on-demand, not at boot (unless that is needed).  On current Linux systems, **autofs** is the tool which does this and there isn't any change to the fstab file. Both local and network storage can be mounted using autofs on-demand. It is common in a business to have user HOME directories mounted as they login to each server, but it be the same network storage. Back in the 1990s, we used amd for the same purpose and mounting HOME at login was much more popular than it is today.  All my startup scripts had to understand about 8 different Unix platforms.  Don't know that this level of detail is needed, just trying to be technically accurate - saying "automount" means something specific to system admins. That's all.

---

