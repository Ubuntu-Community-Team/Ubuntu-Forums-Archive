---
title: "Outdated Samba HowTo's"
date: 2010-03-09
forum: The Cafe
---

### Post by inobe on 2010-03-09
we need a really good up to date samba howto sticky in networking forum.


samba is like a hit or miss setup scenario, not like it use to be, seems that samba has changed pretty much when 9.10 was released.


use to get 2mbits a second in 9.04, now i get 100 kbps in 9.10


besides the networking forum isn't the same either for some reason, folks in there posting ubuntu docs and such minus the howto tutorials.

---

### Post by doas777 on 2010-03-09
I havn't noticed any samba slowdowns between 904 and 910, but I have just carried over my existing smb.conf (I use samba in classic non-userspace mode exclusively). i would probably check my nic duplex settings with 'ethtool eth0'

---

### Post by BrokenKingpin on 2010-03-09
I agree. I hate setting up Samba, I always have to mess around with it for a few hours to finally get it working correctly... and the steps seem to change from release to release. It would be even more helpful if there was a really robust GUI front-end to it. All the ones I have tried never seem to work properly.

---

### Post by doas777 on 2010-03-09
> **BrokenKingpin said:**
> I agree. I hate setting up Samba, I always have to mess around with it for a few hours to finally get it working correctly... and the steps seem to change from release to release. It would be even more helpful if there was a really robust GUI front-end to it. All the ones I have tried never seem to work properly.


well part of the problem is that ubuntu is stuck between samba-classic (system space, all config in the smb.conf, no right-click sharing), and the samba-usershare paradigm. half the instructions are on how to configure a file server in classic, and half of them are for the userspace. the problem is that the userspace documentation is never deep enough, so people end up finding the solution in the old system. 

personally I have lots of non-user shares, so I use the classic, and just copy over a smb.conf template that I worked out a few years ago, and tweak it as needed.

---

### Post by juancarlospaco on 2010-03-09
Samba (SMB) is not an high performing protocol, and spamm the network with unneeded packets,
only is good if there are windows pcs on the same network.
NFS, SSH and such are great IMO

---

### Post by inobe on 2010-03-09
> **juancarlospaco said:**
> Samba (SMB) is not an high performing protocol, and spamm the network with unneeded packets,
only is good if there are windows pcs on the same network.
NFS, SSH and such are great IMO

it's a samba thread, you can start an ssh or nfs thread if you like.

---

### Post by cariboo on 2010-03-09
If you feel the community maintained howto's are not good enough, or need changing, you can change them yourself if you have a launchpad account.

---

### Post by inobe on 2010-03-09
check out the samba ubuntu docs and tell me what you think, there should be a much cleaner tutorial out there somewhere.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

in the past i did a ten step setup similar to this.

```
sudo apt-get install samba
```

setup password protection

```
sudo smbpasswd -a username
```

create the directory

```
mkdir /home/username/shares
```

backup smb.conf

```
sudo cp /etc/samba/smb.conf ~
```

edit smb

```
sudo kate /etc/samba/smb.conf
```

add the shares directory permissions and user

```
[shares]
path = /home/username/shares
available = yes
valid users = username
read only = no
browsable = yes
public = yes
writable = yes
```

restart samba

```
sudo /etc/init.d/samba restart
```

test samba

```
testparm
```

done.


this doesn't work anymore ?

---

### Post by juancarlospaco on 2010-03-09
Yep, it works.

---

### Post by inobe on 2010-03-09
i agree, it works but does it perform ?

if yes' are you running a gigabit network:D

---

### Post by CharlesA on 2010-03-09
Looks good.

> **inobe said:**
> i agree, it works but does it perform ?

if yes' are you running a gigabit network:D

Gigabit network here and it is decently fast(75-90MBps), but it's probably due to my server.

---

### Post by inobe on 2010-03-09
> **CharlesA said:**
> Looks good.



Gigabit network here and it is decently fast(75-90MBps), but it's probably due to my server.

could i see your smb.conf

please :o

---

### Post by inobe on 2010-03-10
dangit i was hoping to see that samba.conf =P~

---

### Post by tad1073 on 2010-03-10
I am getting about 1.6 mb/sec while transferring files.

---

### Post by cariboo on 2010-03-10
@inobe

What kind of transfer speeds do you get using other protocols? I have a standard 100Mbps network, and I get transfer rates of between 70Mbps - 80Mbps no matter what I use, SFTP, NFS or Samba.

This is from a server running 9.04 to my desktop system running Lucid alpha 3.

If you aren't sure if you are using all of the bandwidth available to you, give iperf a try, it is in the repositories. There is also Windows and Mac clients available. once you have iperf installed, open a terminal and type:

```
iperf -h
```

for all the command line options.

---

### Post by 3rdalbum on 2010-03-10
I'm stuck with Samba on my low-bandwidth network (wireless G) because I have one dual-boot Windows machine, and I don't think my media boxes can access NFS.

For my small network with only two shares and no particular access controls, I just use system-config-samba to write the configuration files and add users. Most people who need a HOWTO would probably be perfectly happy with this.

---

### Post by Morbius1 on 2010-03-10
inobe,

Here's the problem with all these Samba HowTo's. You need to always preface the HowTo with a description of what method of samba file sharing you're using. This relates back to doas777's comments. In your example it's Classic-shares.

One could also write a comparable HowTo using Nautilus-share that would look like this:

mkdir /home/username/shares
Open Nautilus 
Right click on /home/username/shares
Select "Sharing Options"
Mark all three boxes
Select "Create Share"

If samba is not installed the act of trying to use right click in Nautilus will prompt the user to install it.

There are things that Nautilus-share cannot do that Classic-share can. For example there is no "valid users" option on a per share basis in Nautilus-share. 

BTW, in looking at your example I don't believe it will work as you expect:

> [shares]
path = /home/username/shares
available = yes
[COLOR=Blue] valid users = username[/COLOR]
read only = no
browsable = yes
[COLOR=Blue] public = yes[/COLOR]
[COLOR=Green]writable = yes[/COLOR](1) You're creating a public share but you list only one valid user. Is this a public or a private share? (edited, worded original incorrectly )

(2) You created the "shares" directory in your home folder and you're allowing guest access. But the "shares" directory has by default permissions set to 0755 when you create it. That means that others ( or guests in this case ) will only have read access. Your how to should add a **chmod 0777 /home/username/shares **at the end**. **BTW Nautilus-share would make the permissions modification automatically when you select "Create share".
[COLOR=Blue][B]
EDIT:[/B][/COLOR] I just realized in your description that you used kate as your editor. KDE doesn't have anything like Nautilus-share ( to my knowledge ) so my point about method type makes no sense in this context. Sorry for not being observant enough to catch that.

---

### Post by CharlesA on 2010-03-10
> **inobe said:**
> could i see your smb.conf

please :o

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
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = 
	unix password sync = yes
	workgroup = ASGARD
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




[CBackup]
	comment = Charles' Backup Folder
	invalid users = clone,htpc,karen
	create mode = 660
	path = /array/cbackup
	write list = charles
	directory mode = 770

[Charles]
        comment = Chares' Folder
        invalid users = clone,htpc,karen
        create mode = 660
        path = /array/charles
        write list = charles
        directory mode = 770

[Clone]
        comment = Clonezilla Folder
        invalid users = htpc,karen
        create mode = 660
        path = /array/clone
        write list = clone,charles
        directory mode = 770

[DVDs]
        read list = htpc
        invalid users = clone
        path = /array/dvds
        write list = charles
        comment = DVD Folder
        create mode = 664
        directory mode = 775

[ISOs]
        invalid users = clone,htpc
        path = /array/isos
        write list = charles
        comment = ISO Folder
        create mode = 664
        directory mode = 775

[Music]
        read list = htpc
        invalid users = clone
        path = /array/music
        write list = charles
        comment = Music Folder
        create mode = 664
        directory mode = 775

[Service Packs]
        invalid users = clone,htpc
        path = /array/servicepacks
        write list = charles
        comment = Service Packs Folder
        create mode = 664
        directory mode = 775

[Shared]
        comment = Shared Folder
        create mode = 664
        invalid users = clone
        path = /array/shared
        write list = charles,htpc
        directory mode = 775


[TestOut]
        invalid users = clone,htpc
        path = /array/testout
        write list = charles
        comment = TestOut Folder
        create mode = 664
        directory mode = 775

[WinStuff]
	comment = Windows Stuff
	invalid users = clone,htpc
	create mode = 660
	path = /array/winstuff
	write list = charles
	directory mode = 770

```

Nothing real specific in it tbh, I think it's mostly my server, since it's reading/writing on a RAID of 3 disks.

> **cariboo907 said:**
> 
If you aren't sure if you are using all of the bandwidth available to you, give iperf a try, it is in the repositories. There is also Windows and Mac clients available. once you have iperf installed, open a terminal and type:

```
iperf -h
```

for all the command line options.

Good advice there.

@OP: When I first set Samba up, I used Webmin to do most of the configuration. Far easier to do that then try to edit it manually (but then again, I am lazy >.>)

---

