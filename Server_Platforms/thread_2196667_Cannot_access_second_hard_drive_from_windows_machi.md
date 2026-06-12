---
title: "Cannot access second hard drive from windows machine"
date: 2013-12-30
forum: Server Platforms
---

### Post by stevetingate on 2013-12-30
i recently added a second hard drive to my ubuntu server, formatted it and mounted it, i then created a folder and shared it using samba, then when i try and open it on my windows machine, it sais i cant, 
here is my smb.conf 


[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# Sample configuration file for the Samba suite for Debian GNU/Linux.[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# This is the main Samba configuration file. You should read the[/COLOR]
[COLOR=#000000]# smb.conf(5) manual page in order to understand the options listed[/COLOR]
[COLOR=#000000]# here. Samba has a huge number of configurable options most of which [/COLOR]
[COLOR=#000000]# are not shown in this example[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# Some options that are often worth tuning have been included as[/COLOR]
[COLOR=#000000]# commented-out examples in this file.[/COLOR]
[COLOR=#000000]# - When such options are commented with ";", the proposed setting[/COLOR]
[COLOR=#000000]# differs from the default Samba behaviour[/COLOR]
[COLOR=#000000]# - When commented with "#", the proposed setting is the default[/COLOR]
[COLOR=#000000]# behaviour of Samba but the option is considered important[/COLOR]
[COLOR=#000000]# enough to be mentioned here[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# NOTE: Whenever you modify this file you should run the command[/COLOR]
[COLOR=#000000]# "testparm" to check that you have not made any basic syntactic [/COLOR]
[COLOR=#000000]# errors. [/COLOR]
[COLOR=#000000]# A well-established practice is to name the original file[/COLOR]
[COLOR=#000000]# "smb.conf.master" and create the "real" config file with[/COLOR]
[COLOR=#000000]# testparm -s smb.conf.master >smb.conf[/COLOR]
[COLOR=#000000]# This minimizes the size of the really used smb.conf file[/COLOR]
[COLOR=#000000]# which, according to the Samba Team, impacts performance[/COLOR]
[COLOR=#000000]# However, use this with caution if your smb.conf file contains nested[/COLOR]
[COLOR=#000000]# "include" statements. See Debian bug #483187 for a case[/COLOR]
[COLOR=#000000]# where using a master file is not a good idea.[/COLOR]
[COLOR=#000000]#[/COLOR]


[COLOR=#000000]#======================= Global Settings =======================[/COLOR]


[COLOR=#000000][global][/COLOR]


[COLOR=#000000]## Browsing/Identification ###[/COLOR]


[COLOR=#000000]# Change this to the workgroup/NT-domain name your Samba server will part of[/COLOR]
[COLOR=#000000]workgroup = WORKGROUP[/COLOR]


[COLOR=#000000]# server string is the equivalent of the NT Description field[/COLOR]
[COLOR=#000000]server string = %h server (Samba, Ubuntu)[/COLOR]


[COLOR=#000000]# Windows Internet Name Serving Support Section:[/COLOR]
[COLOR=#000000]# WINS Support - Tells the NMBD component of Samba to enable its WINS Server[/COLOR]
[COLOR=#000000]# wins support = no[/COLOR]


[COLOR=#000000]# WINS Server - Tells the NMBD components of Samba to be a WINS Client[/COLOR]
[COLOR=#000000]# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both[/COLOR]
[COLOR=#000000]; wins server = w.x.y.z[/COLOR]


[COLOR=#000000]# This will prevent nmbd to search for NetBIOS names through DNS.[/COLOR]
[COLOR=#000000]dns proxy = no[/COLOR]


[COLOR=#000000]# What naming service and in what order should we use to resolve host names[/COLOR]
[COLOR=#000000]# to IP addresses[/COLOR]
[COLOR=#000000]; name resolve order = lmhosts host wins bcast[/COLOR]


[COLOR=#000000]#### Networking ####[/COLOR]


[COLOR=#000000]# The specific set of interfaces / networks to bind to[/COLOR]
[COLOR=#000000]# This can be either the interface name or an IP address/netmask;[/COLOR]
[COLOR=#000000]# interface names are normally preferred[/COLOR]
[COLOR=#000000]; interfaces = 127.0.0.0/8 eth0[/COLOR]


[COLOR=#000000]# Only bind to the named interfaces and/or networks; you must use the[/COLOR]
[COLOR=#000000]# 'interfaces' option above to use this.[/COLOR]
[COLOR=#000000]# It is recommended that you enable this feature if your Samba machine is[/COLOR]
[COLOR=#000000]# not protected by a firewall or is a firewall itself. However, this[/COLOR]
[COLOR=#000000]# option cannot handle dynamic or non-broadcast interfaces correctly.[/COLOR]
[COLOR=#000000]; bind interfaces only = yes[/COLOR]






[COLOR=#000000]#### Debugging/Accounting ####[/COLOR]


[COLOR=#000000]# This tells Samba to use a separate log file for each machine[/COLOR]
[COLOR=#000000]# that connects[/COLOR]
[COLOR=#000000]log file = /var/log/samba/log.%m[/COLOR]


[COLOR=#000000]# Cap the size of the individual log files (in KiB).[/COLOR]
[COLOR=#000000]max log size = 1000[/COLOR]


[COLOR=#000000]# If you want Samba to only log through syslog then set the following[/COLOR]
[COLOR=#000000]# parameter to 'yes'.[/COLOR]
[COLOR=#000000]# syslog only = no[/COLOR]


[COLOR=#000000]# We want Samba to log a minimum amount of information to syslog. Everything[/COLOR]
[COLOR=#000000]# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log[/COLOR]
[COLOR=#000000]# through syslog you should set the following parameter to something higher.[/COLOR]
[COLOR=#000000]syslog = 0[/COLOR]


[COLOR=#000000]# Do something sensible when Samba crashes: mail the admin a backtrace[/COLOR]
[COLOR=#000000]panic action = /usr/share/samba/panic-action %d[/COLOR]




[COLOR=#000000]####### Authentication #######[/COLOR]


[COLOR=#000000]# "security = user" is always a good idea. This will require a Unix account[/COLOR]
[COLOR=#000000]# in this server for every user accessing the server. See[/COLOR]
[COLOR=#000000]# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html[/COLOR]
[COLOR=#000000]# in the samba-doc package for details.[/COLOR]
[COLOR=#000000]# security = user[/COLOR]


[COLOR=#000000]# You may wish to use password encryption. See the section on[/COLOR]
[COLOR=#000000]# 'encrypt passwords' in the smb.conf(5) manpage before enabling.[/COLOR]
[COLOR=#000000]encrypt passwords = true[/COLOR]


[COLOR=#000000]# If you are using encrypted passwords, Samba will need to know what[/COLOR]
[COLOR=#000000]# password database type you are using. [/COLOR]
[COLOR=#000000]passdb backend = tdbsam[/COLOR]


[COLOR=#000000]obey pam restrictions = yes[/COLOR]


[COLOR=#000000]# This boolean parameter controls whether Samba attempts to sync the Unix[/COLOR]
[COLOR=#000000]# password with the SMB password when the encrypted SMB password in the[/COLOR]
[COLOR=#000000]# passdb is changed.[/COLOR]
[COLOR=#000000]unix password sync = yes[/COLOR]


[COLOR=#000000]# For Unix password sync to work on a Debian GNU/Linux system, the following[/COLOR]
[COLOR=#000000]# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for[/COLOR]
[COLOR=#000000]# sending the correct chat script for the passwd program in Debian Sarge).[/COLOR]
[COLOR=#000000]passwd program = /usr/bin/passwd %u[/COLOR]
[COLOR=#000000]passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .[/COLOR]


[COLOR=#000000]# This boolean controls whether PAM will be used for password changes[/COLOR]
[COLOR=#000000]# when requested by an SMB client instead of the program listed in[/COLOR]
[COLOR=#000000]# 'passwd program'. The default is 'no'.[/COLOR]
[COLOR=#000000]pam password change = yes[/COLOR]


[COLOR=#000000]# This option controls how unsuccessful authentication attempts are mapped[/COLOR]
[COLOR=#000000]# to anonymous connections[/COLOR]
[COLOR=#000000]map to guest = bad user[/COLOR]


[COLOR=#000000]########## Domains ###########[/COLOR]


[COLOR=#000000]# Is this machine able to authenticate users. Both PDC and BDC[/COLOR]
[COLOR=#000000]# must have this setting enabled. If you are the BDC you must[/COLOR]
[COLOR=#000000]# change the 'domain master' setting to no[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]; domain logons = yes[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# The following setting only takes effect if 'domain logons' is set[/COLOR]
[COLOR=#000000]# It specifies the location of the user's profile directory[/COLOR]
[COLOR=#000000]# from the client point of view)[/COLOR]
[COLOR=#000000]# The following required a [profiles] share to be setup on the[/COLOR]
[COLOR=#000000]# samba server (see below)[/COLOR]
[COLOR=#000000]; logon path = \\%N\profiles\%U[/COLOR]
[COLOR=#000000]# Another common choice is storing the profile in the user's home directory[/COLOR]
[COLOR=#000000]# (this is Samba's default)[/COLOR]
[COLOR=#000000]# logon path = \\%N\%U\profile[/COLOR]


[COLOR=#000000]# The following setting only takes effect if 'domain logons' is set[/COLOR]
[COLOR=#000000]# It specifies the location of a user's home directory (from the client[/COLOR]
[COLOR=#000000]# point of view)[/COLOR]
[COLOR=#000000]; logon drive = H:[/COLOR]
[COLOR=#000000]# logon home = \\%N\%U[/COLOR]


[COLOR=#000000]# The following setting only takes effect if 'domain logons' is set[/COLOR]
[COLOR=#000000]# It specifies the script to run during logon. The script must be stored[/COLOR]
[COLOR=#000000]# in the [netlogon] share[/COLOR]
[COLOR=#000000]# NOTE: Must be store in 'DOS' file format convention[/COLOR]
[COLOR=#000000]; logon script = logon.cmd[/COLOR]


[COLOR=#000000]# This allows Unix users to be created on the domain controller via the SAMR[/COLOR]
[COLOR=#000000]# RPC pipe. The example command creates a user account with a disabled Unix[/COLOR]
[COLOR=#000000]# password; please adapt to your needs[/COLOR]
[COLOR=#000000]; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u[/COLOR]


[COLOR=#000000]# This allows machine accounts to be created on the domain controller via the [/COLOR]
[COLOR=#000000]# SAMR RPC pipe. [/COLOR]
[COLOR=#000000]# The following assumes a "machines" group exists on the system[/COLOR]
[COLOR=#000000]; add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u[/COLOR]


[COLOR=#000000]# This allows Unix groups to be created on the domain controller via the SAMR[/COLOR]
[COLOR=#000000]# RPC pipe. [/COLOR]
[COLOR=#000000]; add group script = /usr/sbin/addgroup --force-badname %g[/COLOR]


[COLOR=#000000]########## Printing ##########[/COLOR]


[COLOR=#000000]# If you want to automatically load your printer list rather[/COLOR]
[COLOR=#000000]# than setting them up individually then you'll need this[/COLOR]
[COLOR=#000000]# load printers = yes[/COLOR]


[COLOR=#000000]# lpr(ng) printing. You may wish to override the location of the[/COLOR]
[COLOR=#000000]# printcap file[/COLOR]
[COLOR=#000000]; printing = bsd[/COLOR]
[COLOR=#000000]; printcap name = /etc/printcap[/COLOR]


[COLOR=#000000]# CUPS printing. See also the cupsaddsmb(8) manpage in the[/COLOR]
[COLOR=#000000]# cupsys-client package.[/COLOR]
[COLOR=#000000]; printing = cups[/COLOR]
[COLOR=#000000]; printcap name = cups[/COLOR]


[COLOR=#000000]############ Misc ############[/COLOR]


[COLOR=#000000]# Using the following line enables you to customise your configuration[/COLOR]
[COLOR=#000000]# on a per machine basis. The %m gets replaced with the netbios name[/COLOR]
[COLOR=#000000]# of the machine that is connecting[/COLOR]
[COLOR=#000000]; include = /home/samba/etc/smb.conf.%m[/COLOR]


[COLOR=#000000]# Most people will find that this option gives better performance.[/COLOR]
[COLOR=#000000]# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html[/COLOR]
[COLOR=#000000]# for details[/COLOR]
[COLOR=#000000]# You may want to add the following on a Linux system:[/COLOR]
[COLOR=#000000]# SO_RCVBUF=8192 SO_SNDBUF=8192[/COLOR]
[COLOR=#000000]# socket options = TCP_NODELAY[/COLOR]


[COLOR=#000000]# The following parameter is useful only if you have the linpopup package[/COLOR]
[COLOR=#000000]# installed. The samba maintainer and the linpopup maintainer are[/COLOR]
[COLOR=#000000]# working to ease installation and configuration of linpopup and samba.[/COLOR]
[COLOR=#000000]; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &[/COLOR]


[COLOR=#000000]# Domain Master specifies Samba to be the Domain Master Browser. If this[/COLOR]
[COLOR=#000000]# machine will be configured as a BDC (a secondary logon server), you[/COLOR]
[COLOR=#000000]# must set this to 'no'; otherwise, the default behavior is recommended.[/COLOR]
[COLOR=#000000]# domain master = auto[/COLOR]


[COLOR=#000000]# Some defaults for winbind (make sure you're not using the ranges[/COLOR]
[COLOR=#000000]# for something else.)[/COLOR]
[COLOR=#000000]; idmap uid = 10000-20000[/COLOR]
[COLOR=#000000]; idmap gid = 10000-20000[/COLOR]
[COLOR=#000000]; template shell = /bin/bash[/COLOR]


[COLOR=#000000]# The following was the default behaviour in sarge,[/COLOR]
[COLOR=#000000]# but samba upstream reverted the default because it might induce[/COLOR]
[COLOR=#000000]# performance issues in large organizations.[/COLOR]
[COLOR=#000000]# See Debian bug #368251 for some of the consequences of *not*[/COLOR]
[COLOR=#000000]# having this setting and smb.conf(5) for details.[/COLOR]
[COLOR=#000000]; winbind enum groups = yes[/COLOR]
[COLOR=#000000]; winbind enum users = yes[/COLOR]


[COLOR=#000000]# Setup usershare options to enable non-root users to share folders[/COLOR]
[COLOR=#000000]# with the net usershare command.[/COLOR]


[COLOR=#000000]# Maximum number of usershare. 0 (default) means that usershare is disabled.[/COLOR]
[COLOR=#000000]; usershare max shares = 100[/COLOR]


[COLOR=#000000]# Allow users who've been granted usershare privileges to create[/COLOR]
[COLOR=#000000]# public shares, not just authenticated ones[/COLOR]
[COLOR=#000000]usershare allow guests = yes[/COLOR]


[COLOR=#000000]#======================= Share Definitions =======================[/COLOR]


[COLOR=#000000]# Un-comment the following (and tweak the other settings below to suit)[/COLOR]
[COLOR=#000000]# to enable the default home directory shares. This will share each [/COLOR]
[COLOR=#000000]# user's home director as \\server\username[/COLOR]
[COLOR=#000000];[homes][/COLOR]
[COLOR=#000000]; comment = Home Directories[/COLOR]
[COLOR=#000000]; browseable = no[/COLOR]


[COLOR=#000000]# By default, the home directories are exported read-only. Change the[/COLOR]
[COLOR=#000000]# next parameter to 'no' if you want to be able to write to them.[/COLOR]
[COLOR=#000000]; read only = yes[/COLOR]


[COLOR=#000000]# File creation mask is set to 0700 for security reasons. If you want to[/COLOR]
[COLOR=#000000]# create files with group=rw permissions, set next parameter to 0775.[/COLOR]
[COLOR=#000000]; create mask = 0700[/COLOR]


[COLOR=#000000]# Directory creation mask is set to 0700 for security reasons. If you want to[/COLOR]
[COLOR=#000000]# create dirs. with group=rw permissions, set next parameter to 0775.[/COLOR]
[COLOR=#000000]; directory mask = 0700[/COLOR]


[COLOR=#000000]# By default, \\server\username shares can be connected to by anyone[/COLOR]
[COLOR=#000000]# with access to the samba server. Un-comment the following parameter[/COLOR]
[COLOR=#000000]# to make sure that only "username" can connect to \\server\username[/COLOR]
[COLOR=#000000]# The following parameter makes sure that only "username" can connect[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# This might need tweaking when using external authentication schemes[/COLOR]
[COLOR=#000000]; valid users = %S[/COLOR]


[COLOR=#000000]# Un-comment the following and create the netlogon directory for Domain Logons[/COLOR]
[COLOR=#000000]# (you need to configure Samba to act as a domain controller too.)[/COLOR]
[COLOR=#000000];[netlogon][/COLOR]
[COLOR=#000000]; comment = Network Logon Service[/COLOR]
[COLOR=#000000]; path = /home/samba/netlogon[/COLOR]
[COLOR=#000000]; guest ok = yes[/COLOR]
[COLOR=#000000]; read only = yes[/COLOR]


[COLOR=#000000]# Un-comment the following and create the profiles directory to store[/COLOR]
[COLOR=#000000]# users profiles (see the "logon path" option above)[/COLOR]
[COLOR=#000000]# (you need to configure Samba to act as a domain controller too.)[/COLOR]
[COLOR=#000000]# The path below should be writable by all users so that their[/COLOR]
[COLOR=#000000]# profile directory may be created the first time they log on[/COLOR]
[COLOR=#000000];[profiles][/COLOR]
[COLOR=#000000]; comment = Users profiles[/COLOR]
[COLOR=#000000]; path = /home/samba/profiles[/COLOR]
[COLOR=#000000]; guest ok = no[/COLOR]
[COLOR=#000000]; browseable = no[/COLOR]
[COLOR=#000000]; create mask = 0600[/COLOR]
[COLOR=#000000]; directory mask = 0700[/COLOR]


[COLOR=#000000][printers][/COLOR]
[COLOR=#000000]comment = All Printers[/COLOR]
[COLOR=#000000]browseable = no[/COLOR]
[COLOR=#000000]path = /var/spool/samba[/COLOR]
[COLOR=#000000]printable = yes[/COLOR]
[COLOR=#000000]guest ok = no[/COLOR]
[COLOR=#000000]read only = yes[/COLOR]
[COLOR=#000000]create mask = 0700[/COLOR]


[COLOR=#000000]# Windows clients look for this share name as a source of downloadable[/COLOR]
[COLOR=#000000]# printer drivers[/COLOR]
[COLOR=#000000][print$][/COLOR]
[COLOR=#000000]comment = Printer Drivers[/COLOR]
[COLOR=#000000]path = /var/lib/samba/printers[/COLOR]
[COLOR=#000000]browseable = yes[/COLOR]
[COLOR=#000000]read only = yes[/COLOR]
[COLOR=#000000]guest ok = no[/COLOR]
[COLOR=#000000]# Uncomment to allow remote administration of Windows print drivers.[/COLOR]
[COLOR=#000000]# You may need to replace 'lpadmin' with the name of the group your[/COLOR]
[COLOR=#000000]# admin users are members of.[/COLOR]
[COLOR=#000000]# Please note that you also need to set appropriate Unix permissions[/COLOR]
[COLOR=#000000]# to the drivers directory for these users to have write rights in it[/COLOR]
[COLOR=#000000]; write list = root, @lpadmin[/COLOR]


[COLOR=#000000]# A sample share for sharing your CD-ROM with others.[/COLOR]
[COLOR=#000000];[cdrom][/COLOR]
[COLOR=#000000]; comment = Samba server's CD-ROM[/COLOR]
[COLOR=#000000]; read only = yes[/COLOR]
[COLOR=#000000]; locking = no[/COLOR]
[COLOR=#000000]; path = /cdrom[/COLOR]
[COLOR=#000000]; guest ok = yes[/COLOR]


[COLOR=#000000]# The next two parameters show how to auto-mount a CD-ROM when the[/COLOR]
[COLOR=#000000]#	cdrom share is accesed. For this to work /etc/fstab must contain[/COLOR]
[COLOR=#000000]#	an entry like this:[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# The CD-ROM gets unmounted automatically after the connection to the[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# If you don't want to use auto-mounting/unmounting make sure the CD[/COLOR]
[COLOR=#000000]#	is mounted on /cdrom[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]; preexec = /bin/mount /cdrom[/COLOR]
[COLOR=#000000]; postexec = /bin/umount /cdrom


i opened the log and the error i recieve is 
[/COLOR][COLOR=#000000]process_usershare_file: stat of /var/lib/samba/usershares/fileshare failed. Permission denied

somebody please help !!![/COLOR]

---

### Post by Bucky Ball on 2013-12-30
*Thread closed.*

Please do not post duplicate threads. Getting help here:

[http://ubuntuforums.org/showthread.php?t=2195387](http://ubuntuforums.org/showthread.php?t=2195387)

Also, please wait 24 hours before bumping threads.

---

