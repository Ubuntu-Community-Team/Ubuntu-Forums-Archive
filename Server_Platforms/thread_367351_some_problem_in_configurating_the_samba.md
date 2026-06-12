---
title: "some problem in configurating the samba"
date: 2007-02-22
forum: Server Platforms
---

### Post by tommychw on 2007-02-22
i have some problem in configurating the samba
it says i(windows) don't have permission
my windows workgroup=WORKGROUP
windows user=admin
linux user=tommychw
windows ip=192.168.0.100
linux ip=192.168.0.101

if there is sth wrong in the file , plz help me to correct
thz

Samba config file
# 
# Sample configuration file for the Samba suite for Debian GNU/Linux. 
# 
# 
# This is the main Samba configuration file. You should read the 
# smb.conf(5) manual page in order to understand the options listed 
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example 
# 
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a # 
# for commentary and a ; for parts of the config file that you 
# may wish to enable 
# 
# NOTE: Whenever you modify this file you should run the command 
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# 

#======================= Global Settings ======================= 

[global] 
log file = /var/log/samba/log.%m 
load printers = yes 
printer = hp_par_HP_LaserJet_6P 
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* . 
socket options = TCP_NODELAY 
obey pam restrictions = yes 
null passwords = yes 
username map = /etc/samba/user.map 
passwd program = /usr/bin/passwd %u 
passdb backend = tdbsam 
dns proxy = no 
printing = cups 
server string = tommychw-server (Samba, Ubuntu) 
invalid users = root 
unix password sync = yes 
remote announce = 192.168.0.100/WORKGROUP 
workgroup = WORKGROUP 
os level = 20 
auto services = global printers print$ Web Home Files Rails 
printcap name = /etc/printcap 
security = user 
syslog = 0 
panic action = /usr/share/samba/panic-action %d 
max log size = 1000 

## Browsing/Identification ### 

# Change this to the workgroup/NT-domain name your Samba server will part of 

# server string is the equivalent of the NT Description field 

# Windows Internet Name Serving Support Section: 
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server 
; wins support = no 

# WINS Server - Tells the NMBD components of Samba to be a WINS Client 
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both 
; wins server = w.x.y.z 

# This will prevent nmbd to search for NetBIOS names through DNS. 

# What naming service and in what order should we use to resolve host names 
# to IP addresses 
; name resolve order = lmhosts host wins bcast 

#### Networking #### 

# The specific set of interfaces / networks to bind to 
# This can be either the interface name or an IP address/netmask; 
# interface names are normally preferred 
; interfaces = 127.0.0.0/8 eth0 

# Only bind to the named interfaces and/or networks; you must use the 
# 'interfaces' option above to use this. 
# It is recommended that you enable this feature if your Samba machine is 
# not protected by a firewall or is a firewall itself. However, this 
# option cannot handle dynamic or non-broadcast interfaces correctly. 
; bind interfaces only = true 



#### Debugging/Accounting #### 

# This tells Samba to use a separate log file for each machine 
# that connects 

# Put a capping on the size of the log files (in Kb). 

# If you want Samba to only log through syslog then set the following 
# parameter to 'yes'. 
; syslog only = no 

# We want Samba to log a minimum amount of information to syslog. Everything 
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log 
# through syslog you should set the following parameter to something higher. 

# Do something sensible when Samba crashes: mail the admin a backtrace 


####### Authentication ####### 

# "security = user" is always a good idea. This will require a Unix account 
# in this server for every user accessing the server. See 
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html 
# in the samba-doc package for details. 
; security = user 
# You may wish to use password encryption. See the section on 
# 'encrypt passwords' in the smb.conf(5) manpage before enabling. 

# If you are using encrypted passwords, Samba will need to know what 
# password database type you are using. 


; guest account = nobody 

# This boolean parameter controls whether Samba attempts to sync the Unix 
# password with the SMB password when the encrypted SMB password in the 
# passdb is changed. 
; unix password sync = no 

# For Unix password sync to work on a Debian GNU/Linux system, the following 
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for 
# sending the correct chat script for the passwd program in Debian Sarge). 

# This boolean controls whether PAM will be used for password changes 
# when requested by an SMB client instead of the program listed in 
# 'passwd program'. The default is 'no'. 
; pam password change = no 

########## Domains ########### 

# Is this machine able to authenticate users. Both PDC and BDC 
# must have this setting enabled. If you are the BDC you must 
# change the 'domain master' setting to no 
# 
; domain logons = yes 
# 
# The following setting only takes effect if 'domain logons' is set 
# It specifies the location of the user's profile directory 
# from the client point of view) 
# The following required a [profiles] share to be setup on the 
# samba server (see below) 
; logon path = \\%N\profiles\%U 
# Another common choice is storing the profile in the user's home directory 
; logon path = \\%N\%U\profile 

# The following setting only takes effect if 'domain logons' is set 
# It specifies the location of a user's home directory (from the client 
# point of view) 
; logon drive = H: 
; logon home = \\%N\%U 

# The following setting only takes effect if 'domain logons' is set 
# It specifies the script to run during logon. The script must be stored 
# in the [netlogon] share 
# NOTE: Must be store in 'DOS' file format convention 
; logon script = logon.cmd 

# This allows Unix users to be created on the domain controller via the SAMR 
# RPC pipe. The example command creates a user account with a disabled Unix 
# password; please adapt to your needs 
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u 

########## Printing ########## 

# If you want to automatically load your printer list rather 
# than setting them up individually then you'll need this 
; load printers = yes 

# lpr(ng) printing. You may wish to override the location of the 
# printcap file 
; printing = bsd 
; printcap name = /etc/printcap 

# CUPS printing. See also the cupsaddsmb( manpage in the 
# cupsys-client package. 
; printing = cups 
; printcap name = cups 

# When using [print$], root is implicitly a 'printer admin', but you can 
# also give this right to other users to add drivers and set printer 
# properties 
; printer admin = @lpadmin 


############ Misc ############ 

# Using the following line enables you to customise your configuration 
# on a per machine basis. The %m gets replaced with the netbios name 
# of the machine that is connecting 
; include = /home/samba/etc/smb.conf.%m 

# Most people will find that this option gives better performance. 
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html 
# for details 
# You may want to add the following on a Linux system: 
# SO_RCVBUF=8192 SO_SNDBUF=8192 

# The following parameter is useful only if you have the linpopup package 
# installed. The samba maintainer and the linpopup maintainer are 
# working to ease installation and configuration of linpopup and samba. 
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' & 

# Domain Master specifies Samba to be the Domain Master Browser. If this 
# machine will be configured as a BDC (a secondary logon server), you 
# must set this to 'no'; otherwise, the default behavior is recommended. 
; domain master = auto 

# Some defaults for winbind (make sure you're not using the ranges 
# for something else.) 
; idmap uid = 10000-20000 
; idmap gid = 10000-20000 
; template shell = /bin/bash 

#======================= Share Definitions ======================= 

# Un-comment the following (and tweak the other settings below to suit) 
# to enable the default home directory shares. This will share each 
# user's home directory as \\server\username 
;[homes] 
; comment = Home Directories 
; browseable = no 

# By default, \\server\username shares can be connected to by anyone 
# with access to the samba server. Un-comment the following parameter 
# to make sure that only "username" can connect to \\server\username 
; valid users = %S 

# By default, the home directories are exported read-only. Change next 
# parameter to 'yes' if you want to be able to write to them. 
; writable = no 

# File creation mask is set to 0600 for security reasons. If you want to 
# create files with group=rw permissions, set next parameter to 0664. 
; create mask = 0600 

# Directory creation mask is set to 0700 for security reasons. If you want to 
# create dirs. with group=rw permissions, set next parameter to 0775. 
; directory mask = 0700 

# Un-comment the following and create the netlogon directory for Domain Logons 
# (you need to configure Samba to act as a domain controller too.) 
;[netlogon] 
; comment = Network Logon Service 
; path = /home/samba/netlogon 
; guest ok = yes 
; writable = no 
; share modes = no 

# Un-comment the following and create the profiles directory to store 
# users profiles (see the "logon path" option above) 
# (you need to configure Samba to act as a domain controller too.) 
# The path below should be writable by all users so that their 
# profile directory may be created the first time they log on 
;[profiles] 
; comment = Users profiles 
; path = /home/samba/profiles 
; guest ok = no 
; browseable = no 
; create mask = 0600 
; directory mask = 0700 

[printers] 
printable = yes 
writable = no 
path = /tmp 
comment = All Printers 
public = no 
create mode = 0700 

# Windows clients look for this share name as a source of downloadable 
# printer drivers 
[print$] 
comment = Printer Drivers 
path = /var/lib/samba/printers 
browseable = yes 
read only = yes 
guest ok = no 
# Uncomment to allow remote administration of Windows print drivers. 
# Replace 'ntadmin' with the name of the group your admin users are 
# members of. 
; write list = root, @ntadmin 

# A sample share for sharing your CD-ROM with others. 
;[cdrom] 
; comment = Samba server's CD-ROM 
; writable = no 
; locking = no 
; path = /cdrom 
; public = yes 

# The next two parameters show how to auto-mount a CD-ROM when the 
# cdrom share is accesed. For this to work /etc/fstab must contain 
# an entry like this: 
# 
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0 
# 
# The CD-ROM gets unmounted automatically after the connection to the 
# 
# If you don't want to use auto-mounting/unmounting make sure the CD 
# is mounted on /cdrom 
# 
; preexec = /bin/mount /cdrom 
; postexec = /bin/umount /cdrom 

[Web] 
guest account = tommychw 
writeable = yes 
invalid users = root,@root 
write list = tommychw 
path = /var/www/ 
force group = admin 
force user = tommychw 
comment = JT Server 
valid users = tommychw,@tommychw 
create mode = 0777 
allow hosts = 192.168.0.100 

[Home] 
comment = Joshua's Home directory 
valid users = tommychw,@tommychw 
writeable = yes 
invalid users = root,@root 
path = /home/tommychw 
allow hosts = 192.168.0.100 


[Files] 
revalidate = yes 
valid users = tommychw,@tommychw 
writeable = yes 
invalid users = root,@root 
path = /var/jt27-files 
allow hosts = 192.168.0.100 


[Rails] 
writeable = yes 
valid users = tommychw,@tommychw 
invalid users = root,@root 
path = /var/jt27-rails 
allow hosts = 192.168.0.100

---

### Post by evilspoons on 2007-02-22
"Valid users" should be the Windows user attempting to access the share, not the Linux user that owns the file. I think.

You might want to try allowing access without login just to see if you can get that working (guest access), and verify the rest of your rules are working first. I had a lot of trouble getting SAMBA to work (access denied errors) until I realized that I had forgotten to chmod the folder I was sharing, so no one had access to it even outside of SAMBA (doh!).

---

### Post by IcarusR on 2007-02-22
Users trying to acess the shares need to be listed as valid users. 
> valid users = tommychw,@tommychw 
Should, I believe be ?
 > valid users = tommychw 

All my users are setup as users on server with useradd & smbpasswd.

There is a samba newsgroup which I got answers from & mailing list on samba.org.

Hope this helps.

Just found this post ["Setup Samba peer-to-peer with Windows"]("http://www.ubuntuforums.org/showthread.php?t=202605")  which might help you.

---

