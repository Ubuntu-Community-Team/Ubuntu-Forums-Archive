---
title: "Samba server connection timout after not using for a while."
date: 2015-07-04
forum: Server Platforms
---

### Post by Higgins909 on 2015-07-04
My samba server seems to have stopped working or something?
I see a smbd and a few winbindd and a nmbd process but cant connect at all by file explorer on windows from 2 of my computers.
It just times out. (used to work fine)

I just allowed port 21 thinking it might be the cause but it wasn't.

I think what might have broken it was a update/upgrade (sudo apt-get update/upgrade)
I've noticed it been broken for maybe a week now.

I've got tons of files queuing up over that time and need to be transported to my file server.

Thanks,
Higgins909

---

### Post by Higgins909 on 2015-07-04
I've bring some updated news.  It is still not working. I have also discovered that ntop website thing is not working too, but my apache2 server seems to work still.

I tried to update my server to the fullest even sudo apt-get dist-upgrade even tho its still the same version of ubuntu server.
I tried to remove samba then restart then install.
Webmin still has the config tho even after reinstalling samba.
Webmin can't seem to restart or stop samba or winsomething... that one isnt there anymore.
I found out a bit about smbtree... that is empty with or without sudo.

here is my config.
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
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supd$

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
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba $

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


[Langweiler Share]
        force group = root
        create mode = 775
        force user = admin-ben
        write list = admin-ben,@root
        writeable = yes
        path = /
        directory mode = 775

[Langweiler2]
        path = /media






```
For some reason my shares are really far away, like a page away in my ssh.
I havent messed with the config file since I setup the server earlyer this year.  I used webmin to config it too as its a bit more layed out for me lol.

---

### Post by volkswagner on 2015-07-05
Webmin is not supported. I suggest a clean install and avoid webmin.

It will be easier for folks here to help, without webmin in the mix.

---

### Post by Higgins909 on 2015-07-06
I'm starting to give up. I tried to reinstall it a few more times and removed my config and had to find something like smbd-common to replace it.
Im starting to look at just going to 15.04.

```

admin-ben@Langweiler:~$ sudo service samba status
[sudo] password for admin-ben:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Failed to open /var/lib/samba/private/secrets.tdb
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_new_rid: failed to open /var/lib/samba/private/passdb.tdb!
 * nmbd is not running
 * smbd is not running

```

---

### Post by bab1 on 2015-07-06
> **Higgins909 said:**
> I'm starting to give up. I tried to reinstall it a few more times and removed my config and had to find something like smbd-common to replace it.
Im starting to look at just going to 15.04.

```

admin-ben@Langweiler:~$ sudo service samba status
[sudo] password for admin-ben:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Failed to open /var/lib/samba/private/secrets.tdb
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_new_rid: failed to open /var/lib/samba/private/passdb.tdb!
 * nmbd is not running
 * smbd is not running

```

Not sure what you did,  but the error is usually due to the user installing Samba via tasksel.  This is not really the best idea because the installer assumes you are going to be installing Samba as a Domain Controller (DC).  In that configuration you can't use Samba as a standalone file server.

Samba is the same in 14.04 , 14.10 and 15.04.  FYI the file server service is smbd not samba.  The samba service is for the DC,

So the first question is: How did you install Samba.

---

### Post by Higgins909 on 2015-07-06
apt-get 

It's the only installer I ever use.
could be wrong, but isn't it short or something like that, for tasksel?

---

### Post by bab1 on 2015-07-06
> **Higgins909 said:**
> apt-get 

Its it only installer I ever use.
could be wrong, but isnt it sort or something like that for tasksel?

What packages did you install?

Tasksel is an installer for Ubuntu server edition.  It is not an apt package manager as are: aptitude, apt-get, synaptic or USC.

Post the output of ```
dpkg -l samba*
```

---

### Post by Higgins909 on 2015-07-06
```

admin-ben@Langweiler:~$ dpkg -l samba*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  samba          2:4.1.6+dfsg amd64        SMB/CIFS file, print, and login s
un  samba-ad-dc    <none>       <none>       (no description available)
un  samba-client   <none>       <none>       (no description available)
ii  samba-common   2:4.1.6+dfsg all          common files used by both the Sam
ii  samba-common-b 2:4.1.6+dfsg amd64        Samba common files used by both t
ii  samba-doc      2:4.1.6+dfsg all          Samba documentation
ii  samba-dsdb-mod 2:4.1.6+dfsg amd64        Samba Directory Services Database
ii  samba-libs:amd 2:4.1.6+dfsg amd64        Samba core libraries
un  samba-tools    <none>       <none>       (no description available)
ii  samba-vfs-modu 2:4.1.6+dfsg amd64        Samba Virtual FileSystem plugins
un  samba4         <none>       <none>       (no description available)
un  samba4-clients <none>       <none>       (no description available)
un  samba4-common  <none>       <none>       (no description available)
un  samba4-common- <none>       <none>       (no description available)
admin-ben@Langweiler:~$

```

samba
maybe smbfs but I think it said something like it didn't exist anymore
I think samba-common not that sure, issues finding it in my history and researching.


I was using sudo apt-get remove --purge  samba to remove.

I was also getting all those errors when checking the service status of ntop too, I ended up fixing that by allowing the port through ufw.

---

### Post by bab1 on 2015-07-06
What do you get with this```
dpkg -l winbind
```

Winbind is not needed with a standalone Samba server but it can cause problems if installed.

Also post the output of this ```
pgrep -l mbd
```

---

### Post by Higgins909 on 2015-07-06
```

admin-ben@Langweiler:~$ dpkg -l winbind
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                    Version                  Architecture             Description
+++-=======================================-========================-========================-===================================================================================
un  winbind                                 <none>                   <none>                   (no description available)
admin-ben@Langweiler:~$

```

pgrep -l mbd has no output.

---

### Post by bab1 on 2015-07-06
> **Higgins909 said:**
> ...

pgrep -l mbd has no output.

That means the smbd and nmbd processes are not running.  Those 2 are the file sharing daemons.

Before you start these 2 daemons.  Let's do one thing more.  Post the output of this```
pgrep -l samba
```...that is the DC daemon.  If it is running then you will have problems with the smbd and nmbd daemons.

---

### Post by SeijiSensei on 2015-07-06
If you do intend to upgrade, use 14.04 with long-term support.  Production servers should always be running an LTS version of Ubuntu.

---

