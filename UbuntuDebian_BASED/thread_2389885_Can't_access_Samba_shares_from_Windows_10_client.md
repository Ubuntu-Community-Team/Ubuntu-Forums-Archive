---
title: "Can't access Samba shares from Windows 10 client"
date: 2018-04-22
forum: Ubuntu/Debian BASED
---

### Post by marcerickson on 2018-04-22
I can't see the shares and can't see the server either by name or by IP address.  Error is "Windows cannot access <SERVERNAME> Error code 0x80004005 Unspecified error" or "Windows cannot access <IPADDRESS> Error code 0x80070035 The network path was not found."

OS is LinuxLite v3.8 with updates applied.  The user accounts and passwords on the Ubuntu (LinuxLite) machine and Windows machine are identical.  A Samba user account identical to the Linux user account has been created.

The Linux permissions on data, data2, and DATA3 are:  Owner - <me (me)> Access - Read & Write  Group - <me> Access - Read & Write  Others - Read & Write

Or maybe you prefer it this way:
ls -dl /media/marc/data/
drwxrwxrwx 4 marc marc 4096 Apr 21 00:34 /media/marc/data/

ls -dl /media/marc/data2/
drwxrwxrwx 9 marc marc 4096 Mar 28 06:11 /media/marc/data2/

ls -dl /media/marc/DATA3/
drwxrwxrwx 8 marc marc 4096 Apr 19 10:09 /media/marc/DATA3/


samba.conf is:

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
    unix password sync = yes
    log file = /var/log/samba/log.%m
    passdb backend = tdbsam
    writeable = yes
    netbios name = POWEREDGE1800
    server role = standalone server
    os level = 20
    max log size = 1000
    syslog = 0
    server string = %h server (Samba, Ubuntu)
    dns proxy = no
    encrypt passwords = yes
    panic action = /usr/share/samba/panic-action %d
    map to guest = bad user
    pam password change = yes
    passwd program = /usr/bin/passwd %u
    workgroup = WORKGROUP
    usershare allow guests = yes
    obey pam restrictions = yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

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

[data]
    path = /media/marc/data/
    directory mask = 0777
        create mask = 777
    writeable = yes
    browseable = yes
    guest ok = yes
    read only = no

[data2]
    path = /media/marc/data2/
        directory mask = 0777
        create mask = 777
    writeable = yes
        browseable = yes
    guest ok = yes
        read only = no

[DATA3]
    path = /media/marc/DATA3/
        directory mask = 0777
        create mask = 777
    writeable = yes
        browseable = yes
    guest ok = yes
        read only = no
```

---

### Post by marcerickson on 2018-05-08
Bumping.

---

### Post by joseortiz3 on 2018-05-14
I am also having this issue. The April 2018 Windows 10 update 1803 doesn't hurt samba functionality for *updated* computers, but for some reason my freshly-reset 1803 computer is having this problem.

I made a superuser post about the problem:
[https://superuser.com/questions/1322497/did-windows-10-april-update-break-network-discovery-name-resolution-and-samba?noredirect=1#comment1971368_1322497](https://superuser.com/questions/1322497/did-windows-10-april-update-break-network-discovery-name-resolution-and-samba?noredirect=1#comment1971368_1322497)

---

### Post by marcerickson on 2018-05-15
I believe that it isn't a problem with SMB v1.0 as I can't access the share from a Win 7 box either.  I tried configuring Samba to use SMB 2 with these instructions: [https://www.cyberciti.biz/faq/how-to-configure-samba-to-use-smbv2-and-disable-smbv1-on-linux-or-unix/](https://www.cyberciti.biz/faq/how-to-configure-samba-to-use-smbv2-and-disable-smbv1-on-linux-or-unix/)

and it didn't make a difference.  Even the Windows 2000 computer I have doesn't 'see' the shares or Linuxlite computer (I used it for faxing and rarely power it up anymore).

I had this problem earlier when the 3.x kernel was current.  Could it be a kernel problem?

---

### Post by Morbius1 on 2018-05-16
**** I downloaded LinuxLite and ran it as a Live session. It enables ufw by default which will block Samba server access. Did you allow samba through the firewall:
```
sudo ufw allow Samba
```
**** You also have a tricky situation with your shares. They are all of the form:
> [data]
    path = /media/marc/data/
    directory mask = 0777
        create mask = 777
    writeable = yes
    browseable = yes
    guest ok = yes
    read only = no
There is only one user that will be permitted to traverse the /media/marc folder to reach the /data folder and that is marc. 

[1] So you can change your share definition to not allow guest access and force all of your client users to access the share as marc with his samba password.
[2] Or you can "force" your guest client users to look like marc ( for those shares ) by changing the share definition to this:
> [data]
    path = /media/marc/data/
    directory mask = 0777
        create mask = 777
    writeable = yes
    browseable = yes
    guest ok = yes
    read only = no
    [COLOR=#0000cd]**force user = marc**[/COLOR] 
Then restart smbd.

I can from Win10 access the server by ip address ( \\192.168.1.208 ) , by it's mDNS qualified host name ( \\linuxlite.local ), and even by netbios name ( \\linuxlite ) although one usually needs to make an adjustment to the name resolve order parameter in smb.conf to make the last one work.

---

### Post by marcerickson on 2018-05-16
It was the firewall.  I wasn't aware there was one.  Now it works!  Thank you so much!

I'm the only user on the network - the Linuxlite server is my media server.  I appreciate your effort.

Thanks again!

---

### Post by hikerbk on 2019-01-14
Did you just disable firewall or add a rule?

---

### Post by marcerickson on 2019-01-14
I disabled the firewall as it's not really needed.  I'm the only user on the network and internet access is through a router and a cable modem.

---

