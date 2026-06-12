---
title: "cp only copies directories and not files"
date: 2010-09-27
forum: Server Platforms
---

### Post by GriFF3n on 2010-09-27
I am trying to copy the files from my WHS disk to my Ubuntu Server disk. I have the windows disk mounted at /media/WINDOWS and I want to transfer to /storage so I ran;

```

sudo cp -r /media/WINDOWS /storage

```

It takes about 4-5 seconds and is complete, but there is about 500 GB worth of data there so I know it didn't really copy everything over. When I look at the files in console it shows them, but when I look at the /storage through SAMBA on my Windows machine, it only shows the directories. Am I doing something wrong with the 'cp' command? Is there a better way to do this?

---

### Post by SeijiSensei on 2010-09-27
> **GriFF3n said:**
> Is there a better way to do this?

Use [rsync]("http://www.samba.org/ftp/rsync/rsync.html"). ('sudo apt-get install rsync' if it isn't already there.).

rsync -av /path/to/directory /target

will copy everything in the source to the target.  Next time you run this it will copy only those files that have changed since the last snapshot.

---

### Post by GriFF3n on 2010-09-27
> **SeijiSensei said:**
> Use [rsync]("http://www.samba.org/ftp/rsync/rsync.html"). ('sudo apt-get install rsync' if it isn't already there.).

rsync -av /path/to/directory /target

will copy everything in the source to the target.  Next time you run this it will copy only those files that have changed since the last snapshot.


Yea thats what I was thinking of doing. It just throws me off that 'cp' only copied directories and not files.

---

### Post by GriFF3n on 2010-09-27
rsync does the same thing, makes directories but doesn't copy files. Used the same syntacs as described and no go.

I get;

```

unsupported reparse point

```

for all the files.

---

### Post by CharlesA on 2010-09-27
Try this:

```
sudo rsync -ai /media/WINDOWS/* /storage/
```

---

### Post by GriFF3n on 2010-09-27
> **CharlesA said:**
> Try this:

```
sudo rsync -ai /media/WINDOWS/* /storage/
```


Thanks for the idea but still no go. Maybe it has something to do with file permissions? Not really sure but this is a pretty big problem considering the main objective of this server is a fileserver.

---

### Post by psusi on 2010-09-27
It sounds like you copied the files just fine but you have something wrong with samba.

---

### Post by the_original_billq on 2010-09-27
> **GriFF3n said:**
> I am trying to copy the files from my WHS disk to my Ubuntu Server disk. I have the windows disk mounted at /media/WINDOWS and I want to transfer to /storage so I ran;

```

sudo cp -r /media/WINDOWS /storage

```

It takes about 4-5 seconds and is complete, but there is about 500 GB worth of data there so I know it didn't really copy everything over. When I look at the files in console it shows them, but when I look at the /storage through SAMBA on my Windows machine, it only shows the directories. Am I doing something wrong with the 'cp' command? Is there a better way to do this?

I went back to your original post, because I have a question about how you are verifying that it is not copying files.

From a terminal session on the server, if you do:

find /storage -type f

...nothing shows up?

Let's make sure it's not a Windows or Samba issue...

-Bill

---

### Post by GriFF3n on 2010-09-27
> **the_original_billq said:**
> 
From a terminal session on the server, if you do:

```

find /storage -type f

```

-Bill

I get nothing. I sftp into my box from work using FileZilla. I connect and can navigate my files. I can go into the files I've "copied", but cannot access them. I see the files and their types, but they are not showing the true size or anything. If I do a 'file' on any of the files in these directories, I get a "unsupported reparse point'

---

### Post by the_original_billq on 2010-09-27
Let's understand this a bit better.

Can you create a simple text file in /storage?

Try doing something very simple, like

cp /etc/profile /storage/foo

cat /storage/foo

If that doesn't work, I would ask...  Is /storage local, or a Samba-mounted filesystem?

---

### Post by Jack Monaghan on 2010-09-27
I use
```
cp -auv /directory /new/directory
``` 
to copy my home directory and it copy's all files
the -a is archive the same as -dpR this keeps all permissions and such
the -u to only copy new files
the -v so i know it is doing something

a while back i use to use /* and this caused it to only copy the parent directory of hidden directory's

Jack

---

### Post by psusi on 2010-09-27
Is /storage an NTFS partition?  It sounds like it is and that it's messed up.  Don't use NTFS on a linux server.

---

### Post by GriFF3n on 2010-09-27
> **the_original_billq said:**
> Let's understand this a bit better.

Can you create a simple text file in /storage?

Try doing something very simple, like

cp /etc/profile /storage/foo

cat /storage/foo

If that doesn't work, I would ask...  Is /storage local, or a Samba-mounted filesystem?


That works fine. When I installed the system, I made three partitions, one swap, one root " / " and one storage " /storage". Could this be the problem?

---

### Post by GriFF3n on 2010-09-27
> **psusi said:**
> Is /storage an NTFS partition?  It sounds like it is and that it's messed up.  Don't use NTFS on a linux server.

Not NTFS, formatted as a EXT4 when installing the base system.

---

### Post by CharlesA on 2010-09-27
Post the output of this please:

```
mount
```
```
ls -ld /storage
```
```
ls -ld /media/WINDOWS
```

---

### Post by GriFF3n on 2010-09-27
> **CharlesA said:**
> Post the output of this please:

```
mount
```
```
ls -ld /storage
```
```
ls -ld /media/WINDOWS
```

```
mount

/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda3 on /storage type ext4 (rw)
/dev/sdb2 on /media/WINDOWS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

```
ls -ld /storage

drwxrwxrwx 6 root root 4096 2010-09-27 14:12 /storage


```

```
ls -ld /media/WINDOWS

drwxrwxrwx 1 root root 4096 2010-09-19 19:43 /media/WINDOWS
```

Here you go!

---

### Post by koenn on 2010-09-27
> **GriFF3n said:**
>  When I look at the files in console it shows them, but when I look at the /storage through SAMBA on my Windows machine, it only shows the directories. Am I doing something wrong with the 'cp' command? Is there a better way to do this?
have a look at the owner and permissions on the files as you see them on the console.
Then ask yourself what user account you're using when you look at them via samba, and what sort of access this account would have to directories and files.

---

### Post by GriFF3n on 2010-09-27
> **koenn said:**
> have a look at the owner and permissions on the files as you see them on the console.
Then ask yourself what user account you're using when you look at them via samba, and what sort of access this account would have to directories and files.

If I'm ssh'd in, file permissions shouldn't really have anything to do with it, right? It's a headless server, and I am the only user of the system.

---

### Post by CharlesA on 2010-09-27
> **GriFF3n said:**
> If I'm ssh'd in, file permissions shouldn't really have anything to do with it, right? It's a headless server, and I am the only user of the system.

If the owner and group are set incorrectly, then it would be a problem.

---

### Post by koenn on 2010-09-27
> **GriFF3n said:**
> If I'm ssh'd in, file permissions shouldn't really have anything to do with it, right? It's a headless server, and I am the only user of the system.

you said "when I look at the /storage through SAMBA on my Windows machine, it only shows the directories ..."

do you think it would be normal for any user on any windows machine to have access to any file on your linux server ? 
file permissions have everything to do with it - you can't really troubleshoot an issue until you've verified it's not a permissions problem.

---

### Post by GriFF3n on 2010-09-27
```


samba.conf


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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = WORKGROUP
	os level = 20
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

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

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections

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

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

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
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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

[Server]
	path = /storage
	browseable = yes
	read only = no
	guest ok = no
	create mask = 0644
	directory mask = 0755
	force user = griff3n	
	force group = griff3n
[WHS]
	path = /media/WINDOWS/shares/Server
	browseable = yes
	read only = no
	guest ok = no
	create mask = 0644
	directory mask = 0755
	force user = griff3n
	force group = griff3n


```

and fstab

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=1fb699d0-62eb-42aa-b195-7788b1ba2bef /               ext4    errors=remount-ro 0       1
# /storage was on /dev/sda3 during installation
UUID=f6649404-75dc-4605-8d7b-1ff8717c39c7 /storage        ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=1c5ac9c6-bdab-4f61-b219-76ff64772e0b none            swap    sw              0       0

#Windows Share
/dev/sdb2	/media/WINDOWS ntfs-3g	defaults 0 0 


```

I'm terrible with permissions, do these look ok?

---

### Post by GriFF3n on 2010-09-28
So it looks like its permissions that's not letting me copy the actual files from my Window's drive (/media/WINDOWS) to my Ubuntu Server's drive (/storage). 

```

ls -ld /storage

drwxrwxrwx 6 root root 4096 2010-09-27 14:12 /storage
Code:
ls -ld /media/WINDOWS

drwxrwxrwx 1 root root 4096 2010-09-19 19:43 /media/WINDOWS

```

I am trying to add my user (GriFF3n) to permissions but have no luck. Have tried;

```

sudo chown GriFF3n /media

```

and the permissions stay the same as above with;
```

drwxrwxrwx 1 root root 4096 2010-09-19 19:43 /media

```

Not sure why I can't change permissions. I've done it as root too and still no go. Any ideas?

---

### Post by CharlesA on 2010-09-28
Don't change the owner or permissions on /media. That one needs to be owned by root.

Try this:

```
ls -l /media/Windows/
```

Check the permissions there.

---

### Post by GriFF3n on 2010-09-28
```
ls -l /media/Windows/
```

```

total 29
drwxrwxrwx 1 root root 16384 2010-01-14 22:16 7c4e1a9efd99bb408c050177ea
drwxrwxrwx 1 root root     0 2010-01-15 04:53 DE
drwxrwxrwx 1 root root  4096 2010-01-15 00:28 folders
-rwxrwxrwx 2 root root    16 2010-09-19 19:57 QSM_VolumeID
drwxrwxrwx 1 root root     0 2010-01-15 00:46 RECYCLER
drwxrwxrwx 1 root root  4096 2010-01-15 00:42 shares
drwxrwxrwx 1 root root  4096 2010-08-23 17:58 System Volume Information

```

---

### Post by CharlesA on 2010-09-28
Find a file and try to cp it into your home directory and see if it is able to be copied or errors out.

---

### Post by GriFF3n on 2010-09-28
> **CharlesA said:**
> Find a file and try to cp it into your home directory and see if it is able to be copied or errors out.

It copies to my home folder, but it shows up as a read file. I 'ls -l' on the file and get;

```

unsupported reparse point

```

Broken link? So its not actually copying over the file, just the name of the file?

---

### Post by CharlesA on 2010-09-28
It shows in red? That means it's trying to link to the file, which it can't do on an NTFS partition.

I'm not sure what it is doing.

Try booting off a liveCD and see if you can mount the drive and copy it over.

---

### Post by GriFF3n on 2010-09-28
> **CharlesA said:**
> It shows in red? That means it's trying to link to the file, which it can't do on an NTFS partition.

I'm not sure what it is doing.

Try booting off a liveCD and see if you can mount the drive and copy it over.

Yea, thats what I was thinking about doing too. The sucky part is that its a headless system, so I'll have to connect everything up to it and perform the live boot.

---

### Post by CharlesA on 2010-09-28
> **GriFF3n said:**
> Yea, thats what I was thinking about doing too. The sucky part is that its a headless system, so I'll have to connect everything up to it and perform the live boot.

Ugh. If that doesn't work, I'd suggest taking that problem drive out and hooking it up to a Windows machine and see if it can copy files from it.

---

### Post by GriFF3n on 2010-09-28
> **CharlesA said:**
> Ugh. If that doesn't work, I'd suggest taking that problem drive out and hooking it up to a Windows machine and see if it can copy files from it.


Yep, another option. Thanks again for all the suggestions CharlesA. I'll update once files are copied.

---

### Post by GriFF3n on 2010-09-29
Not looking good. I took the drive out (WHS Drive) and connected it to my main machine (Win7). I was able to see the data, but I can not copy it or access it. Windows says I don't have permission. I think when I chmod it in the server it screwed up the windows permissions. I might have lost all my data!:(

---

### Post by CharlesA on 2010-09-29
If it's in a Windows Home Server machine, then you should be able to access it from that machine. Just take ownership of the files.

User accounts/permissions aren't the same computer to computer, since Windows uses a different GUID for each user account.

---

### Post by GriFF3n on 2010-09-29
I tried to boot the drive and it loads the windows boot screen, and then restarts unexpectedly. Keeps doing this at the same screen too. Won't load into WHS at all.

---

### Post by CharlesA on 2010-09-29
I'd say the drive is toast.

See if you can take ownership of the files from another windows machine and pull the data off.

---

### Post by psusi on 2010-09-29
> **GriFF3n said:**
> Not looking good. I took the drive out (WHS Drive) and connected it to my main machine (Win7). I was able to see the data, but I can not copy it or access it. Windows says I don't have permission. I think when I chmod it in the server it screwed up the windows permissions. I might have lost all my data!:(

You can't chmod files on a windows drive.  If you don't have permission, then change the permissions.

---

