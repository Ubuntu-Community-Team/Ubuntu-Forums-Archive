---
title: "Samba and WinBind errors preventing package installs"
date: 2017-03-08
forum: Server Platforms
---

### Post by dd-custom-mods on 2017-03-08
Hi Ubuntu experts and enthusiasts!

So I've been trying to get a webserver set up and also need to get Samba share to be working. Below is what happens when I try to install any software that touches those two packages. Any ideas other than a clean install to fix this? I've tried to force uninstall and reinstall both samba and winbind.  Samba acts like it works but winbind just gives the same error.

[IMG]http://www.overclock.net/image/id/12907147/width/400/flags/LL[/IMG]

---

### Post by howefield on 2017-03-08
What version of Ubuntu are you using and please copy/paste the text output into your post enclosed within [noparse]```

```[/noparse] tags. I'd doubt that anyone will be able to read your image.

---

### Post by QIII on 2017-03-08
Hello!

Your image may be hard to read.

If you are using ssh to get to the machine, would you please copy & paste the text back here between code tags?

To use code tags:

1.  Click the # button in the toolbar above the text entry box, place your cursor between the code tags that appear and paste or type your text.

2.  Paste or type your text, highlight it and then click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by dd-custom-mods on 2017-03-08
> **howefield said:**
> What version of Ubuntu are you using and please copy/paste the text output into your post enclosed within [noparse]```

```[/noparse] tags. I'd doubt that anyone will be able to read your image.

> **QIII said:**
> Hello!

Your image may be hard to read.

If you are using ssh to get to the machine, would you please copy & paste the text back here between code tags?

To use code tags:

1.  Click the # button in the toolbar above the text entry box, place your cursor between the code tags that appear and paste or type your text.

2.  Paste or type your text, highlight it and then click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Thank you for the heads up of the image... the original on the other site is bigger.  I am using SSH(Putty) so I will copy the output and post it when I get a baby free moment tonight.  Also suggested was a uname -a command to give the details of the server.

Here's some specs and use of the server now:

[COLOR=#272A34][FONT=&quot]This is a local server that's run out of my basement on my main rig hand me downs.  I run two 24/7 Minecraft servers, for me and the kids, and PLEX server which streams to multiple devices.
It's updated to the last stable release 16.04
Winbind is being used in conjecture with Samba through my Webmin admin portal. 
[/FONT][/COLOR]
[COLOR=#272A34][FONT=&quot] [/FONT][/COLOR]
[COLOR=#272A34][FONT=&quot]Server Specs:[/FONT][/COLOR]
[COLOR=#272A34][FONT=&quot]CPU: 3.0Ghz Phenom II X4 945[/FONT][/COLOR]
[COLOR=#272A34][FONT=&quot]Motherboard:  Asus M5A88-V EVO [/FONT][/COLOR]
[COLOR=#272A34][FONT=&quot]RAM: ADATA 6GB [/FONT][/COLOR]
[COLOR=#272A34][FONT=&quot]Hard Drives: 4x1TB in RAID 6, 320GB for OS/Swap[/FONT][/COLOR]
[COLOR=#272A34][FONT=&quot]Cooling: Xigmatek Loki[/FONT][/COLOR]
[COLOR=#272A34][FONT=&quot]NIC: Intel based dual NIC[/FONT][/COLOR]

---

### Post by dd-custom-mods on 2017-03-10
Here are some outputs and the config file for Samba.  I hope this helps.

```
root@CIASERV:/home/agent007# uname -a
Linux CIASERV 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_6                   4 x86_64 x86_64 GNU/Linux
[1]+  Stopped                 service smbd status
```

```
Setting up winbind (2:4.4.5+dfsg-2ubuntu5.2) ...
Job for winbind.service failed because the control process exited with error code.
See "systemctl status winbind.service" and "journalctl -xe" for details.
invoke-rc.d: initscript winbind, action "start" failed.
â winbind.service - Samba Winbind Daemon
   Loaded: loaded (/lib/systemd/system/winbind.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2017-03-10 13:54:14 EST; 8ms ago
     Docs: man:winbindd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 13514 ExecStart=/usr/sbin/winbindd $WINBINDOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 13514 (code=exited, status=1/FAILURE)
 
Mar 10 13:54:14 CIASERV systemd[1]: Starting Samba Winbind Daemon...
Mar 10 13:54:14 CIASERV systemd[1]: winbind.service: Main process exited, code=exited, statu...LURE
Mar 10 13:54:14 CIASERV systemd[1]: Failed to start Samba Winbind Daemon.
Mar 10 13:54:14 CIASERV systemd[1]: winbind.service: Unit entered failed state.
Mar 10 13:54:14 CIASERV systemd[1]: winbind.service: Failed with result 'exit-code'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up samba (2:4.4.5+dfsg-2ubuntu5.2) ...
Failed to preset unit: Unit file /etc/systemd/system/samba-ad-dc.service is masked.
/usr/bin/deb-systemd-helper: error: systemctl preset failed on samba-ad-dc.service: No such file or directory
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "start" failed.
â smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2017-03-10 13:54:16 EST; 9ms ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 13620 ExecStart=/usr/sbin/smbd $SMBDOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 13620 (code=exited, status=1/FAILURE)
 
Mar 10 13:54:15 CIASERV systemd[1]: Starting Samba SMB Daemon...
Mar 10 13:54:16 CIASERV systemd[1]: smbd.service: Main process exited, code=exited, status=1...LURE
Mar 10 13:54:16 CIASERV systemd[1]: Failed to start Samba SMB Daemon.
Mar 10 13:54:16 CIASERV systemd[1]: smbd.service: Unit entered failed state.
Mar 10 13:54:16 CIASERV systemd[1]: smbd.service: Failed with result 'exit-code'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.24-3ubuntu1) ...
Errors were encountered while processing:
 winbind
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


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
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    obey pam restrictions = yes
    dns proxy = no
    default = DATA
    unix password sync = yes
    max log size = 1000
    log file = /var/log/samba/log.%m
    winbind trusted domains only = no
    server string = Home Server (Samba, PLEX, SSH, Minecraft)
    panic action = /usr/share/samba/panic-action %d
    passwd program = /usr/bin/passwd %u
    os level = 20
    passdb backend = tdbsam
    security = share
    usershare allow guests = yes
    writeable = yes
    public = yes
    winbind use default domain = yes
    guest account = agent007
    map to guest = bad user
    pam password change = yes
    workgroup = WORKGROUP
    syslog = 0
    encrypt passwords = yes
    netbios name = CIASERV
    server role = standalone server


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of


# server string is the equivalent of the NT Description field


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.


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


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.


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










________smb.conf ends_______
________smb.log begins______
________smb.log ends_______
________smb.status begins______



```

---

### Post by Morbius1 on 2017-03-10
I can only comment on one parameter in your smb.conf:
> security = share
Back in the olden days samba would look at that and ignore it essentially reverting it to "security = user" which is the default.

But in the latest version of samba they decided to get medieval about the whole thing and will actually stop the smbd service from running. My suggestion is to go into smb.conf and just comment-out the line.

---

### Post by dd-custom-mods on 2017-03-10
> **Morbius1 said:**
> I can only comment on one parameter in your smb.conf:

Back in the olden days samba would look at that and ignore it essentially reverting it to "security = user" which is the default.

But in the latest version of samba they decided to get medieval about the whole thing and will actually stop the smbd service from running. My suggestion is to go into smb.conf and just comment-out the line.
 
I commented that line out.  I tried to start the Samba service and got an error.  This is the output of systemctl status smbd.service

```
root@CIASERV:/etc/samba# systemctl status smbd.service
â smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2017-03-10 20:42:55 EST; 18s ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 12525 ExecStart=/usr/sbin/smbd $SMBDOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 12525 (code=exited, status=1/FAILURE)


Mar 10 20:42:55 CIASERV systemd[1]: Starting Samba SMB Daemon...
Mar 10 20:42:55 CIASERV systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILUR
Mar 10 20:42:55 CIASERV systemd[1]: Failed to start Samba SMB Daemon.
Mar 10 20:42:55 CIASERV systemd[1]: smbd.service: Unit entered failed state.
Mar 10 20:42:55 CIASERV systemd[1]: smbd.service: Failed with result 'exit-code'.

```

---

