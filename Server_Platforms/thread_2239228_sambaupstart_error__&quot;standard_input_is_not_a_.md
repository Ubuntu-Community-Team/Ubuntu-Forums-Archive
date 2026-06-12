---
title: "samba/upstart error:  &quot;standard input is not a socket, assuming -D option&quot;"
date: 2014-08-12
forum: Server Platforms
---

### Post by silentcreek on 2014-08-12
Hi,

I'm running Ubuntu Server 14.04.1 with samba as a standalone fileserver. The shares work absoluetly fine, but I'm seeing some errors in my logs that I don't know how to get rid of.

Every time I boot up my machine, I see **this error** in my logs:
```
[2014/08/12 22:03:53.590428,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
```

EDIT: I understand now that this is because smbd ist executed by upstart with the -F option rather than -D. But why does the upstart smbd.conf call smbd -F rather than -D? Especially considering that smbd is assuming -D anyway. Do other users of Ubuntu Server see the same error in their logs?

There are more messages in the logs, but these have *lower priorities than "error"*:
```
[2014/08/12 22:03:53.314399,  0] ../source4/smbd/server.c:370(binary_smbd_main)
  samba version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/08/12 22:03:53.356620,  0] ../source3/winbindd/winbindd_cache.c:3196(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 2
[2014/08/12 22:03:53.423242,  0] ../source4/smbd/server.c:478(binary_smbd_main)
  At this time the 'samba' binary should only be used for either:
  'server role = active directory domain controller' or to access the ntvfs file server with 'server services = +smb' or the rpc proxy with 'dcerpc endpo$
  You should start smbd/nmbd/winbindd instead for domain member and standalone file server tasks
[2014/08/12 22:03:53.590428,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
```

 I don't see the reason for the message regarding the server role. Upstart executes smbd rather than samba. So what's the problem here? 

I selected samba during the initial installation of Ubuntu Server. Then I only changed the smb.conf, created a user for samba, but didn't touch the start up scripts (smbd.conf for upstart). As I said, everything is working fine. It's just the (error) messages that I would like to avoid.

My smb.conf looks like this:
```
[global]
workgroup = WORKGROUP
server string = SERVER
security = user
load printers = no
printing = bsd
printcap name = /dev/null
disable spoolss = yes
log file = /var/log/samba/samba.log
max log size = 100
dns proxy = no
disable netbios = yes
hosts deny = 0.0.0.0/0
hosts allow = 192.168.0.
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072 SO_SNDBUF=131072
smb ports = 445
[SHARED]
path = /media/storage/shared/
read only = no
public = no
writeable = yes
valid users = usr-share
```

I'd appreciate any help. If you need more details, please let me know.

Thanks and kind regards,

Timo

---

### Post by silentcreek on 2014-08-16
Ok, I narrowed down the problem by checking the upstart configuration file for smbd. It seems the error is related to the way smbd is called by upstart. Why is this happening? Anyone elese sees these messages in their logs?

Thanks,

Timo

---

### Post by bab1 on 2014-08-18
> **silentcreek said:**
> Ok, I narrowed down the problem by checking the upstart configuration file for smbd. It seems the error is related to the way smbd is called by upstart. Why is this happening? Anyone elese sees these messages in their logs?

Thanks,

Timo
In Ubuntu (and I assume Debian) the default startup of the Samba daemon is with the -F switch.  This causes the smbd daemon create new instances via a fork from the main daemon rather than creating new Samba daemons as what would happen with the -D switch.  For most workgroup instances the -f switch is more useful than the -D switch.  The smbd -D option is a much heavier load on the CPU than the smbd -F option.

None of this addresses your problem of the lack of internal communications (e.g. standard input is not a socket).  My assumption is this is a standalone server (workgroup) and somewhere you have misconfigured the smb.conf file.   I have my suspicions, but it is easier to just start over. With a default installation with no modifications at all, samba should work correctly.  My suggestion is to replace the modified smb.conf file with the original default copy and restart the samba daemon.  Then check for errors.  If that works you can add the shares.  If you have problems ask here BEFORE you alter the smb.conf parameters.

---

### Post by silentcreek on 2014-08-20
> **bab1 said:**
>  My assumption is this is a standalone server (workgroup) and somewhere you have misconfigured the smb.conf file.   I have my suspicions, but it is easier to just start over. With a default installation with no modifications at all, samba should work correctly.
Thanks, bab1. I replaced my smb.conf with the original one from /usr/share/samba/smb.conf. First, I thought the problem disappeared, but that was only because I was looking in the wrong place**. With the original smb.conf **(nothing touched, not even my shares defined) in place, **the message** "standard input is not a socket"** still shows up** - but only [B]in /var/log/samba/log.smbd
[/B]
I noticed one more thing, though. Ubuntu's original smb.conf sets syslog = 0  (meaning log only messages with priority ERR or higher to syslog, according to man smb.conf) and my own config didn't. With this option set, the message does not show up in the syslog logs. If I comment this out, or set syslog = 1 (i.e. log WARN or higher), then it shows up in syslog. So, samba seems to treat this message as a warning rather than an error. This is interesting because, I have a log file for all syslog messages with priority error or higher and even though samba sees this message as a warning, rsyslog treats it as an error. But anyway, so if I set syslog = 0, I can avoid the message to be passed to syslog, but it's still in log.smbd (with Ubuntu's original smb.conf in place).

Can anyone else using samba as a standalone server confirm this (i.e. that the message "standard input is not a socket" shows up in log.smbd)? I might set up a virtual machine with a clean installation of Ubuntu Server 14.04.1 to tackle this further down but I won't have much time for testing, since I will be travelling for a couple of days.

Regards,

Timo

---

### Post by silentcreek on 2014-08-20
**Ok, this is definitely a Ubuntu issue.** I just set up Ubuntu Server 14.04.1 on a virtual machine. When the installation process asked which services/tasks it should set up, I checked Samba file server. After the installation was finished, I logged into the clean system and checked /var/log/samba/log.smbd

It shows (sorry for posting this as a screenshot):
[IMG]http://oi61.tinypic.com/1z4cqcx.jpg[/IMG]

So, this issue is not related to my smb.conf or my server setup at all. The messages about the printers disappear if you set your smb.conf accordingly. But the issue "standard input is not a socket, assuming -D option" stays.

Cheers,

Timo

---

### Post by bab1 on 2014-08-20
> **silentcreek said:**
> **Ok, this is definitely a Ubuntu issue.** I just set up Ubuntu Server 14.04.1 on a virtual machine. When the installation process asked which services/tasks it should set up, I checked Samba file server. After the installation was finished, I logged into the clean system and checked /var/log/samba/log.smbd

It shows (sorry for posting this as a screenshot):
[IMG]http://oi61.tinypic.com/1z4cqcx.jpg[/IMG]

So, this issue is not related to my smb.conf or my server setup at all. The messages about the printers disappear if you set your smb.conf accordingly. But the issue "standard input is not a socket, assuming -D option" stays.

Cheers,

Timo
All I can say is this is NOT the normal Samba reaction to a default install.  I have to think you have changed or installed something to cause this problem.  I've installed or helped others install Samba on Ubuntu hundreds of times and specifically Samba 4.1 on Ubuntu 14.04 dozens of times.  It always works fine.  The package is stable for Ubuntu in that regard.

What Samba packages have you installed specifically?  What is the specific environment?  Have you made any networking files changes? By default Samba listens on all interfaces so this problem should not occur by default.  Have you changed the /etc/nsswitch.conf file settings?  

Post the output of these commands```

cat /etc/nsswitch.conf

cat /etc/samba/smb.conf

cat /etc/hosts

cat /etc/hostname

testparm -s

```

---

### Post by silentcreek on 2014-08-21
> **bab1 said:**
> All I can say is this is NOT the normal Samba reaction to a default install.  I have to think you have changed or installed something to cause this problem. [...]

What Samba packages have you installed specifically?  What is the specific environment?  Have you made any networking files changes? By default Samba listens on all interfaces so this problem should not occur by default.  Have you changed the /etc/nsswitch.conf file settings?
Maybe I wasn't clear enough. But the screenshot is from a default Ubuntu Server 14.04.1 64bit installation that I did yesterday to confirm this. **So this is the default behaviour! I made no changes to any file after the installation.**

Here's the description of what I did:
1) Download the latest Ubuntu Server 14.04.1 LTS 64bit installation image from Ubuntu.com
2) Install in in a Virtual Box environment (default settings, Windows 7 64bit host)
3) During installation I only select my keyboard layout (German) and then confirmed the defaults the installer proposed (like timezone, partitioning, etc)
4) I did not set up any disk encryption during installation
5) After the installer copied most of the files, it asked which services should be installed (I mean [this dialogue]("http://landoflinux.com/images/ubuntu_server_1204_29.png")): I checked OpenSSH and Samba file server (the same selection as on my production server).
6) After the instalaltion completed, I logged into the clean system and looked at /var/log/samba/log.smbd
7) I did not install any additional packages. I did not alter any configuration files!


Even though I don't see the point of posting all this since I didn't make any changes, here's the output for the files and commands you asked for.

/etc/nsswitch.conf
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

/etc/samba/smb.conf
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

/etc/hosts
```
127.0.0.1    localhost
127.0.1.1    test

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

/etc/hostname
```
test
```

testparm -s
```
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```

---

### Post by silentcreek on 2014-08-21
Oh, and one more remark:

> **bab1 said:**
> I've installed or helped others install Samba [...] on Ubuntu 14.04 dozens of times.  It always works fine.  The package is stable for Ubuntu in that regard.

I don't have any issues with stability. It works absolutely fine for me. Samba does what's it's supposed to do. But the message is there and I'm wondering why and how to resolve this. It might be a "cosmetical" issue only, since it I don't see any restrictions in functionality.
 And just a sidenote: Even though I already pointed out that my smb.conf was not the problem, I had my configuration in place for years now, without any issues. First on Debian Squeeze, then on Ubuntu. Before installing Ubuntu 14.04, I used 13.10. In 13.10 I didn't see this error message, that's why it caught my attention now in 14.04.

But back to the topic: *Is it possible that I'm seeing this issue because of packages or configurations I did NOT install or alter? *For example, I assume a lot of people not only use Samba but also Cups to have their server work as a print server. Would it be possible that if I install samba but not cups (just an example, I have no indication that this would be the case) I see such an error while the majority doesn't?

Cheers,

Timo

---

### Post by bab1 on 2014-08-21
> **silentcreek said:**
> ...

Here's the description of what I did:
...
5) After the installer copied most of the files, it asked which services should be installed (I mean this dialogue): I checked OpenSSH and Samba file server (the same selection as on my production server).

At this point you stop having a default standalone (workgroup) environment.  I believe the install you have done is in preparation for having a Samba Domain Controller and Samba server v4.1.

I reread most of the errors you sent and I see things like this ```
[2014/08/12 22:03:53.356620,  0] ../source3/winbindd/winbindd_cache.c:3196(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 2

```
Winbind is not needed for a workgroup Samba server (file sharing only).  It can cause problems.

> 
I don't have any issues with stability. It works absolutely fine for me. Samba does what's it's supposed to do. 
The stability I was referring to was that the package has not needed much updating over the years.> 
But the message is there and I'm wondering why and how to resolve this. It might be a "cosmetical" issue only, since it I don't see any restrictions in functionality.
t is just a warning and if it works for you then great!> 
 And just a sidenote: Even though I already pointed out that my smb.conf was not the problem, I had my configuration in place for years now, without any issues. First on Debian Squeeze, then on Ubuntu. Before installing Ubuntu 14.04, I used 13.10. In 13.10 I didn't see this error message, that's why it caught my attention now in 14.04.
Always in a VM?  No infrastructure changes?> 

But back to the topic: *Is it possible that I'm seeing this issue because of packages or configurations I did NOT install or alter? *For example, I assume a lot of people not only use Samba but also Cups to have their server work as a print server. Would it be possible that if I install samba but not cups (just an example, I have no indication that this would be the case) I see such an error while the majority doesn't?

Cheers,

Timo
You install the Samba packages differently from how I do.  I install the bare Ubuntu server and then use APT to install the package *samba*.  This installs the Samba client and the Samba standalone server.  No AD DC, no Winbind or LDAP or Kerbros, etc.  FYI: The samba package on Ubuntu before 14.04 installed Samba3.  On Ubuntu 14.04 and on that Samba package installs Samba4.  Both have the same smbd daemon. 

Since this is a VM only I would try reinstalling the Ubuntu server but** do not add any services**.  Then add Samba and SSH by doing this```
sudo apt-get install samba ssh
```. That will install Samba and SSH client and server.  Then check for errors and let me know how it works.

---

### Post by silentcreek on 2014-08-21
Thanks again, bab1.

I will try another clean installation and install samba manually afterwards to see if this solves it. However, I have to postpone any further testing until next week as I'm traveling now.

About the VM environment: No, my actual production server is not virtualized. The installation in a VM was for testing purposes only to see if a new installation behaves differently. It was just easier to do this in a VM quickly without touching a psychical machine.

If you're assumption about tasksel is right, though, it might be less ambiguous if this was indicated in future versions (i.e. that this is meant for domain controller setups rather than a standalone server). Especially since the default smb.conf sets the server role to standalone server and the comments say that this would be the most likely setup.

I'll see next week.

Regards,
Timo

---

### Post by bab1 on 2014-08-21
> **silentcreek said:**
> Thanks again, bab1.

I will try another clean installation and install samba manually afterwards to see if this solves it. However, I have to postpone any further testing until next week as I'm traveling now.

About the VM environment: No, my actual production server is not virtualized. The installation in a VM was for testing purposes only to see if a new installation behaves differently. It was just easier to do this in a VM quickly without touching a psychical machine.

If you're assumption about tasksel is right, though, it might be less ambiguous if this was indicated in future versions (i.e. that this is meant for domain controller setups rather than a standalone server). Especially since the default smb.conf sets the server role to standalone server and the comments say that this would be the most likely setup.

I'll see next week.

Regards,
Timo
If I remember correctly this is why I never use tasksel.  It is arbitrary in what and how it installs server services.  I use APT via apt-get for greater control over what is installed and how it is configured by default.

[COLOR="#0000FF"]Edit:  One last test that you can perform both before and after you reinstall Samba.  Post the outputs of this [/COLOR]```

ps -ef |grep mbd|grep -v color
```... this should show you how the smbd and nmbd daemons are really running.  I get this```
root      1794     1  0 18:02 ?        00:00:00 nmbd -D
root      2951     1  0 19:59 ?        00:00:00 smbd -F
root      2953  2951  0 19:59 ?        00:00:00 smbd -F

```
I don't think you will have any luck getting the tasksel developers to change the way the descriptions are.  The installer is pretty complicated as it is.  If you want to try you need to start the conversation by filing a bug report.  You can start [here]("https://launchpad.net/ubuntu/+source/tasksel").  To my way of thinking It's just one of those gotcha's that you have to learn by experience.

Good luck.  Let us know what happens.

---

### Post by silentcreek on 2014-08-24
Ok, I got back home tonight and was eager to do that tests as discussed. I found out something disappointing and something interesting.

The disappointing part: I did a new clean install of Ubuntu Server 14.04.1 64bit in a VM as described above BUT this time I did not use tasksel to install any server services. After the installation finished, I logged into the new system, installed samby with 'sudo apt-get install samba', rebooted the machine and used 'cat /var/log/samba/log.smbd' to check the logs. Result: The error persisits. So the way tasksel configures samba is not the problem.

But here's the interesting part: As suggested, I used
```
ps -ef |grep mbd|grep -v color
```
to check how the services are started. And the services seems to be started correct. On both, the clean installation with only samba installed on top, as well as on my (physical) production server, the output of the above command shows that smbd is started as 'smbd -F' and nmbd with the -D option (nmbd only on the clean installation because my own smb.conf - see initial post - disables nmbd).

Now, I don't understand. Does the output is ps -ef only show the comand used to start the service but smbd operates unter the -D option anyway (according to the error message 'assuming -D option') or does ps -ef show how smbd is really running?

I'm a little lost now as to how to proceed...

Regards,

Timo

---

### Post by bab1 on 2014-08-25
> **silentcreek said:**
> Ok, I got back home tonight and was eager to do that tests as discussed. I found out something disappointing and something interesting.

The disappointing part: I did a new clean install of Ubuntu Server 14.04.1 64bit in a VM as described above BUT this time I did not use tasksel to install any server services. After the installation finished, I logged into the new system, installed samby with 'sudo apt-get install samba', rebooted the machine and used 'cat /var/log/samba/log.smbd' to check the logs. Result: The error persisits. So the way tasksel configures samba is not the problem.

You are too quick to find fault instead of asking why that is.  All I can tell you is:  The ***initial*** boot should not show the error regarding starting with smbd -D any restarts will show that error.  The error is really the fact that the error message itself is shown inappropriatly.  If I restart smbd I get the same error too.  It's no big deal.  I just edit the smb.cof file to show "syslog = 0"   > 

But here's the interesting part: As suggested, I used
```
ps -ef |grep mbd|grep -v color
```
to check how the services are started. And the services seems to be started correct. On both, the clean installation with only samba installed on top, as well as on my (physical) production server, the output of the above command shows that smbd is started as 'smbd -F' and nmbd with the -D option (nmbd only on the clean installation because my own smb.conf - see initial post - disables nmbd).

What you don't get is any nagging winbindd errors.  Samba is running fne.
> 
Now, I don't understand. Does the output is ps -ef only show the comand used to start the service but smbd operates unter the -D option anyway (according to the error message 'assuming -D option') or does ps -ef show how smbd is really running?

The command *ps* lists the _running_ processes.  The smbd daemon is not started with -D even if the error message says so by default.  :-)  Read the ps man pages.
> 

I'm a little lost now as to how to proceed...

Regards,

Timo
Turn off the error messages to syslog and use the server as it is.  I wanted you to be rid of Winbind and not see any error on initial boot.  We have done that.  Find something else to worry about.

---

### Post by silentcreek on 2014-08-25
> **bab1 said:**
> You are too quick to find fault instead of asking why that is.
In my last post I did not draw any conclusion where to find fault. I have no idea where the problem is and why the message occurs, as I said. I just said that my test showed that whether I use tasksel or not did not make a difference regarding to the "assuming -D option" message.
  > **bab1 said:**
> All I can tell you is:  The ***initial*** boot should not show the error regarding starting with smbd -D any restarts will show that error.
I'm not quite sure what you mean by *initial*. If you mean a clean server installation without any additional server services installed, then, yes. Of course, at that point, samba is not installed, so there can't be an error message. But as soon as you install the samba package via apt-get and apt starts the smbd/nmbd services, you can see the message in the log (I restarted the system after the installation to confirm, but it's the same).

> **bab1 said:**
> The error is really the fact that the error message itself is shown inappropriatly.  If I restart smbd I get the same error too.  It's no big deal.  I just edit the smb.cof file to show "syslog = 0"
Well, this is the first time you actuall say you get the same error. That changes everything. You said before that the message should not be there at all on a clean server installation with samba installed and no misconfiguration. Setting syslog to zero just means, the message is not passed to syslog, but it's still in the log.smbd which is written by samba itself (at least with the default smb.conf).

Now, if you say the message itself is no big deal, then this is a totally different thing. If I knew from the beginning that this message is normal and nothing to worry about, I wouldn't have done all that testing.
> **bab1 said:**
>  What you don't get is any nagging winbindd errors.
Ok, I forgot that part. That's true. If I install samba via apt-get rather than tasksel, apt-get shows that winbind is not installed. So this solves the winbindd issue and that message doesn't show up. But this was never my main concern anyway because, as opposed to the other message, this was never reported to syslog as an error. So, if this is resolved before I really worried about it, good.

> **bab1 said:**
> The command *ps* lists the _running_ processes.  The smbd daemon is not started with -D even if the error message says so by default.  :-)
Allright. So, to wrap it up:
1) The message "assuming -D option" is common, but incorrect. Samba is running fine and this can be safely ignored.
2) For standalone servers, it's better to install samba manually via apt rather than using the tasksel option during the installation process.
*Edit:* 3) Users who dont need the AD DC functionality, may want to disable the automatic start of samba-ad-dc so that they can avoid the message about the samba binary being used with an inappropriate wrong server role (see below).

Regards,

Timo

*Edit:* I found the source and solution to the last message in the logs that I mentioned initially but that we didn't further discuss or tackle down:
```
[2014/08/12 22:03:53.423242,  0] ../source4/smbd/server.c:478(binary_smbd_main)   At this time the 'samba' binary should only be used for either:   'server role = active directory domain controller' or to access the ntvfs file server with 'server services = +smb' or the rpc proxy with 'dcerpc endpo$   You should start smbd/nmbd/winbindd instead for domain member and standalone file server tasks
```
In a default samba installation (meaning clean Ubuntu Server installation with Samba installed via apt-get and no changes made to the default smb.conf) this message can be found in /var/log/samba/log.%m
The reason for this is the upstart job samba-ad-dc. It is set up along with the smbd and nmbd upstart jobs when you install samba and is executed by default during boot. If you set the samba-ad-dc.conf in /etc/init/ to manual or rename/delete it, the system will not try to start samba as an AD DC and you won't see that message anymore.

---

### Post by Bu83KQdr on 2014-12-16
> **silentcreek said:**
> The reason for this is the upstart job samba-ad-dc. It is set up along with the smbd and nmbd upstart jobs when you install samba and is executed by default during boot. If you set the samba-ad-dc.conf in /etc/init/ to manual or rename/delete it, the system will not try to start samba as an AD DC and you won't see that message anymore.This was useful. Thanks!

---

### Post by SeijiSensei on 2015-05-07
Thanks from me, too.  This is one of the few useful pieces on the "samba binary" error message in 14.04.

I renamed the file to samba-ad-dc.conf.disabled in case I want to play with having Samba run as an AD.  The file /etc/init/smbd.conf starts Samba with the "-F" option as expected.

---

