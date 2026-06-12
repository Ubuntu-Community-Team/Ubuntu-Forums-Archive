---
title: "Right mess getting server setup"
date: 2008-12-04
forum: Server Platforms
---

### Post by happyhacker on 2008-12-04
I just cannot get access to shares which appear on my XP PC. I either get the "\\server1\homes is not accessible . .. " or on another share password refusal. Following is my samba.conf, if anyone could give me a clue that would be appreciated. I am using webmin and usual advice in the posts but to no avail. It's probably some simple setting.

[COLOR="Navy"]#
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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
#

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = SO_KEEPALIVE TCP_NODELAY
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	wins support = true
	dns proxy = no
	netbios name = server1
	writeable = yes
	server string = acdor server1
	path = /homes
	unix password sync = yes
	workgroup = acdor
	os level = 65
	syslog = 0
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes

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

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

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

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
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

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin
# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
[homes]
	writeable = yes
	valid users = wayfinders,@office
	public = yes
[common]
	guest account = roger
	comment = all our common shared files
	writeable = yes
	create mode = 777
	path = /office/common[/COLOR]

---

### Post by lykwydchykyn on 2008-12-04
While I don't have an encyclopaedic knowledge of samba directives, the "path=/homes" directive under the [global] section seems a bit odd to me.  Try running the command "testparm" on your server and paste the output here.  It should alert you to problems in your configuration.

I don't think you want public=yes under your [homes] configuration, either.  not very secure, and may be possibly causing issues.

Oh, and \\server1\homes will not work.  [homes] is a special share that shares the home directories of individual users.  If you are using the [homes] share, you'd go to \\server1\username to get to a user's home directory.

---

### Post by happyhacker on 2008-12-05
Thanks, I will try testparm next time I'm in the office. I have probably misused the homes dir. I saw it listed in webmin but noticed that there was not an actual directory so I created one. Was it wrong to do so?

---

### Post by lykwydchykyn on 2008-12-05
yes.  Homes is, like i said, a special share that behaves differently from regular shares.  

I'd suggest checking out the "samba by example" guide from samba.org ([http://us3.samba.org/samba/docs/man/Samba-Guide/](http://us3.samba.org/samba/docs/man/Samba-Guide/)), it's not overly technical and gives a lot of great information (just ignore most of the install-related stuff, it's rather redhat-oriented).

---

### Post by hyper_ch on 2008-12-05
I'd cut down the complexity to a very simple smb.conf. Then checking if it works. If it does, add more complexity... until everything runs or you find out when and where you encounter problems.

---

### Post by happyhacker on 2008-12-08
Now, I've researched a basic samba.conf file based on your advice and it is shown below for comment. I hope it is self explanatory and hope to try it later this week and will replace the default Samba config file with this one. Then I will see how Webmin sees it when it boots.

The only thing I'm not sure of is do I have to create the homes directory (just the homes not those underneath like "ceo" as I know these will be created when I create the users)?

[COLOR="Blue"]# Configuration file for the ACDorchester Ubuntu Samba server acdorServer1.

# This file serves the following Linux directories:

# homes/ceo/		private directory for the executive officer's use.
# homes/info/		private directory for the office secretary's use.
# homes/wayfinders/	private directory for wayfinders.
# homes/care/		private directory for Care.
# homes/i&a/		private directory for Information and Advice.
# homes/forums/		private directory for Forums.
# homes/reception/	private directory for Reception.
# office/forms		common directory for common office files used day-to-day.
# office/common		common directory for exchanging/agreeing with anybody.

[global]
workgroup = ACDOR
netbios name = acdorserver1
encrypt passwords = yes
security = user

[homes]
comment = all users private files
#valid users = @office
browseable = no
writeable = yes
wide links = no
hide dot files = yes

[common]
comment = all our common shared files
valid users = @office
browseable = yes
writeable = yes
path = /office/common

[forms]
comment = all files useable by all but only changed by ceo or info.
valid users = @office
browseable = yes
write list = ceo, info
writeable = yes
path = /office/forms[/COLOR]

---

### Post by lykwydchykyn on 2008-12-08
No, you don't have to create anything.  It's a bit confusing because [homes] reads all the directories under "/home" -- not /homes!

---

### Post by happyhacker on 2008-12-09
Yes, thanks, I've learnt that today and that one must get the linux permissions sorted first. Am I right in thinking that whilst Samba cannot override the underlying permissions that it modifies them e.g. if the linux is 777 and Samba is 755 a user can only do 755? So does this mean that one can set a shared dir to 777 and then Samba it to 755 or anything less?

---

### Post by lykwydchykyn on 2008-12-09
Interestingly, this is one of the same little issues that trips people up on Windows as well.  Local file permissions apply as well as share permissions, and the most restrictive permissions wins out.

You can set file create and directory create masks in your config that determine the default *local* permissions of newly created files and directories.  That deals with local permissions.

Samba permissions would not look like 755 or 775; if you see that kind of notation it's dealing with local permissions.  Essentially, you can define which users can access the share, and whether they access it read only or read/write.

For instance, in your original smb.conf, you had "create mode=777".  This means that if anyone creates a file (including pasting a file) in this share, it's *local* permissions will be 777.  Files already in the share are not affected, and files copied into the share via other means (scp or ftp, for example) are not affected.

As I said, it works the same way on Windows (NTFS file permissions apply), the difference is that file permissions on most people's windows boxes tend to be a little loose.

---

### Post by happyhacker on 2008-12-10
I now seem to have a little arrangement setup which allows write for named members for a share and another share which allows anyone write access to files.

One problem I have now is when I log on. When I start up in the mornings I click on the share on windows and get the logon box. I put in my username but no password is expected (I have to leave it blank). But this user has password configured.

[LIST=1]
[*]I see that in Linux the associated group has "No password" set. Is this why I am bypassing the password?

[*]Are there group and user passwords to attend to (Samba does not seem to configure group passwords)?

[*]If I want users to go straight into a share without the password, how do I configure this?
[/LIST]

---

### Post by lykwydchykyn on 2008-12-10
1. I don't know where you're looking to see this, but I don't think it should matter.
2. I'm not aware there's any such thing as a "group password" in any OS.  Groups are just names given to a collection of accounts, to which privileges can be assigned.  You can't login as a group. Samba does keep its own database of passwords, so you need to specify passwords for accounts using the smbpasswd command.  You can configure them to sync with the Linux accounts, so that every time you change a user's password the samba password gets changed too.  But for technical reasons they aren't the same by default (think it has to do with the encryption methods used by Samba/Windows and Linux being different).
3. Putting 'guest ok = yes' on a share should do it, but I've never been successful in predicting how Windows will respond to various security settings.  Some of it depends on how the Windows machine is set up (simple sharing mode, domain membership, etc).

---

