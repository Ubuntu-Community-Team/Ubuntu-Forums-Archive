---
title: "Samba server, not enough disk space with transfers over ~5GB"
date: 2015-07-25
forum: Server Platforms
---

### Post by Higgins909 on 2015-07-25
I've got a new file server but... but this time its on a VM.
At first I though it was my messup with mounting the whole hdd with uuid but I fixed that so its now using a partition like normal.
config:

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
;   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Langweiler]
security = user
encrypt passwords = true
workgroup = workgroup
path = /media
read only = no
guest ok = no
browseable = no
create mask = 775
directory mask = 0755

```
What is causing my transfer at a time limit to be ~5GB? I've got a folder that is 20GB and have transfered a bunch of 5GB sections and watching my disk fill up with df -h
This is a ubuntu server minimal VM install.

---

### Post by volkswagner on 2015-07-26
Are you running a desktop environment?

You shouldn't mount directly at /media.

Please post your /etc/fstab file.

Post output of the following commands:
```
sudo df -h
```
```
sudo du -h / --max-depth=1
```
```
sudo fdisk -l
```

---

### Post by Higgins909 on 2015-07-26
I think you may have hit the nail on the head, makes sence if I think about it.
"You shouldn't mount directly at /media."
But I will wait for more info from you.  Thought I was going to be out of luck.


fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/LangweilerS--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/vda1 during installation
UUID=2699810a-8f52-4c22-8ac3-5dfa3937ad58 /boot           ext2    defaults        0       2
/dev/mapper/LangweilerS--vg-swap_1 none            swap    sw              0       0
UUID=589cbe8b-17f1-4443-ad7b-aa8d2bef795b /media/storage1 ext4 defaults 0 2
UUID=92ec0582-e63b-4b7f-af11-cbb6c706d7fe /media/storage2 ext4 defaults 0 2

```
^must be font as in nano those 2 UUID I added line up perfect.
sudo df -h
```

admin-ben@LangweilerS:~$ sudo df -h
[sudo] password for admin-ben:
Filesystem                        Size  Used Avail Use% Mounted on
udev                              493M     0  493M   0% /dev
tmpfs                             100M  4.9M   95M   5% /run
/dev/mapper/LangweilerS--vg-root  6.5G  836M  5.4G  14% /
tmpfs                             497M     0  497M   0% /dev/shm
tmpfs                             5.0M     0  5.0M   0% /run/lock
tmpfs                             497M     0  497M   0% /sys/fs/cgroup
/dev/vda1                         236M   27M  197M  12% /boot
/dev/sda1                          27G  2.2G   23G   9% /media/storage1
/dev/sdb1                         143G   29G  107G  22% /media/storage2
tmpfs                             100M     0  100M   0% /run/user/1000
admin-ben@LangweilerS:~$

```
sudo du -h / --max-depth=1
```

admin-ben@LangweilerS:~$ sudo du -h / --max-depth=1
4.0K    /srv
3.6M    /etc
0       /sys
6.3M    /sbin
12K     /root
91M     /lib
31G     /media
4.9M    /run
0       /dev
25M     /boot
4.0K    /mnt
32K     /home
9.5M    /bin
16K     /lost+found
295M    /var
417M    /usr
4.0K    /lib64
32K     /tmp
4.0K    /opt
du: cannot access ‘/proc/1981/task/1981/fd/4’: No such file or directory
du: cannot access ‘/proc/1981/task/1981/fdinfo/4’: No such file or directory
du: cannot access ‘/proc/1981/fd/3’: No such file or directory
du: cannot access ‘/proc/1981/fdinfo/3’: No such file or directory
0       /proc
32G     /
admin-ben@LangweilerS:~$

```
sudo fdisk -l
```

admin-ben@LangweilerS:~$ sudo fdisk -l

Disk /dev/vda: 8 GiB, 8589934592 bytes, 16777216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x486bf2d6

Device     Boot  Start      End  Sectors  Size Id Type
/dev/vda1  *      2048   499711   497664  243M 83 Linux
/dev/vda2       501758 16775167 16273410  7.8G  5 Extended
/dev/vda5       501760 16775167 16273408  7.8G 8e Linux LVM

Disk /dev/sda: 27 GiB, 28991029248 bytes, 56623104 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xadd61b22

Device     Boot Start      End  Sectors Size Id Type
/dev/sda1        2048 56623103 56621056  27G 83 Linux

Disk /dev/sdb: 145 GiB, 155692564480 bytes, 304087040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2066546a

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1        2048 304087039 304084992  145G 83 Linux

Disk /dev/mapper/LangweilerS--vg-root: 6.7 GiB, 7226785792 bytes, 14114816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/LangweilerS--vg-swap_1: 1020 MiB, 1069547520 bytes, 2088960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
admin-ben@LangweilerS:~$

```

---

### Post by volkswagner on 2015-07-26
Since you actually have two mount points inside /media, you'll want to have your share defined deeper in the filesystem.

You are trying to include two disk partitions in your share at /media. SAMBA really has no way of telling if /media/storage1/videos
has more space available than /media/storage2/otherfolder.

I found this the hard way. I once tried to keep files in one defined share and control access with ACL's and SAMBA config. When my 
share ran low on disk space, I created a sub dir in the share and mounted additional disk space. Even though the new directory was
on a near empty disk, SAMBA still only showed available disk space for the disk which held the main share directory.

I think you'll need to create two shares one for /media/storage1 and one for /media/storage2.

You second option would be to use some sort of raid, disk pooling, or other mechanism to combine the two physical volumes.

EDIT: Now that I think  about it. Another solution may be for you to use my sub directory example above. 
Since /media/storage1 is only ~23Gigs, you may have good results mounting /dev/sda1 inside a sub directory.
Since we are talking about remounting, you may as well choose a different directory other than /media.

You could create /srv or /srv/data and mount as follows:

/dev/sda1 mount at /srv/data/share/subdir
/dev/sdb1 mount at /srv/data/share

Then create your samba share as
```
path = /srv/data/share
```

I found [this article]("http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm") invaluable for understanding samba permissions and acl's.
If this is the reason you tried to combine all into one share.

The downside to the subdirectory method is if /dev/sdb1 has only 10 gig available disk space but /dev/sda1 is nearly empty with 20 gigs avail, a Windows
user that has the share mapped as a drive will show only 10 gig available for folders inside /srv/data/share/subdir (when in fact there would be 20gig avail).
You may never see this problem if /dev/sdb1 always has less available space.

---

### Post by Higgins909 on 2015-07-31
That sounds pretty nice as I won't have to keep going back to the media place to go back to switch drives.
But for now I will keep it at 
/media/storage1/storage1
/media/storage2/storage2
that got me past the 5GB~ limit.  I still gotta add my 1tb usb drive to it.
/dev/sda1 mount at /srv/data/share   (27gb)
/dev/sdb1 mount at /srv/data/share/145gb
/dev/sdc1 mount at /srv/data/share/1tb

If I ever got hacked and they were looking for data I wonder if they would even look there for my drives.

Thanks!

---

### Post by bab1 on 2015-07-31
> **Higgins909 said:**
> 
If I ever got hacked and they were looking for data I wonder if they would even look there for my drives.

Yes they would.  The preferred location for shared data is at /srv.  See [here]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

---

### Post by Hugo_Serrano on 2015-08-01
> **bab1 said:**
> Yes they would.

No worries trying to hide it by choosing a strange path.
df -f
mount
cat /etc/fstab
cat /etc/mtab
any of those will give it away :D

---

### Post by volkswagner on 2015-08-01
Yes, don't plan [security by obscurity]("https://en.wikipedia.org/wiki/Security_through_obscurity")

A simple recursive search for filetypes with keywords at root filesystem level, doesn't care about directory names or paths.

---

### Post by Higgins909 on 2015-08-02
I did some work right now to my server/VM.  Got them all mounted at srv/data or in that area.
/srv/data  (mounted the 27gb here)
/srv/data/145gb
/srv/data/tb
was moving data to my freshly reinstalled 1tb and got the data error... maybe I will mount the tb at the data location...

what if I were to mount all the drives at the data dir, what would happen?

---

### Post by volkswagner on 2015-08-02
If you follow my example above, you'll want to mount the disk with most available space at /srv/data, then mount disks with less available
space inside that.

You can't mount multiple disks at the same mount point. If mount /dev/sda1 at /srv/data then try to mount /dev/sdb1 at /srv/data, you'll
get a device busy error.

Do you really need that 27 gig disk? Seems like a waste of energy to have that disk spinning if you have a 1TB available.

---

