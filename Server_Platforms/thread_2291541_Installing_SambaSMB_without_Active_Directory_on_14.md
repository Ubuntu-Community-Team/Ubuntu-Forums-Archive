---
title: "Installing Samba/SMB without Active Directory on 14.04"
date: 2015-08-20
forum: Server Platforms
---

### Post by Marc-NJ on 2015-08-20
I can't seem to figure out how to install Samba as a standalone file server without the Active Directory integration on Ubuntu Server 14.04 LTS.

I just created a VirtualBox virtual machine, installed Ubuntu Server 14.04.3 LTS into it, and did NOT select "Samba file server" from tasksel (I only selected LAMP, OpenSSH, and Print).  After the server was fully up, I did an "apt-get install samba" and it also wanted to install the following:

```
The following NEW packages will be installed:
  attr libhdb9-heimdal libkdc2-heimdal python-dnspython samba
  samba-dsdb-modules samba-vfs-modules tdb-tools
```

Once it had installed, I restarted the VirtualBox virtual machine, and in the boot-up messages, I got the following:

```
* Starting SMB/CIFS File Server                           [OK]
...
* Starting SMB/CIFS File and Active Directory Server      [OK]
...
* Starting SMB/CIFS File and Active Directory Server      [fail]
```


So I have no idea how to get it to stop failing because it's trying to run the Active Directory server when all I want is the SMB/CIFS File Server - they seem to be tied up together and I can't figure out how to install one and not the other?

Any help??

Thanks!


P.S. The Samba user documentation ([https://wiki.samba.org/index.php/User_Documentation](https://wiki.samba.org/index.php/User_Documentation)) doesn't have any wiki pages for "Samba as a Standalone Server" - so go figure!?!?

---

### Post by bab1 on 2015-08-21
> **Marc_Bressman said:**
> I can't seem to figure out how to install Samba as a standalone file server without the Active Directory integration on Ubuntu Server 14.04 LTS.

I just created a VirtualBox virtual machine, installed Ubuntu Server 14.04.3 LTS into it, and did NOT select "Samba file server" from tasksel (I only selected LAMP, OpenSSH, and Print).  After the server was fully up, I did an "apt-get install samba" and it also wanted to install the following:

```
The following NEW packages will be installed:
  attr libhdb9-heimdal libkdc2-heimdal python-dnspython samba
  samba-dsdb-modules samba-vfs-modules tdb-tools
```

These are the correct packages for Samba and its dependencies.  They are the same packages installed on my Ubuntu 14.04 system.> 

Once it had installed, I restarted the VirtualBox virtual machine, and in the boot-up messages, I got the following:

```
* Starting SMB/CIFS File Server                           [OK]
...
* Starting SMB/CIFS File and Active Directory Server      [OK]
...
* Starting SMB/CIFS File and Active Directory Server      [fail]
```


So I have no idea how to get it to stop failing because it's trying to run the Active Directory server when all I want is the SMB/CIFS File Server - they seem to be tied up together and I can't figure out how to install one and not the other?

The install is only part of the deal.  Let's see the smb.conf file that you are using.  I assume that it is the default used at install.  At this point you should have only installed Samba and nothing else.  Post the output of this command```
cat /etc/samba/smb.conf
```
> 
P.S. The Samba user documentation ([https://wiki.samba.org/index.php/User_Documentation](https://wiki.samba.org/index.php/User_Documentation)) doesn't have any wiki pages for "Samba as a Standalone Server" - so go figure!?!?
That site is really supposed to be the user "supplied" documentation.  Maybe when we get this figured out you can add the appropriate directions.  ;-)

---

### Post by LHammonds on 2015-08-21
I have a section on my server install notes called "[Configure Ubuntu for File Sharing]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=200#p363")" which shows how I install / configure Samba.

---

### Post by Marc-NJ on 2015-08-21
Output of smb.conf as requested :)  But you are correct, I haven't edited this file at all - it is the default from having just installed Samba on a fresh Ubuntu 14.04 Virtual Machine.

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



```

---

### Post by TheFu on 2015-08-21
Well - that smb.conf doesn't have any shares configured.  You will need to add that, restart smb and nmb, then attempt to connect from a client.

[http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)
Please be very careful using "sudo gedit" - always, always, always, use **sudoedit** to edit protected files.

The **Ubuntu Server Guide** also covers Samba. Any web search will find it.

---

### Post by Marc-NJ on 2015-08-21
Yup - I haven't configured any shares, or anything yet really.  I'm just trying to figure out why installing Samba seems to have also installed the Active Directory Server component of it, and why I'm getting [fail] messages for that portion of Samba on my boot-up ?  Thanks.

---

### Post by bab1 on 2015-08-22
> **Marc_Bressman said:**
> Yup - I haven't configured any shares, or anything yet really.  I'm just trying to figure out why installing Samba seems to have also installed the Active Directory Server component of it, and why I'm getting [fail] messages for that portion of Samba on my boot-up ? 
Although the advice to configure shares will be useful in the future it's not really the question right now.  In fact there is a share configured.  It's only for a printer so it's not really useful.  See the section ```
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
```

The reason I asked to see the smb.conf file is to see what role the server was configured for.  It is configured as a standalone server which is how it should be for a file server.  It is the same as my installed and working Samba file server.  This is the relevant section```
# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   [COLOR="#FF0000"]**server role**[/COLOR] =[COLOR="#0000FF"]** standalone server**[/COLOR]
```

This is important in 2 ways.  First it is configured correctly and second it is not the default setting.  The installer purposely set it correctly. This is a good thing.  From the smb.conf man pages```

       server role (G)

           This option determines the basic operating mode of a Samba server and is one of
           the most important settings in the smb.conf file.

           SERVER ROLE = STANDALONE

           If security is also not specified, this is the default security setting in Samba.
           In standalone operation, a client must first "log-on" with a valid username and
           password (which can be mapped using the username map parameter) stored on this
           machine. Encrypted passwords (see the encrypted passwords parameter) are by
           default used in this security mode. Parameters such as user and guest only if set
           are then applied and may change the UNIX user to use on this connection, but only
           after the user has been successfully authenticated.

          ....

         SERVER ROLE = ACTIVE DIRECTORY DOMAIN CONTROLLER

           This mode of operation runs Samba as an active directory domain controller,
           providing domain logon services to Windows and Samba clients of the domain. This
           role requires special configuration, see the Samba4 HOWTO


           Default: server role = AUTO

```
It looks like your server has been configured as a standalone file server.  This is very good.  Maybe the server is functioning correctly?  Post the output of ```
tail /var/log/samba/log.smbd
```You should find something like this ```
[2015/08/21 20:51:51,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/08/21 20:51:51.202400,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option

```Post the output of this command too.  This will list the nmbd configuration.```
tail /var/log/samba/log.nmbd
```

I wonder what (if any) daemons are running.  Post the output of this```
ps -ef|grep mbd
```
If the daemons are running correctly you should get this returned```
root       663     1  0 20:51 ?        00:00:00 smbd -F
root       677   663  0 20:51 ?        00:00:00 smbd -F
root      1720     1  0 20:51 ?        00:00:00 nmbd -D

```The initial start should have 2 smbd instances and 1 nmbd instance.
The daemon named samba (/usr/sbin/samba) is what used for AD-DC and it should not be running.  You can check that with this```
pgrep -l samba
```If you get no return then the samba daemon is not running (that's a good thing).

Hopefully you will be able to tell us the daemons *smbd* and *nmbd* are running and that the *samba* daemon is not.

---

### Post by Marc-NJ on 2015-08-27
Thanks for the response, and sorry for my delayed response!

As far as the output for both log.smbd and log.nmbd - both files are completely empty right now.  Is that something concerning?

Here's the other outputs you requested:

```
root@<SERVER_NAME>:/var/log/samba# ps -ef|grep mbd
root       737     1  0 Aug19 ?        00:00:08 smbd -F
root       985   737  0 Aug19 ?        00:00:01 smbd -F
root      1069     1  0 Aug19 ?        00:00:15 nmbd -D
root     14813 14770  0 00:31 pts/1    00:00:00 grep --color=auto mbd
root@<SERVER_NAME>:/var/log/samba# pgrep -l samba
root@<SERVER_NAME>:/var/log/samba#
```

Aside from the log files being empty, everything else you stated seems to match up, but I'm still confused why I'm seeing those [fail] messages on initial boot-up?

Thanks again for your help (and anyone else's help also)!

---

### Post by bab1 on 2015-08-27
> **Marc_Bressman said:**
> Thanks for the response, and sorry for my delayed response!

As far as the output for both log.smbd and log.nmbd - both files are completely empty right now.  Is that something concerning?

Not from my point of view.  No errors is a good thing.
> 

Here's the other outputs you requested:

```
root@<SERVER_NAME>:/var/log/samba# ps -ef|grep mbd
root       737     1  0 Aug19 ?        00:00:08 smbd -F
root       985   737  0 Aug19 ?        00:00:01 smbd -F
root      1069     1  0 Aug19 ?        00:00:15 nmbd -D
root     14813 14770  0 00:31 pts/1    00:00:00 grep --color=auto mbd

```

This is correct output for a standalone Samba file server.
> 
```

root@<SERVER_NAME>:/var/log/samba# pgrep -l samba

root@<SERVER_NAME>:/var/log/samba#
```
This also shows that the Samba AD-DC is **not** running.  This is correct for your install.> 

Aside from the log files being empty, everything else you stated seems to match up, but I'm still confused why I'm seeing those [fail] messages on initial boot-up?

Thanks again for your help (and anyone else's help also)!
I see a pattern here.  "Much ado about nothing".  It looks to me like everything is working correctly.  The init scripts shut down the Samba process (the daemon named samba).  On my system I get this message in the ***dmesg***  log```

dmesg|grep samba
[    4.221217] init: samba-ad-dc main process (679) terminated with status 1

```
That is the normal condition.  What do you get from the command```
dmesg | grep samba
```

From what I can see, the messages you see at boot up are normal (but maybe ambiguous) and you can ignore them.  The system is running perfectly.  Why do the messages you see come up?  IDK.  One of life's little mysteries.  Not worth spending any more time on.

---

### Post by Marc-NJ on 2015-08-28
Bab1 - I apologize - I got my virtualbox VM fresh install of Ubuntu Server 14.04 confused with the actual physical machine I'm setting up (or trying to set up) with Ubuntu Server 14.04 (and had previously selected Samba from tasksel, but since removed it I think - more on this below).

The previous /etc/samba/smb.conf was from the virtual machine, but then the additional commands you asked me to run were accidentally from my physical machine.  Here is the correct commands output from the virtual machine:

```

root@ubuntu14043:~# tail /var/log/samba/log.smbd
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/08/28 14:56:11,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/08/28 14:56:11.536025,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/08/28 14:56:11.718827,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/08/28 14:56:11.718827,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
root@ubuntu14043:~# tail /var/log/samba/log.nmbd
[2015/08/20 22:10:30,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/08/21 13:09:56,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/08/21 13:22:36,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/08/28 14:56:11,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
root@ubuntu14043:~#
root@ubuntu14043:~# ps -ef|grep mbd
root       670     1  0 14:59 ?        00:00:00 smbd -F
root       815     1  0 14:59 ?        00:00:00 nmbd -D
root       817   670  0 14:59 ?        00:00:00 smbd -F
root      1663  1643  0 15:04 pts/0    00:00:00 grep --color=auto mbd
root@ubuntu14043:~# pgrep -l samba
root@ubuntu14043:~#

```

Aside from the outputs from /var/log/samba/log.smbd and /var/log/samba/log.nmbd (which actually ended up I think being what you thought they would be in the first place instead of entirely blank) everything else looks the same.  So I'm assuming that means that both servers are actually set up as you would have expected, right?

The output of the command you just suggested I run on the last post you made is as follows:

Virtual Machine:

```

root@ubuntu14043:~# dmesg | grep samba
[   10.879596] init: samba-ad-dc main process (809) terminated with status 1

```

Physical Machine:

```

root@<SERVER_NAME>:~# dmesg | grep samba
[    8.487927] init: samba-ad-dc main process (967) terminated with status 1

```

It looks like their both the same, right?  So I'm guessing based on what you said and what I can understand, on both machines Samba is set up as a standalone server and is not running in any way as an AD DC server, and despite those [fail] messages that appear on start-up, I can just ignore them, right?  Thanks again for all your help!

Also, just a quick follow-up on the physical machine (if you might be able to just help or confirm for me).  As mentioned previously in another thread and on here, I had selected Samba when installing Ubuntu Server 14.04 from tasksel, which I believe you stated made it install as an AD DC server.  Since then, I have done the following on the physical machine:

```

root@<SERVER_NAME>:~# apt-get purge samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-41 linux-headers-3.16.0-41-generic
  linux-headers-3.16.0-44 linux-headers-3.16.0-44-generic
  linux-headers-3.16.0-45 linux-headers-3.16.0-45-generic
  linux-image-3.16.0-30-generic linux-image-3.16.0-41-generic
  linux-image-3.16.0-44-generic linux-image-3.16.0-45-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-41-generic
  linux-image-extra-3.16.0-44-generic linux-image-extra-3.16.0-45-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  samba* winbind*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 13.3 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 234736 files and directories currently installed.)
Removing winbind (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
winbind stop/waiting
Purging configuration files for winbind (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Removing samba (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
nmbd stop/waiting
smbd stop/waiting
Purging configuration files for samba (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
root@<SERVER_NAME>:~# apt-get purge smbclient libsmbclient
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-41 linux-headers-3.16.0-41-generic
  linux-headers-3.16.0-44 linux-headers-3.16.0-44-generic
  linux-headers-3.16.0-45 linux-headers-3.16.0-45-generic
  linux-image-3.16.0-30-generic linux-image-3.16.0-41-generic
  linux-image-3.16.0-44-generic linux-image-3.16.0-45-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-41-generic
  linux-image-extra-3.16.0-44-generic linux-image-extra-3.16.0-45-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libsmbclient* smbclient*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1,212 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 234506 files and directories currently installed.)
Removing smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Removing libsmbclient:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Purging configuration files for libsmbclient:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
root@<SERVER_NAME>:~# apt-get purge samba-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-41 linux-headers-3.16.0-41-generic
  linux-headers-3.16.0-44 linux-headers-3.16.0-44-generic
  linux-headers-3.16.0-45 linux-headers-3.16.0-45-generic
  linux-image-3.16.0-30-generic linux-image-3.16.0-41-generic
  linux-image-3.16.0-44-generic linux-image-3.16.0-45-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-41-generic
  linux-image-extra-3.16.0-44-generic linux-image-extra-3.16.0-45-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  cifs-utils* libpam-smbpass* samba-common* samba-common-bin*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 2,694 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 234474 files and directories currently installed.)
Removing cifs-utils (2:6.0-1ubuntu2) ...
Purging configuration files for cifs-utils (2:6.0-1ubuntu2) ...
Removing libpam-smbpass:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Purging configuration files for libpam-smbpass:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Removing samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Removing samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Purging configuration files for samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
root@<SERVER_NAME>:~# apt-get purge system-config-samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'system-config-samba' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-41 linux-headers-3.16.0-41-generic
  linux-headers-3.16.0-44 linux-headers-3.16.0-44-generic
  linux-headers-3.16.0-45 linux-headers-3.16.0-45-generic
  linux-image-3.16.0-30-generic linux-image-3.16.0-41-generic
  linux-image-3.16.0-44-generic linux-image-3.16.0-45-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-41-generic
  linux-image-extra-3.16.0-44-generic linux-image-extra-3.16.0-45-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The above consists of basically 4 commands I ran:
apt-get purge samba
apt-get purge smbclient libsmbclient
apt-get purge samba-common
apt-get purge system-config-samba

I then attempted to reinstall:

```

root@<SERVER_NAME>:/etc/init# apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-41 linux-headers-3.16.0-41-generic
  linux-headers-3.16.0-44 linux-headers-3.16.0-44-generic
  linux-headers-3.16.0-45 linux-headers-3.16.0-45-generic
  linux-image-3.16.0-30-generic linux-image-3.16.0-41-generic
  linux-image-3.16.0-44-generic linux-image-3.16.0-45-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-41-generic
  linux-image-extra-3.16.0-44-generic linux-image-extra-3.16.0-45-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba-common samba-common-bin
Suggested packages:
  bind9 bind9utils ldb-tools ntp smbldap-tools winbind heimdal-clients
The following NEW packages will be installed:
  samba samba-common samba-common-bin
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,484 kB of archives.
After this operation, 13.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main samba-common all 2:4.1.6+dfsg-1ubuntu2.14.04.8 [157 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main samba-common-bin amd64 2:4.1.6+dfsg-1ubuntu2.14.04.8 [488 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main samba amd64 2:4.1.6+dfsg-1ubuntu2.14.04.8 [839 kB]
Fetched 1,484 kB in 0s (1,959 kB/s)
Preconfiguring packages ...
Selecting previously unselected package samba-common.
(Reading database ... 234383 files and directories currently installed.)
Preparing to unpack .../samba-common_2%3a4.1.6+dfsg-1ubuntu2.14.04.8_all.deb ...
Unpacking samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Selecting previously unselected package samba-common-bin.
Preparing to unpack .../samba-common-bin_2%3a4.1.6+dfsg-1ubuntu2.14.04.8_amd64.deb ...
Unpacking samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Selecting previously unselected package samba.
Preparing to unpack .../samba_2%3a4.1.6+dfsg-1ubuntu2.14.04.8_amd64.deb ...
Unpacking samba (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...


Creating config file /etc/samba/smb.conf with new version
Setting up samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
Setting up samba (2:4.1.6+dfsg-1ubuntu2.14.04.8) ...
smbd start/running, process 2324
nmbd start/running, process 2362
samba-ad-dc start/running, process 2399
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...

```

But as you can see, all I did was reinstall "Samba" and not any of the other items I had removed, such as: 
smbclient libsmbclient
samba-common
system-config-samba

It's possible that some of those items got reinstalled with Samba, but since they were previously installed, I'm not sure if I should reinstall them as well,and if doing so might impact my current non-AD-DC server setup that I have right now.

One other thing if it matters, here's the configuration of my /etc/init/samba-ad-dc.conf (if it matters):



```

description "SMB/CIFS File and Active Directory Server"
author      "Jelmer Vernooij <jelmer@ubuntu.com>"


start on (local-filesystems and net-device-up)
stop on runlevel [!2345]


expect fork
normal exit 0


pre-start script
        [ -r /etc/default/samba4 ] && . /etc/default/samba4
        install -o root -g root -m 755 -d /var/run/samba
        install -o root -g root -m 755 -d /var/log/samba
end script


exec samba -D

```

And I also have a /etc/init.d/samba-ad-dc file which I can post the contents of if it matters.

Thanks again!!

---

### Post by bab1 on 2015-08-28
> **Marc_Bressman said:**
> Bab1 - I apologize - I got my virtualbox VM fresh install of Ubuntu Server 14.04 confused with the actual physical machine I'm setting up (or trying to set up) with Ubuntu Server 14.04 (and had previously selected Samba from tasksel, but since removed it I think - more on this below).

I hate that when it happens to me.  I search for missing files and the realize I'm not looking at the correct machine.
> 
The previous /etc/samba/smb.conf was from the virtual machine, but then the additional commands you asked me to run were accidentally from my physical machine.  Here is the correct commands output from the virtual machine:

```

root@ubuntu14043:~# tail /var/log/samba/log.smbd
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/08/28 14:56:11,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/08/28 14:56:11.536025,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/08/28 14:56:11.718827,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/08/28 14:56:11.718827,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL

```

It helps if you separate the various commands and the output.
> 
```

root@ubuntu14043:~# tail /var/log/samba/log.nmbd
[2015/08/20 22:10:30,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/08/21 13:09:56,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/08/21 13:22:36,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/08/28 14:56:11,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013

```

```

root@ubuntu14043:~# ps -ef|grep mbd
root       670     1  0 14:59 ?        00:00:00 smbd -F
root       815     1  0 14:59 ?        00:00:00 nmbd -D
root       817   670  0 14:59 ?        00:00:00 smbd -F
root      1663  1643  0 15:04 pts/0    00:00:00 grep --color=auto mbd

``````

root@ubuntu14043:~# pgrep -l samba
root@ubuntu14043:~#

```
Aside from the outputs from /var/log/samba/log.smbd and /var/log/samba/log.nmbd (which actually ended up I think being what you thought they would be in the first place instead of entirely blank) everything else looks the same.  So I'm assuming that means that both servers are actually set up as you would have expected, right?

It all looks good to me.
> 
The output of the command you just suggested I run on the last post you made is as follows:

Virtual Machine:
Commonly referred to as the "guest" machine 
> 
```

root@ubuntu14043:~# dmesg | grep samba
[   10.879596] init: samba-ad-dc main process (809) terminated with status 1

```

Physical Machine:
In this context the machine is the host machine.  The host the real machine (running OS).  The physical machine is just the hardware.  Just so you know...  ;-)> 

```

root@<SERVER_NAME>:~# dmesg | grep samba
[    8.487927] init: samba-ad-dc main process (967) terminated with status 1

```

It looks like their both the same, right?  So I'm guessing based on what you said and what I can understand, on both machines Samba is set up as a standalone server and is not running in any way as an AD DC server, and despite those [fail] messages that appear on start-up, I can just ignore them, right?  Thanks again for all your help!

Everything looks good.> 
Also, just a quick follow-up on the physical machine 

(if you might be able to just help or confirm for me).  As mentioned previously in another thread and on here, I had selected Samba when installing Ubuntu Server 14.04 from tasksel, which I believe you stated made it install as an AD DC server.  Since then, I have done the following on the physical machine:
You mean the host machine, eh?>  

```

root@<SERVER_NAME>:~# apt-get purge samba
...

```
I then attempted to reinstall:

```

root@<SERVER_NAME>:/etc/init# apt-get install samba
...
[B][SIZE=3][COLOR="#FF0000"]The following extra packages will be installed:
  samba-common samba-common-bin[/COLOR][/SIZE]
[/B]

```
The installer is smart enough to pick up the dependencies. > 
```


[B][SIZE=3][COLOR="#0000FF"]The following NEW packages will be installed:
  samba samba-common samba-common-bin[/COLOR][/SIZE][/B]
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.

```
...and install Samba and its dependencies.> 
But as you can see, all I did was reinstall "Samba" and not any of the other items I had removed, such as: 
[COLOR="#008000"][B]smbclient 
libsmbclient[/B][/COLOR]
[COLOR="#0000FF"]system-config-samba[/COLOR]
The Samba server is not dependent on these (in green) to run.  They are for the Samba client.  The item (in blue) is a 3rd party python app.  There is no reason why you can't add them back in yourself.  > 
It's possible that some of those items got reinstalled with Samba, but since they were previously installed, I'm not sure if I should reinstall them as well,and if doing so might impact my current non-AD-DC server setup that I have right now.

It is because you have re-installed which is different from a fresh install.  In the end you just have to add the missing apps back using *sudo apt-get*
> 

Thanks again!!
It looks like everything is correct now.  I would add back the missing apps so you have all that you wanted originally.

---

### Post by Marc-NJ on 2015-08-28
Thanks so much once again for all the info and looking everything over.  Hopefully not to continue to beat a dead horse, but just a few quick follow-up questions:

1) So it appears based on the output I read over that I removed the following initially from my machine:
samba* winbind*
smbclient libsmbclient
samba-common
cifs-utils* libpam-smbpass* samba-common* samba-common-bin*

And then upon reinstalling Samba, it only installed back the following:
samba samba-common samba-common-bin

So that leaves the following still not installed:
winbind* 
smbclient libsmbclient
cifs-utils* libpam-smbpass

It appears I never had system-config-samba installed, but the rest of the items on the list were originally installed on the server (presumably from the initial OS install and tasksel) and were then uninstalled by me to attempt to fully remove Samba (in it's AD DC form) before adding it back (in it's standalone server form).  Can I safely install the items above (winbind* smbclient libsmbclient cifs-utils* libpam-smbpass)?  I don't actually know what most of them do to be honest, so am not sure if I need them or not...lol!

2) Should there be a /etc/init/samba-ad-dc.conf file and a /etc/init.d/samba-ad-dc file even if Samba isn't installed in an AD DC mode?  

Thanks again!

---

### Post by bab1 on 2015-08-28
> **Marc_Bressman said:**
> Thanks so much once again for all the info and looking everything over.  Hopefully not to continue to beat a dead horse, but just a few quick follow-up questions:

1) So it appears based on the output I read over that I removed the following initially from my machine:
samba* winbind*
smbclient libsmbclient
samba-common
cifs-utils* libpam-smbpass* samba-common* samba-common-bin*

And then upon reinstalling Samba, it only installed back the following:
samba samba-common samba-common-bin

So that leaves the following still not installed:
winbind* 
smbclient libsmbclient
cifs-utils* libpam-smbpass

You should only need these (below) for a standalone Samba file server that might also be a Samba client.```
smbclient libsmbclient
cifs-utils* libpam-smbpass
```
The windbind package is one of the problems to begin with.  It maps WINDOWS AD_DC USERS to Linux users.  Once again, you do not want that package installed.
> 
It appears I never had system-config-samba installed, but the rest of the items on the list were originally installed on the server (presumably from the initial OS install and tasksel) and were then uninstalled by me to attempt to fully remove Samba (in it's AD DC form) before adding it back (in it's standalone server form).  Can I safely install the items above (winbind* smbclient libsmbclient cifs-utils* libpam-smbpass)?  I don't actually know what most of them do to be honest, so am not sure if I need them or not...lol!
The package ***smbclient*** and its libs provide smbclient functionality to the command line.  smbclient has an FTP style command line.  

The package cifs-utils provides the ability to mount SMB/CIFS style shares (//server/share) from the command line.  T

he package libpam-smbpass provides password sync between the Linux user and the Samba user (one password).

It won't hurt to install those packages.  It might come in handy when I diagnose the next problem you have.  ;-)> 

2) Should there be a /etc/init/samba-ad-dc.conf file and a /etc/init.d/samba-ad-dc file even if Samba isn't installed in an AD DC mode?  

Yes.  If you are familiar with Windows servers you know what DC-Promo is.  The init scripts above are part of the Samba way of doing the same thing,  The should be there, even if they do nothing right now.

---

### Post by Marc-NJ on 2015-09-01
OK, so I reinstalled 

```

smbclient libsmbclient
cifs-utils* libpam-smbpass

```

Quick question about libpam-smbpass - now that I've installed it again, if I run pam-auth-update, I get a fourth option there (in addition to the previous three that were selected: Unix authentication, Register user sessions in the systemd control group hierarchy, and Inheritable Capabilities Management) that is : SMB password synchronization (and it is also selected).  I vaguely recall that having this selected caused the following error a while ago:

```

no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

```

And although that doesn't seem to be happening now, just wasn't sure if I should leave that selected or not.  Also, after installing the above (including libpam-smbpass) and then logging back in via PuTTY, I got this:

```

Added user <MY_USER_NAME>.

```

Which seems odd since I'm not sure what that means exactly?  Is it adding me to some new group??

As far as the winbind package - quick question about that.  I do see that in a 12.04 install on start-up, it says something about "starting the winbind daemon winbind" , so it appears as if winbind is installed on an Ubuntu 12.04 server running Samba - just want to double-check that I definitely SHOULD NOT install it on my new 14.04 server?

As far as my question regarding the /etc/init/samba-ad-dc.conf file and a /etc/init.d/samba-ad-dc file - I definitely understand your response - and thanks for that!

Also - thanks once again so much for sticking with me on this - I really appreciate it!  You seem very knowledgeable about Ubuntu and Samba, and if you're ever in the NYC/NJ area, let me know so I can buy you a drink to thank you for assisting me with these questions!

---

### Post by bab1 on 2015-09-01
> **Marc_Bressman said:**
> OK, so I reinstalled 

```

smbclient libsmbclient
cifs-utils* libpam-smbpass

```

Quick question about libpam-smbpass - now that I've installed it again, if I run pam-auth-update, I get a fourth option there (in addition to the previous three that were selected: Unix authentication, Register user sessions in the systemd control group hierarchy, and Inheritable Capabilities Management) that is : SMB password synchronization (and it is also selected).  I vaguely recall that having this selected caused the following error a while ago:

```

[COLOR="#FF0000"]**no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory**[/COLOR]

```

And although that doesn't seem to be happening now, just wasn't sure if I should leave that selected or not. 

The problem above (in red) was usually solved by removing and reinstalling libpam-smbpass.  Which you just did!  So of course it works now.  ;-)
> 

Also, after installing the above (including libpam-smbpass) and then logging back in via PuTTY, I got this:

```

Added user <MY_USER_NAME>.

```

Which seems odd since I'm not sure what that means exactly?  Is it adding me to some new group??

I'm not sure either.  I have never seen that.  You can check your user account with this```
getent passwd |grep <user_name>
```...or look at all users with this```
getent passwd
```To look at the user groups you can use this```
getent group
```
> 
As far as the winbind package - quick question about that.  I do see that in a 12.04 install on start-up, it says something about "starting the winbind daemon winbind" , so it appears as if winbind is installed on an Ubuntu 12.04 server running Samba - just want to double-check that I definitely SHOULD NOT install it on my new 14.04 server?

*_No winbind is needed on any Samba server_* that is used only as a file server (workgroup).  It shouldn't be used by your current 14.04 install or on the previous 12.04 install.  No winbind unless you are running either a NT Domain PDC or a Samba Active Directory Domain Controller (AD-DC).
> 
As far as my question regarding the /etc/init/samba-ad-dc.conf file and a /etc/init.d/samba-ad-dc file - I definitely understand your response - and thanks for that!

Also - thanks once again so much for sticking with me on this - I really appreciate it!  You seem very knowledgeable about Ubuntu and Samba, and if you're ever in the NYC/NJ area, let me know so I can buy you a drink to thank you for assisting me with these questions!
Just help the next guy when you feel like you understand all of this.  That's thanks enough.

[COLOR="#0000FF"]Edit:  One thing you can do is mark this thread SOLVED.  [/COLOR]

---

### Post by Marc-NJ on 2015-09-02
Will definitely mark this thread resolved right now.

I just checked what groups I'm in via Webmin, and they are:
- adm *(which is basically the wheel group, right?)*
- cdrom
- dip
- lpadmin
- plugdev
- sambashare
- sudo

No idea on some of those groups, or whether anything looks out of the ordinary, but maybe the thing I saw where it added me to a group was for the sambashare group?  Oh well, I'm not going to worry too much unless you see anything here that looks wrong?  Thanks again!

---

### Post by bab1 on 2015-09-02
> **Marc_Bressman said:**
> Will definitely mark this thread resolved right now.

I just checked what groups I'm in via Webmin, and they are:
- adm *(which is basically the wheel group, right?)*
- cdrom
- dip
- lpadmin
- plugdev
- sambashare
- sudo

No idea on some of those groups, or whether anything looks out of the ordinary, but maybe the thing I saw where it added me to a group was for the sambashare group?  Oh well, I'm not going to worry too much unless you see anything here that looks wrong?  Thanks again!
Everything looks correct.  The sambashare group is added for usershare samba users.  A usershare is defined as a Samba share that is created by a non-root user (usually via a GUI interface).  User shares are normally created in the users home directory.

There is no real wheel group in Linux.  Members of adm are allowed to view some logfiles (i.e. /var/log/syslog)```
-rw-r----- 1 syslog            adm     1.2K Sep  2 20:17 syslog
-rw-r----- 1 syslog            adm     1.3M Sep  2 20:01 syslog.1
-rw-r----- 1 syslog            adm      54K Aug 30 11:40 syslog.2.gz
-rw-r----- 1 syslog            adm      55K Aug 29 10:23 syslog.3.gz
-rw-r----- 1 syslog            adm      56K Aug 28 14:53 syslog.4.gz
-rw-r----- 1 syslog            adm     129K Aug 27 07:37 syslog.5.gz
-rw-r----- 1 syslog            adm     153K Aug 26 08:56 syslog.6.gz
-rw-r----- 1 syslog            adm      61K Aug 24 09:36 syslog.7.gz

```

The closest to the wheel group you will find with an Ubuntu distro is the sudo group.  Here is a [**description of the wheel group**]("http://unix.stackexchange.com/questions/1262/where-did-the-wheel-group-get-its-name").

---

### Post by JKyleOKC on 2016-09-01
I realize that this thread is more than a year old; I came across it when trying to find the reason for that error message about a LDAP server failing during boot, and am replying at this late date because it DID lead me to the actual cause -- which seems to me to be a bit of lazy scripting in the */etc/init.d/samba-ad-dc* file!

This file is what starts the samba servers during boot, and one of its first actions is to check the configuration files. If **not** configured to provide LDAP, it exits immediately with Error Code of 1 -- precisely as reported in the *dmesg* log, but the real-time display if enabled simply reports FAIL in bright red letters. Had the test been written to continue only if so configured, and always return 0, none of us would have gotten confused!

My own mind is a bit easier now; hope this helps anyone else who is bothered by that big red warning that scrolls by rapidly on the screen!

---

