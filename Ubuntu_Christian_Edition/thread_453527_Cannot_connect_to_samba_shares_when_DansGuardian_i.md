---
title: "Cannot connect to samba shares when DansGuardian is Enabled"
date: 2007-05-24
forum: Ubuntu Christian Edition
---

### Post by theicyj on 2007-05-24
Does anyone know how to browse samba shares when DansGuardian is enabled?  When DansGuardian is disabled, I can view them with no problems at all.

---

### Post by tak1150 on 2007-05-24
Sorry: I don't have an answer to your question, but the psalm in your signature is my favorite psalm as well :)

---

### Post by tak1150 on 2007-07-05
OK, I have the same problem now...

Somebody, help!

---

### Post by tak1150 on 2007-07-05
OK, I figured this out!

You have to edit the configuration file for the firewall "firehol"
```
sudo gedit /etc/firehol/firehol.conf
```

And either add or uncomment this line
```
server samba accept
```

Restarting firehol did not work for me. I had to reboot the computer, but hey it worked!!

Tak

---

### Post by theicyj on 2007-07-06
Thanks for the help (and nice comments).  I have since removed DansGaurdian because of some issues I have had with it, such as this one. I think I will have to give it another try though.

---

### Post by tak1150 on 2007-07-06
All righty,

Now DansGuardian is not filter any more! (after the modification to the firehol config file)

Back to square 1, somebody, HELP!

---

### Post by theicyj on 2007-07-09
I got samba shares working perfectly.

Here is my firehol.conf (hope this helps):
> iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
	policy 	drop
	protection strong
	client all 	accept
	server smtp 	accept
	server cups 	accept
	server samba 	accept
	client samba 	accept
#server webcache accept
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

# Accept all client traffic on any interface
	#client all accept

---

### Post by tak1150 on 2007-07-09
Once you comment out
```
client all accept
```

DansGuardian is working again (and Samba too!)

---

### Post by petedct on 2007-07-21
Thanks for the firehol config theicyj. It's begun to loosen the hold firehol has on my samba network. I still have one problem though. I have three PCs on the network. One running Feisty without Dans, one running Feisty with Dans and an XP box. Using the above firehol config on the Feisty/Dans box the Feisty boxes are talking just fine and the XP box can see the Feisty/Dans box but the Feisty/Dans box can not see the XP box. If I stop firehol on the Feisty/Dans box then it can see the XP box but once firehol is started back up then the XP box can no longer be seen. Any ideas?

---

### Post by tak1150 on 2007-07-22
So it sounds like you already have a shared folder in the XP box?

When you do
```
nmblookup hostname_of_XP_box
```

What do you get in the terminal (of Ubuntu box)?

---

### Post by petedct on 2007-07-23
Hi tak1150, thanks for responding.

Yes all 3 three PCs have shared folders.

On the Ubuntu/Dans box with firehol running:
nmblookup cjd
querying cjd on 192.168.0.255
name_query failed to find name cjd

With firehol stopped:
nmblookup cjd
querying cjd on 192.168.0.255
192.168.0.3 cjd<00>

---

### Post by petedct on 2007-07-23
Update:
With firehol running I can connect to the XP PC using it's ip address but not the hostname. Actually I need to use the ip address to connect to my other Ubuntu PC, without Dans, as well. Now I'm not sure if I have a networking issue or firehol issue.

---

### Post by tak1150 on 2007-07-23
Can you post your "firehol.conf" (see above posts) and "smb.conf" (in /etc/samba/)?
Thanks.

---

### Post by petedct on 2007-07-24
I'm thinking that I may have to allow one more networking service in firehol. Thought that it could be wins but I see that wins is not turned on in samba. Maybe I need to turn it on in samba then allow it in firehol?

Here are the configs.

firehol

```
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server smtp accept
server cups accept
server samba accept
client samba accept
#server webcache accept
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

#Accept all client traffic on any interface
#client all accept
```

samba

```
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
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
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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


[transfer]
path = /home/pete/transfer
available = yes
browsable = yes
public = yes
writable = yes
```


Thanks

---

### Post by tak1150 on 2007-07-27
Is that all of your smb.conf?

If it is, there is a huge section of it that's missing.
There should be a section that starts with [global]

Perhaps you should re-install samba?
Otherwise, I can post my smb.conf, but I gotta run for now; sorry!

---

### Post by TravMan63 on 2007-08-09
Sounds like a firehol problem, I wouldn't think Dansguardian would stop this (not sure though).

Check out
[http://firehol.sourceforge.net/tutorial.html](http://firehol.sourceforge.net/tutorial.html)

and

[http://firehol.sourceforge.net/services.html](http://firehol.sourceforge.net/services.html)

Appears to me a port is being blocked by the firewall.

TM

-edit
for the XP box being unseen - try
server microsoft_ds accept or
client microsoft_ds accept

---

### Post by petedct on 2007-08-10
Yes I agree. It's most likely firehol that needs a service to be accepted. I tried as you suggested with microsoft_ds and had no luck. I'm not up on networking enough to know which service it could be. I've tried several from the list at your second link but again no luck. Thanks for your trouble.

---

### Post by tak1150 on 2007-08-11
I might be way off, but...

Is your samba share tunneled through SSH? If it is, you will have to open the port for SSH in firehol.

```
server ssh accept
```

To make sure that it is a firewall problem, try
```
sudo /etc/init.d/firehol stop
```
while you have your dansguardian enabled.
(I'm pretty sure that dansguardian filtering still works with firehol being stopped b/c it's thru proxy and not ports that it filters).

If your samba works with after the above command, it's definitely firehol.

---

### Post by petedct on 2007-08-11
Good ideas but ssh is not installed. Also, when firehol is stopped Dan's filtering is stopped as well. Fortunately I can connnect using IP addresses. Host names are easier to remember though. Thanks

---

### Post by tak1150 on 2007-08-13
I just confirmed on my laptop; you can have firehol disabled while dansguardian is working. As said before, dansguardian works with proxy and not ports.

---

### Post by petedct on 2007-08-13
If I just stop firehol I can easily find offensive content with Firefox. What are your Dansguardian settings?

---

### Post by tak1150 on 2007-08-14
Oh I am sorry; I forgot that I changed the proxy setting so that dansguardian works independently.

In Firefox (i use swiftfox, but it's the same), go Edit --> Preferences --> Advanced --> Network --> Settings

I set it to Manual Proxy Configuration.
For "HTTP Proxy" 127.0.0.1
For "Port" (next to HTTP proxy) 8080
Leave everything else untouched.

This should work (unless of course I'm forgetting something again) and it should be independent of firehol. Let me know how this goes.

---

### Post by petedct on 2007-08-16
That works!!  I can connect to the other PCs on my network using host names and the undesirable contect is blocked in Firefox. Thanks.

One last question. Should I just flat out remove firehol, I'm behind a router, or is there a way to keep it from starting?

---

### Post by tak1150 on 2007-08-17
I suggested stopping firehol and keeping dansguardian running so that you can be sure that it's a firehol problem (even though I still think it's your smb.conf file that is causing the problem, but I could be very wrong).

If you are behind a router that has no open ports (except for TCP 80 for viewing web, etc) and have other means of security, it might be alright to not have a firewall. But I still recommend that you have one.

If you want to semi-permanently disable firehol without removing it (so you can come back to it later),

```
sudo gedit /etc/default/firehol

```
Then where it says "START_FIREHOL=YES" change it to
```
START_FIREHOL=NO
```
After you either stop firehol or reboot, firehol will not start automatically any more.

You could, instead of firehol, try Firestarter, which has nice GUI w/ it. If you do this, make sure that you get the binary (deb file) and not the source so that it's easier to start it automatically at boot.

I have had some trouble with Firehol and I have not been able to configure it so that it runs and allows my web server to function. So on the web server machine I'm using firestarter. One thing I don't like about it is I have not figured out how to do things from command line (b/c I'm away from it sometimes).

If you like to, I'd be happy to work this out together so that your Samba system works with firehol. I'm curious to see how that'd work as well. It may be related to netbios things... Got to get back to work now though.

---

### Post by petedct on 2007-08-18
Thanks for your generious offer of continued assistance.

I've been playing a bit with Firestarter in a VM. So far so good.

I botched the cut and paste if my Samba config file 3 weeks ago so here it is again.

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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

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
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
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
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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


[transfer]
path = /home/pete/transfer
available = yes
browsable = yes
public = yes
writable = yes
```

---

### Post by tak1150 on 2007-08-21
Your smb.conf looks fine.
I vaguely remember that the first 2 lines in firehol.conf are for filtering all traffic and not just for web browser. Now that you've set your browser proxy manually, perhaps you can comment out the 2 lines and turn on firehol?

---

