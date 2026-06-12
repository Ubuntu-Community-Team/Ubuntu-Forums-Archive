---
title: "Samba - Missing file sharing tab in Windows XP SP2"
date: 2007-12-02
forum: Server Platforms
---

### Post by fromoven on 2007-12-02
Hi there,

I'm running Samba on 6,06 as a PDC with roaming profile and everything seems fine except a few minor anoying glitches:

I have a problem with regular users (non admins) trying to share files or folders from a Win XP client: the "file sharing and security" is unavailable.  One user (the domain admin) has that capability because I've granted him all the Se"CrappyRights"Privilege.  I did the SeDiskOperatorPrivilege to the regular user and it still doesn't work.

On the Linux box, the ownership and group are listed to that regular user but when I access the security tab on XP, the privileges liste are not checked.  The user can check all the boxes but when saved, it defaults back to all unchecked.

I've skimmed through my book "Using Samba 3d edition", the official HOW-TO and I can't find how to correct theses glitches.

The next step might be to start pulling my hairs one by one...

So now, I'm requesting your professional help.

Thanks

SMB.CONF:

#====================== Global Settings =======================
[global]

#### core networking options ####
netbios name		= SERVER
workgroup           = HOMEDOMAIN
encrypt passwords   = true
wins support		= yes
name resolve order	= wins lmhosts hosts bcast
security			= user
preferred master	= yes
domain master		= yes
local master		= yes
domain logons		= yes
os level			= 100
passdb backend		= tdbsam:/var/lib/samba/passdb.tdb
passwd chat			= "*Enter\snew\sUNIX\spassword:* %n\n" "*Retype\snew\sUNIX\spassword:* %n\n" *password\supdated\ssuccessfully* .
logon home			= \\server\%U
logon path			= \\server\%U\profile
logon drive			= U:
logon script		= logonscript.bat


#### User and Machine opertations####
enable privileges			= yes
add user script 			= /usr/sbin/useradd -m %u
delete user script 			= /usr/sbin/userdel -r %u
add group script 			= /usr/sbin/groupadd %g
add user to group script 	= /usr/sbin/usermod -G %g %u
delete group script 		= /usr/sbin/groupdel %g
add machine script 			= /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u


#### Logging ####
log file	 = /var/log/samba/%m.log
log level	 = 3


#### Misc settings ####
socket options		= TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
follow symlinks		= yes


#======================= Share Definitions =======================


[netlogon]
comment			= Net Logon Service
path			= /raid/netlogon
read only		= yes
write list		= papa,mike,+administrator


[profile]
comment			= User Roaming Profiles
path			= /raid/profile
browseable		= no
read only		= no
inherit permissions	= yes


[bill]
writeable		= yes
browseable		= yes
guest ok		= no
dos filemode 	= yes
path			= /raid/bill
admin users		= bill
valid users		= bill,+ntadmins,+admin
invalid users	= antoine
write list		= bill,+ntadmins,+admin


[commun]
writeable		= yes
browseable		= yes
guest ok		= no
dos filemode	= yes
path			= /raid/commun
admin users		= bill,antoine
valid users		= bill,antoine,+ntadmins,+admin,+users
write list		= bill,antoine,+ntadmins,+admin,+users

[antoine]
writeable		= yes
browseable		= yes
guest ok		= no
dos filemode	= yes
path			= /raid/antoine
admin users		= bill,antoine
valid users		= bill,antoine,+ntadmins,+admin,+users
write list		= bill,antoine,+ntadmins,+admin,+users

---

