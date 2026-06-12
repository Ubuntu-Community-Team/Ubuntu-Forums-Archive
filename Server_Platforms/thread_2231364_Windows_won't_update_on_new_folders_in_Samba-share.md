---
title: "Windows won't update on new folders in Samba-share"
date: 2014-06-25
forum: Server Platforms
---

### Post by Henning_Herfjord on 2014-06-25
Dear community,

This is my very first post in this forum.

At home I have a machine with two NICs and a large HDD witch operates as NAT/Firewall/DHCP-server/File-server etc. Recently I have changed my configuration and re-installed the system manually based upon Ubuntu 14.04 (server) in contrast to my many year old friend ClearOS. I did this because I missed a lot of Ubuntus features and wide add-on/SW/repo support compared to CentOS.

Anyway, my system has been up running for a couple of weeks, and I'm starting to get all the fine-tuning to the different demands on track. Mostly I'm really satisfied with my new setup and the freedom within my 100% custom setup based upon Ubuntu. 

I face one issue however; I have a basic Samba setup for simple file-sharing to my Windows clients. I have two computers, my wifes and mine, and they react differently. Both Windows 7. The problem is when a folder is created within a share, I have to log out of Windows and then to log back in again to be able to access the new folder on one of the clients. This behavior is not consistent, and if I remember correctly, I once had to restart Samba to be able to see the new folder on either machine. Sometimes the folders appears as expected on both clients. I've tried to manually access the path to the new folder and neither that or F5 helps me out, I have to re-login to access the new folder.

It's worth mentioning that my user at the Ubuntu-server has sudo and ssh priveligies, but otherwice both mine and my wifes user are within the same groups. The folders affected are accessed by ACL-controlling and the native user-control does not give access. The affected folders are created by a service running as its own user.

So, as far as I understand the problem can be located to three possible causes: Access trouble, Windows problems or Samba setup.

Does anyone know what's causing this?

Thank's in advance,

BR
Henning

```

#User control
drwxrwx---+ 2 serviceuser serviceuser

#ACL
group:familygroup:rwx

```

```

# /etc/samba/smb.conf
# I've cut out some commented sections. This is basically the default file.

######################

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = FAMILY

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
   interfaces = 127.0.0.0/8 eth1

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = yes

#### Follow Symlinks ####
   unix extensions = no

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
[homes]
   comment = Home Directories
   browseable = no
   path = /home/%S/documents

[Storage]
     comment = Storage
     path = /home/storage
     browseable = yes
     read only = no
     follow symlinks = yes
     wide links = yes
```

---

### Post by Henning_Herfjord on 2014-07-03
Dear all,

I'm a bit curious why no one replied to my inquiry; did I use the wrong sub-forum?

Anyway, I think I found the problem. Windows cache related...

From another forum:
> Control Panel > Sync Center > Manage Offline Files (bottom left menu, or type it in search box)

Click Disable Offline Files

BR
Henning

---

