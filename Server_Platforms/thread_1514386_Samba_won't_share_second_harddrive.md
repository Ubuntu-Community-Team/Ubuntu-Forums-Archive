---
title: "Samba won't share second harddrive"
date: 2010-06-20
forum: Server Platforms
---

### Post by mkmcllln on 2010-06-20
Hi all,

My first post, and I'm an Ubuntu n00b.  But I've done a lot of reading and still can't seem to get anywhere with this.

First of all.  I know that I've set Samba up correctly because I can create a share in /home/documents which is mounted on my primary hard drive /dev/sda1, Windows 7 can access it no problem. But, when I try to set up a Samba share on my second hard drive /dev/sdb1, Windows 7 cannot access it.  I've mounted the share in /media/Share
The error I get in Window 7 is: " Windows cannot access \\HOMESERVER\Data Check the spelling of the name. Otherwise, there might be a problem with your network..."

My first thought is I must have the hard drive mounted  or formatted incorrectly, but I can't find anything on this forum to tell me otherwise.
I feel like I need to restart the process of this Samba set up.  Can someone please guide me through: reformatting sdb1, mounting sdb1, setting up my smb.conf, fstab, and any other config files required to use my second hard drive as a Samba share?

---

### Post by Ryan Dwyer on 2010-06-21
Please post your share definition from smb.conf. Also, browse to /media/Share locally and check that files exist there (to prove that it is mounted correctly).

---

### Post by Morbius1 on 2010-06-21
You never stated what method of Samba sharing you're using so you might want to post the output of the following commands as well:
```
net usershare info 
sudo net usershare info
```It sort of sound like a linux permissions problem and since you're mounting the second partition yourself you might want to post your fstab:
```
cat /etc/fstab
```

---

### Post by mkmcllln on 2010-06-21
> **Morbius1 said:**
> You never stated what method of Samba sharing you're using so you might want to post the output of the following commands as well:
```
net usershare info 
sudo net usershare info
```It sort of sound like a linux permissions problem and since you're mounting the second partition yourself you might want to post your fstab:
```
cat /etc/fstab
```

```
mike@HomeServer:~$ net usershare info
info_fn: file /var/lib/samba/usershares/nas1 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
mike@HomeServer:~$ sudo net usershare info
[sudo] password for mike: 
mike@HomeServer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sdb1    /media/Share    ext3    defaults    0    2
\\HOMESERVER\data  /media/Share/data  ext3  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0


```This is what i get when I follow your commands.  I'm not sure what's going on here.

BTW if it helps any, I'm using Ubuntu Desktop 10.04 LTS

---

### Post by mkmcllln on 2010-06-21
> **Morbius1 said:**
> You never stated what method of Samba sharing you're using so you might want to post the output of the following commands as well:
```
net usershare info 
sudo net usershare info
```It sort of sound like a linux permissions problem and since you're mounting the second partition yourself you might want to post your fstab:
```
cat /etc/fstab
```

My smb.conf file looks like this:
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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup
    netbios name = homeserver

# server string is the equivalent of the NT Description field
    server string = HOMESERVER

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
    wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;  interfaces = lo, eth0

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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
    security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;    encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

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
;    printing = cups
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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    guest ok = yes
;    guest account = nobody
    username map = /etc/samba/smbusers

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
    writeable = yes
    valid users = avahi, mike, nobody
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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Data]
    comment = MyShare
    path = /media/Share/data
    writeable = yes
    guest ok = yes
;    browseable = yes

[Documents]
    path = /home/mike/Documents
    writeable = yes
;    browseable = yes
    guest ok = yes
```

For some reason those comment marks are automatically added in front of browseable = yes.  I don't think that's my main issue though.

I'm willing to start from the top if someone will help me clear everything I did, and walk me through step by step.  I want to be able to share my 1.5 TB secondary hard drive (sdb1) with my Windows 7 PC. I understand Samba is the best way to share it.  I have a feeling I'm not mounting the drive correctly, but I really don't know what I'm doing wrong.

Thanks to anyone that can help.

---

### Post by Morbius1 on 2010-06-21
Yikes!

I don't know what this is but it's not going to do whatever it is you want it to do:
> \\HOMESERVER\data  /media/Share/data  ext3  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0I fairly certain that your system is just ignoring that line. You might want to comment it out by placing a # sign in front of it so it looks like this:
> #\\HOMESERVER\data  /media/Share/data  ext3  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0Save the file and run the following command just to make sure there are no errors in your fstab:
```
sudo mount -a
```Me thinks the problem is here:
> /dev/sdb1    /media/Share    ext3    defaults    0    2> [Data]
    comment = MyShare
    path = /media/Share/data
    writeable = yes
    guest ok = yes
;    browseable = yes
The fstab line is fine but by default it will mount /dev/sdb1 with owner = root and with permissions set to 0755 meaning root can read and write to that mountpoint /media/Share but everyone else can only read. Now you create a subfolder /media/Share/data and share it allowing guest access. It's permissions will also be 0755. That last "5" says that "others" which would include remote guests in this case can only read. You need to change the permissions on your shared folder:

```
sudo chmod 0777 /media/Share/data
```

If that doesn't fix it by itself post the output of this command:
```
ls -al /media/Share
```

---

### Post by mkmcllln on 2010-06-21
> **Morbius1 said:**
> Me thinks the problem is here:
The fstab line is fine but by default it will mount /dev/sdb1 with owner = root and with permissions set to 0755 meaning root can read and write to that mountpoint /media/Share but everyone else can only read. Now you create a subfolder /media/Share/data and share it allowing guest access. It's permissions will also be 0755. That last "5" says that "others" which would include remote guests in this case can only read. You need to change the permissions on your shared folder:

```
sudo chmod 0777 /media/Share/data
```If that doesn't fix it by itself post the output of this 

You are correct!
What you told me to do here was the correct answer.

For any n00b's out there that want to know how to do this the simple way in Ubuntu Desktop 10.04 here's what I ended up doing (with the amazing help from this forum!)

Once the hard drive is physically installed in your machine open System>Administration>Disk Utility

Click on the new disk (you should be able to tell which one it is based on size, or typically the second drive is named something like "/dev/sdb1"

Click Format Volume.  Give it a label and select a file type. I used type ext3 because I read somewhere that Samba wasn't ready for ext4 (not sure if that's true, just wanted to play it safe).

Now, go into your terminal and enter
```
sudo gedit /etc/fstab
```

In the editor add the line:
```
/dev/sdb1    /media/Share    ext3    defaults    0    0
```
Where "Share" is the Label I gave my volume.

Now for you windows users: you can go to places>computer; browse to your new "Share" and create a folder within "Share".  I called mine "data"

go to System>Administration>Samba
It's pretty intuitive to create your own Samba share so hit the + sign and create the share by browsing to your new "data" folder. Also give it a Share name and description. Writable and Visible should be checked.

Go to access and select "allow access to everyone" (FYI,THIS IS LIKELY THE LEAST SAFE SHARE YOU COULD CREATE, SO DON'T OPEN IT TO THE WORLD)
Hit ok and close Samba.

Almost done!
now go back to your Terminal
enter code:
```
sudo chmod 0777 /media/Share/data
sudo service smbd restart
```

Now if you know how to use Windows, go to your windows copmuter and browse your network places to find your share.  Cross your fingers that it work.

Sorry if I offended the real Linux user in my step by step directions.  I understand the importance of CLI, however, as a lifetime Windows user trying to learn Linux, I'm easing myself into the CLI.

---

### Post by wildmanne39 on 2012-07-31
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

