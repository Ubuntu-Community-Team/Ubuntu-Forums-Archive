---
title: "ProFTPd does not log anything!"
date: 2010-06-06
forum: Server Platforms
---

### Post by samandiriel on 2010-06-06
I've gotten proftpd up and running on a fresh lucid 10.04 with little effort, but CANNOT get it to  write to log files.  I uninstalled it and installed vsftp, but had exactly the same issue.  I've diddled it both by hand and with webmin with no luck at all.  Can anyone shed some light on this for me?  Here's the relevant info:

I read the guidelines at [http://www.proftpd.org/docs/howto/Logging.html](http://www.proftpd.org/docs/howto/Logging.html), and permissions all seem to be in order:
drwxrw----  2 root root 4096 2010-06-06 13:55 .
drwxr-xr-x 19 root root 4096 2010-06-06 11:57 ..
-rw-rw----  1 root root    0 2010-06-05 17:39 controls.log
-rw-rw----  1 root root    0 2010-06-05 17:38 proftpd.log
-rw-rw----  1 root root    0 2010-06-06 09:22 proftpd.xfers.log



And "proftpd -td5" shows nothing amiss either:
Checking syntax of configuration file
 - using TCP receive buffer size of 87380 bytes
 - using TCP send buffer size of 16384 bytes
asphodel.malthusian.it -
asphodel.malthusian.it - Config for malthusian.it:
asphodel.malthusian.it - Limit
asphodel.malthusian.it -  DenyAll
asphodel.malthusian.it - DefaultServer
asphodel.malthusian.it - ServerIdent
asphodel.malthusian.it - PassivePorts
asphodel.malthusian.it - TimesGMT
asphodel.malthusian.it - MaxLoginAttempts
asphodel.malthusian.it - RootLogin
asphodel.malthusian.it - TimeoutLogin
asphodel.malthusian.it - TimeoutNoTransfer
asphodel.malthusian.it - TimeoutIdle
asphodel.malthusian.it - DisplayLogin
asphodel.malthusian.it - DisplayChdir
asphodel.malthusian.it - UserID
asphodel.malthusian.it - UserName
asphodel.malthusian.it - GroupID
asphodel.malthusian.it - GroupName
asphodel.malthusian.it - Umask
asphodel.malthusian.it - DirFakeUser
asphodel.malthusian.it - DirFakeGroup
asphodel.malthusian.it - DefaultTransferMode
asphodel.malthusian.it - AllowForeignAddress
asphodel.malthusian.it - AllowRetrieveRestart
asphodel.malthusian.it - AllowStoreRestart
asphodel.malthusian.it - DeleteAbortedStores
asphodel.malthusian.it - TransferRate
asphodel.malthusian.it - TransferRate
asphodel.malthusian.it - TransferRate
asphodel.malthusian.it - TransferRate
asphodel.malthusian.it - IdentLookups
asphodel.malthusian.it - IdentLookups
asphodel.malthusian.it - TransferLog
asphodel.malthusian.it - ExtendedLog
asphodel.malthusian.it - RequireValidShell
asphodel.malthusian.it - TransferLog
asphodel.malthusian.it - ExtendedLog
asphodel.malthusian.it - AllowRetrieveRestart
asphodel.malthusian.it - AllowStoreRestart
asphodel.malthusian.it - DefaultTransferMode
asphodel.malthusian.it - DeferWelcome
asphodel.malthusian.it - IdentLookups
asphodel.malthusian.it - IdentLookups
asphodel.malthusian.it - DeleteAbortedStores
asphodel.malthusian.it - RootLogin
asphodel.malthusian.it - RequireValidShell
asphodel.malthusian.it - mod_lang/0.9: using en_CA.UTF-8 messages
asphodel.malthusian.it - mod_lang/0.9: binding to text domain 'proftpd' using locale path '/usr/share/locale'
asphodel.malthusian.it - mod_lang/0.9: using locale files in '/usr/share/locale'
Syntax check complete.
asphodel.malthusian.it - mod_ban/0.5.3: error detaching shm: Invalid argument
asphodel.malthusian.it - mod_ban/0.5.3: error removing shmid -1: Invalid argument




The config file:
ModulePath /usr/lib/proftpd
LoadModule mod_ctrls_admin.c
#LoadModule mod_tls.c
LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
LoadModule mod_dynmasq.c
LoadModule mod_ifsession.c

# Server Details
ServerType standalone
DefaultServer on
ServerName "malthusian.it"
ServerIdent on "malthusian.it"
ServerAdmin [email]noone@nowhere.com[/email]

# Default settings
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off

MaxInstances 5
MaxLoginAttempts 5
RootLogin on
TimeoutLogin 60
TimeoutNoTransfer 7200
TimeoutIdle 7200
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
Umask 022
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250

# Logging
IdentLookups	on
UseReverseDNS	on
#LogFormat	clf_default "%a - - %t "GET %f FTP/Client" 200 %b"
LogFormat	clf_default "%t %h %u GET %f 200 %b"
SystemLog	/var/log/secure
TransferLog	/var/log/proftpd/proftpd.xfers.log
ExtendedLog	/var/log/proftpd/proftpd.log ALL clf_default

RequireValidShell off

<Limit LOGIN>
	DenyALL
</Limit>

<Global>
	TransferLog		/var/log/proftpd/proftpd.xfers.log
	ExtendedLog		/var/log/proftpd/proftpd.log ALL clf_default
	
	AllowRetrieveRestart	on
	AllowStoreRestart	on
	DefaultTransferMode	binary
	DeferWelcome		off
	IdentLookups		on
	DeleteAbortedStores	on
	RootLogin		on
	RequireValidShell	off
</Global>

---

