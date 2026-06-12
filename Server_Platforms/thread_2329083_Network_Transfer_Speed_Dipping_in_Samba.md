---
title: "Network Transfer Speed Dipping in Samba?"
date: 2016-06-27
forum: Server Platforms
---

### Post by David_Goguen on 2016-06-27
Hey guys,

I have a very strange issue that I cannot seem to get resolved. I'm running an Ubuntu 16.04 LTS server with Samba version 4.3.9 installed from the repos on a gigabit LAN. On my previous server build back at my home, I don't recall having this issue at all (although maybe I did and I just don't remember).

Whenever I try to copy a file from a client to one of the Samba shares on the server, I get random "dips" in speed from my expected/usual gigabit performance. The speed will often go as low as 300 mbps for a few seconds, then come back up to full gigabit speed. It happens several times throughout a network transfer. Here is an example:

[ATTACH=CONFIG]269830[/ATTACH]

At first, I thought that it might only be a problem with Windows clients, but my test from my Mac revealed the same thing:

[ATTACH=CONFIG]269831[/ATTACH]

And the strange thing is, downloading files from the server to a client seems to go at full gigabit speed the whole time, as I expect it to with uploads (the only issue I have with downloads is that sometimes Windows clients will completely lock up during the transfer, but that's a completely different problem that I even had with my old server :P):

[ATTACH=CONFIG]269832[/ATTACH]

I am absolutely stumped by this problem. At first, I thought that the hard drive in the server might be a bottleneck, so I tried creating a share on my SSD. However, when I'd write a file to that share, the same thing happened. Then I thought that it might be a poorly crimped ethernet cable somewhere, so I replaced all of the cable runs in my apartment; the same thing happened. Then I thought it might be my motherboard's integrated network card, so I got an extremely highly rated Intel PCI-E network card; the same thing still happened. RAM and CPU usage on the server look normal from what I can tell, and my network is definitely not congested when I'm running these tests (I'm the only one on the network).

I don't think this is typical of a Samba server, but someone can correct me if I am wrong. I'm wondering if someone out there knows the solution to my problem... I'd like to get the transfers going at constant full gigabit speed if I can. Here's a copy of my Samba configuration file. Thanks in advance!

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
   workgroup = GOGUDA
   security = user


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


name resolve order = bcast lmhosts host wins


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


[Plex Media]
comment = Plex Media
path = /media/Shares/Plex
browseable = yes
read only = no
guest ok = yes


[Public Files]
comment = Public Files
path = /media/Shares/Public
browseable = yes
read only = no
guest ok = yes
create mask = 0777
directory mask = 0777


[David's Files]
comment = David's Files
path = /media/Shares/David
browseable = yes
read only = no
valid users = david





```

---

### Post by MAFoElffen on 2016-06-27
I do Samba and NFS shares on a Storage Server, as a storage pool to my Virtual Servers (Xen and KVM). I haven't grown enough to start doing pools for my vSphere Server yet. But my Servers are on their own subnet, with a router between my main net and my servers. My servers are connected to that storage pool via fiber., on it's own NID. My console has NIC's on both the main and server subnet NID's. My vnet bridged port's on my servers are teamed. I have two NIC's teamed on my server NID. My servers have 6 GB/s controllers/ 6GB/s disks.

I only say the above to give a reference. My Server Management console has teamed NIc's on the main NID and on the Server NID. So 2-to-1 and 2-to-1. So you would think the bandwidth would be fairly good. When I copy 4-6 GB iso files through SCP to one of my servers, I average about 13.4 MB/s. So Native SCP is faster than NFS. NFS is faster than SMB... but not really that noticeable. 

Mine also makes dips in the transfer/copy process, like you posted. I found out where my bottle neck was. The slow point in mine is when my console is doing a disk read. It does not have as fast of disks and controllers as my servers. But transfers to my servers is as fast as I can copy a file from one disk in that box (my console), to another disk in that same box. So I know that it is transferring as fast as it possibly can. I think the controller in it is only rated at 1.5GB/s.

But I see those same stat's and behavior, when copying large files from disk to disk, within the same box on workstations that I work on. 

My server to server rate is much faster. The bottle neck there is my 6GB/s disks. That and my service load to the rest of the network is okay.

So, your results look "normal" to me.

---

### Post by David_Goguen on 2016-06-28
> **MAFoElffen said:**
> I do Samba and NFS shares on a Storage Server, as a storage pool to my Virtual Servers (Xen and KVM). I haven't grown enough to start doing pools for my vSphere Server yet. But my Servers are on their own subnet, with a router between my main net and my servers. My servers are connected to that storage pool via fiber., on it's own NID. My console has NIC's on both the main and server subnet NID's. My vnet bridged port's on my servers are teamed. I have two NIC's teamed on my server NID. My servers have 6 GB/s controllers/ 6GB/s disks.

I only say the above to give a reference. My Server Management console has teamed NIc's on the main NID and on the Server NID. So 2-to-1 and 2-to-1. So you would think the bandwidth would be fairly good. When I copy 4-6 GB iso files through SCP to one of my servers, I average about 13.4 MB/s. So Native SCP is faster than NFS. NFS is faster than SMB... but not really that noticeable. 

Mine also makes dips in the transfer/copy process, like you posted. I found out where my bottle neck was. The slow point in mine is when my console is doing a disk read. It does not have as fast of disks and controllers as my servers. But transfers to my servers is as fast as I can copy a file from one disk in that box (my console), to another disk in that same box. So I know that it is transferring as fast as it possibly can. I think the controller in it is only rated at 1.5GB/s.

But I see those same stat's and behavior, when copying large files from disk to disk, within the same box on workstations that I work on. 

My server to server rate is much faster. The bottle neck there is my 6GB/s disks. That and my service load to the rest of the network is okay.

So, your results look "normal" to me.

Thanks for the response. The weird thing is, all clients are running SSDs as well so I don't see them being the bottleneck either. I just can't figure this out for the life of me.

---

### Post by MAFoElffen on 2016-06-28
So I guess the thing to do might be to set up a controlled test to set some baselines:
- Use one specific iso file.
- Use a script that will write a timestamp before and after a transfer/copy process... to a text file. (ie: echo date >> test.txt)

 -- copy it from one disk or from one directory to another. Record the time
 -- use scp to transfer the file to the remote server
 -- copy to the samba share
- Compare the times

---

### Post by lukeiamyourfather on 2016-06-30
This doesn't look out of the ordinary. Performance can drop for all sorts of reasons. Most likely the transfer rate is dropping because there are groups of small files which have more overhead than one large file.

---

### Post by MAFoElffen on 2016-07-03
That is how I see his spec's also. His transfer rates (and the behaviors of) are within range for what it should be. It is what I see as normal on my servers here, immaterial of the shares being nfs, smb, ZFS, ntfs... or the servers being Linux, Win, or Unix.

His own internet rates make me jealous!

The baselines I asked him for are just further that I might be able to show him a comparison of how they measure to how mine are.

---

