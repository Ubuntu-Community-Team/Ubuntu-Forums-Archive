---
title: "Ubuntu Server 14.04 directory/file sharing issues"
date: 2015-09-10
forum: Server Platforms
---

### Post by charles57 on 2015-09-10
Hi,
I am running Ubuntu Server and have an LVM setup as a share in Samba.   I also have Tonido installed and setup to share as well.   What I am running into is that files saved in Tonido isn't visible anywhere else...  I am also running into issues where files saved on Samba are not visible to other users.  I tried Owncloud and had the same issue.   I have checked the user rights and even set the entire drive's share (folders/files) to 777 with a user/group of nobody:nogroup.  

I was able to get some of the issue fixed with the command lines below.

find /media/shared -type f -exec chmod 777 {} \;



find /media/shared -type d -exec chmod 777 {} \;
Even though all rights are set the same on all directories and folder, some folders are not available on Tonido, while others are.   Same with Samba.  

I am assuming I have not set something up correctly.   I have done a lot searching and just cant find a way to fix the issue.

I want to have the LVM set to share unconditionally, all folders/files with all/any user for Samba and Tonido.   How do I do that?

---

### Post by slickymaster on 2015-09-10
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by charles57 on 2015-09-10
Thank you!   Wasn't sure where to post the question.

---

### Post by bab1 on 2015-09-11
> **charles57 said:**
> Hi,
I am running Ubuntu Server and have an LVM setup as a share in Samba.

One shares portions of the file system that resides on the LV via the SMB protocol.  Using Samba you need to have 3 things correctly configured: There must be a Linux user (adduser), a Samba user (smbpasswd -a) and the correct file system ownership and permissions (chmod and chown).  Have you added the user as both a Linux user and a Samba user?  What is the ownership and permissions of the shared directory?  What share definition parameters have you used for this share?
> 
I also have Tonido installed and setup to share as well.   What I am running into is that files saved in Tonido isn't visible anywhere else... 

Tonido appears to be a WebDAV server.  I would open a separate thread on that subject.  It has nothing to do with Samba other than I would not intermingle the Samba shares with the Tonido shared files at this point; too many variables to sort out.
> 
I am also running into issues where files saved on Samba are not visible to other users.  I tried Owncloud and had the same issue.

What other users.  If you are attempting to share Samba shares over the internet you need to use a VPN for that.  Samba is a LAN application only.  Not sure what Open Cloud has to do with Samba at this point.
> 
I have checked the user rights and even set the entire drive's share (folders/files) to 777 with a user/group of nobody:nogroup. 

I was able to get some of the issue fixed with the command lines below.

```
find /media/shared -type f -exec chmod 777 {} \;

find /media/shared -type d -exec chmod 777 {} \;
```

Drive?  Do you mean share here?  Linux uses the term *drive * to mean the physical disk.  Can I assume you mean a directory at the root of the LV or a partition?  You should not need to set the ownership to *nobody:nogroup* or the permissions to 777 to manage the users access.  Setting the permissions and ownership like you have is a hack for expediency.  It is not correct and it certainly is not secure.
>  
Even though all rights are set the same on all directories and folder, some folders are not available on Tonido, while others are.   Same with Samba.  

I am assuming I have not set something up correctly.   I have done a lot searching and just cant find a way to fix the issue.

I want to have the LVM set to share unconditionally, all folders/files with all/any user for Samba and Tonido.   How do I do that?
Even setting all the folders to, as you say, *share unconditionally* you will still have problems.  I have no experience Tonido, but lots of experience with Samba.  It may be that curing the Samba problems with help with the WebDAV.

Post the output of these terminal commands from the Samba server```

sudo pdbedit -L

cat /etc/samba/smb.conf

df -h

smbtree -d3

```
Please post the various outputs using separate [noparse]```
 
```[/noparse]  code blocks.  You can do this easily by clicking on the [SIZE=5]**# **[/SIZE]icon located at the top of the Advanced Editor that you use to reply back to this thread.

---

### Post by charles57 on 2015-09-11
You say that only a portion is shared.   maybe that is my issue, I have the entire LVM shared (I think).   I could use Tonido to do all the sharing, if it makes sense to do that.   I figure I have something related to the security settings not configured correctly.   I am thinking I should use the same user for both Samba and Tonido, if I continue using both. 

After running this in terminal, I was able to see all the directories in both Samba and Tonido.   However,   I have 2 subdirectories in a folder.  One lets me open it in Tonido, the other gives me an error that it isnt found. both open fine in Samba and on directly on the server.   I checked the rights on both and they are exactly the same.

```
[COLOR=#000000][FONT=Ubuntu Mono]find /media/shared -type f -exec chmod 777 {} \;[/FONT][/COLOR] find /media/shared -type d -exec chmod 777 {} \;
```

I have had issues with saving a file through Samba (or Tonido) and then if I try to view that same file directly on the server, it isn't there (even if I run as root).  Running the above command makes it show up.

Here is the results you asked for.

sudo pdbedit -L
```
bishop0114:1000:Charles

```

cat /etc/samba/smb.conf

```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
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






[Share]
    path = /media/shared
    available = yes
    browsable = yes
    public = yes
    writable = no
    guest ok = yes
    read only = no

```

df -h
```
Filesystem                 Size  Used Avail Use% Mounted on
/dev/sdb1                  103G   23G   75G  24% /
none                       4.0K     0  4.0K   0% /sys/fs/cgroup
udev                       3.8G  4.0K  3.8G   1% /dev
tmpfs                      770M  1.6M  768M   1% /run
none                       5.0M     0  5.0M   0% /run/lock
none                       3.8G  4.0K  3.8G   1% /run/shm
none                       100M  4.0K  100M   1% /run/user
/dev/mapper/public-public  1.8T  1.3T  438G  75% /media/shared

```

smbtree -d3
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface p2p1 ip=192.168.1.200 bcast=192.168.1.255 netmask=255.255.255.0
Enter bishop0114's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.200 ( 192.168.1.200 )
Connecting to 192.168.1.200 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.200 ( 192.168.1.200 )
Connecting to 192.168.1.200 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\CLOUD                  cloud server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name CLOUD<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CLOUD<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CLOUD<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\CLOUD\print$             Printer Drivers
        \\CLOUD\Share              
        \\CLOUD\IPC$               IPC Service (cloud server (Samba, Ubuntu))
    \\BISHOP-PC              
resolve_lmhosts: Attempting lmhosts lookup for name BISHOP-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BISHOP-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BISHOP-PC<0x20>
resolve_hosts: getaddrinfo failed for name BISHOP-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name BISHOP-PC<0x20>
Got a positive name query response from 192.168.1.102 ( 192.168.1.102 )
Connecting to 192.168.1.102 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure

```

---

### Post by darkod on 2015-09-11
I'm no samba expert, but in your Share definition you have:
```
writable = no
read only = no
```

Isn't that a contradiction?

If you want a share open to all you don't even need that many options in its definition. All I have is:
```
[sharename]
   path = /path/folder
   guest ok = yes
   read only = no
```

That's it. Of course, as already mentioned, you need to make sure the /path/folder has correct permissions. For all to write and read you need something like:
```
sudo chmod -R o+rw /media/shared
```

The -R will set the permissions inside the folder structure too, and the o+rw means "add Read and Write to Others", in other words not only for the file owner.

---

### Post by bab1 on 2015-09-11
> **charles57 said:**
> You say that only a portion is shared.   maybe that is my issue, I have the entire LVM shared (I think).   

I was referring to a partition (e.g. a division of the available space on a disk), not a portion.  I was pointing out that you don't need to think of this as a LVM issue at all.
> 

I could use Tonido to do all the sharing, if it makes sense to do that.   I figure I have something related to the security settings not configured correctly.   I am thinking I should use the same user for both Samba and Tonido, if I continue using both. 

Both Samba and Tonido are methods of making part of the file system available to remote users.  I don't manage a WebDAV server, but I do use one that is hosted by someone else.  Both have security settings.  The "user account" does not have to be the same.  If you have multiple user accounts accessing the data you need to ensure that all of those accounts are part of the same user-group.  The access security is provided via the user-group and not the user level.
> 
After running this in terminal, I was able to see all the directories in both Samba and Tonido.   However,   I have 2 subdirectories in a folder.  One lets me open it in Tonido, the other gives me an error that it isnt found. both open fine in Samba and on directly on the server.   I checked the rights on both and they are exactly the same.

Sounds like a Tonido problem, eh?
> 
Here is the results you asked for.

sudo pdbedit -L
```
bishop0114:1000:Charles

```

No other Samba users?
> 
cat /etc/samba/smb.conf
```
...
[Share]
    path = /media/shared
    available = yes
    browsable = yes
    public = yes
    writable = no
    guest ok = yes
    read only = no

```
As mentioned before, you have some conflicting parameters in your share definition.  A simpler share definition would be something like this```

[Share]
    path = /media/shared
    guest ok = yes
    writable = yes

```
This provides a read/write share that is available to all users if you want a read only archive then you can change the *writeable* parameter to: *writable = no*
> 

df -h
```
Filesystem                 Size  Used Avail Use% Mounted on
...

/dev/mapper/public-public  1.8T  1.3T  438G  75% /media/shared

```

This looks okay.  Did you create the mountpoint /media/shared.  The common convention is to use the /media directory for udev mounted media (i.e. usb flashdrives).  I put all my shared data at /srv, but It's really up to you, however.  
> 

smbtree -d3
```
...
    \\CLOUD                  cloud server (Samba, Ubuntu)
...
[COLOR="#0000FF"][B]resolve_hosts: Attempting host lookup for name CLOUD<0x20>
Connecting to 127.0.1.1 at port 445[/B][/COLOR]
...
        \\CLOUD\print$             Printer Drivers
        \\CLOUD\Share              
        \\CLOUD\IPC$               IPC Service (cloud server (Samba, Ubuntu))
...
    \\BISHOP-PC              
...
[COLOR="#008000"][B]name_resolve_bcast: Attempting broadcast lookup for name BISHOP-PC<0x20>
Got a positive name query response from 192.168.1.102 ( 192.168.1.102 )[/B][/COLOR]
Connecting to 192.168.1.102 at port 445
...

```
It appears that there are 2 Samba servers in your network.  The first one (in blue) seems to have the share we are talking about here.  It seems to be using the localhost IP address (127.0.1.1).  That can be causing problems.  Every Ubuntu host has that same address.  It is local to each machine; it refers to itself.

Is the second machine the one you are using for a client?

I think part of your problem is Samba config for user authentication (who are you?) and part of the problem is Linux authorization (you are allowed to do that).

It might be helpful for you to start over and create a test share on CLOUD.  How did you mount the LV at /media/share.  Via fstab?  Via automount (USB plug it in)?

I would remount the LV via fstab.  That will make it a reliable location that is mounted at bootup time. What file system type are you using (e.g ext4)?

Do you really want this share to be open to **_anyone_** who connects to your network?  Maybe you want all users that you manage instead?

You also have a problem with files and directories "created" in the share.  This is also a configuration problem.  It is more a Linux configuration problem.  It is not an obvious thing, but it is a simple config once you know what to do.  Let's to the other things first and then we can work on file ownership when created in the share.

Provide answers to the questions and the terminal output for  ```

cat /etc/fstab

ls -l /media

```

---

### Post by charles57 on 2015-09-12
Not sure why it would show 2 Samba servers.   I only have 1.  I do have a Windows share from my desktop PC (Bishop-PC).  

I think I mounted the drive with fstab.   Again, I am fairly new to Ubuntu server, so I found instructions online and messed around until it worked. 

Here are the results of cat /etc/fstab

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=9926da8d-db86-4a1c-9e4d-f2d0e0a2c685 /               ext4    errors=remount      -ro 0       1
# swap was on /dev/sdb5 during installation
UUID=38405df7-4c8e-4047-afc2-7af041faca59 none            swap    sw                    0       0
/dev/public/public      /media/shared   ext3    user    0       0



```

Here is the results of ls -l /media
```
total 4drwxrwxrwx 14 nobody nogroup 4096 Sep 10 09:04 shared



```

---

### Post by bab1 on 2015-09-12
> **charles57 said:**
> Not sure why it would show 2 Samba servers.   I only have 1.  I do have a Windows share from my desktop PC (Bishop-PC).  

I think I mounted the drive with fstab.   Again, I am fairly new to Ubuntu server, so I found instructions online and messed around until it worked. 

Here are the results of cat /etc/fstab

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=9926da8d-db86-4a1c-9e4d-f2d0e0a2c685 /               ext4    errors=remount      -ro 0       1
# swap was on /dev/sdb5 during installation
UUID=38405df7-4c8e-4047-afc2-7af041faca59 none            swap    sw                    0       0
/dev/public/public      /media/shared   ext3    user    0       0

```

Here is the results of ls -l /media
```
total 4drwxrwxrwx 14 nobody nogroup 4096 Sep 10 09:04 shared



```
You did mount the partition using fstab.  The correct mounting instructions for that line should be ```
/dev/mapper/public-public /media/shared   ext3    user    0       0
```It's a minor point since the system seems to be able to figure out what is going on.

Is this partition really formatted with ext3?  The default formatting is now ext4.

What is in /media/shared ?  Post the output of ```
ls -l /media/shared
```

Did you try the simplified share parameters?  If so, did you restart the Samba daemon?  Here is the command to restart Samba```
sudo service smbd restart
```

---

### Post by darkod on 2015-09-12
@bab1, the /dev/public/public is also correct. There are two ways to refer to LVM, one is /dev/mapper/VGname-LVname and the other /dev/VGname/LVname. That's why it works. The second option is also shorter...

But is mounting it with option 'user' recommended? I mount my data share with defaults and later control permissions with chmod. Could 'user' be the issue depending who is mounting it and who is using it later?

---

### Post by bab1 on 2015-09-12
> **darkod said:**
> @bab1, the /dev/public/public is also correct. There are two ways to refer to LVM, one is /dev/mapper/VGname-LVname and the other /dev/VGname/LVname. That's why it works. The second option is also shorter...

I understand your point.  The only problem I have is that */dev/VGname/LVname *is always translated into /dev/mapper/VGname-LVname.  I feel it's better to not have to translate the listing.  So I'll take simple over shorter.  But is is a very minor point.
> 
But is mounting it with option 'user' recommended? I mount my data share with defaults and later control permissions with chmod. Could 'user' be the issue depending who is mounting it and who is using it later?
The option 'user' allows "non root" users to mount the partition.  From the man page```
The non-superuser mounts.
              Normally,  only the superuser can mount filesystems.  However, when fstab con&#8208;
              tains the user option on a line, anybody can mount the corresponding system.

```
I would add "defaults" so we could have something like this```
<partition>  <mount-point>  <FS>  user,defaults 0  0
```...but there is no need for the ***user*** option since root is mounting the file system.  So it should be one or the other.  I does not affect the use of chmod or chown and it does not affect the initial ownership and permissions on a ext4 file system.

The options are from both fstab and mount.  Here are the fstab options```
  Basic **_file system independent options _**are:

              defaults
                     use default options: rw, suid, dev, exec, auto, nouser, and async.

              noauto do not mount when "mount -a" is given (e.g., at boot time)

              user   allow a user to mount

              owner  allow device owner to mount



```
Of course the file system type (i.e. NTFS or ext4) mount options can differ.

---

