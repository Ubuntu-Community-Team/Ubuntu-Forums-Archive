---
title: "Samba is missing"
date: 2010-09-24
forum: Server Platforms
---

### Post by p2ranger on 2010-09-24
My server has been serving me files faithfully for serveral months. Tonight, I can no longer connect to my shares from a Mac. I had samba set up and running well, but now, I can't find the printer hooked up to my linux server and I can't find the folder share. I tried restarting samba from

```
sudo /etc/init.d/samba restart
```

But that is not longer there. I removed samba with apt-get and reinstalled it. It is still not there when I try the restart command. Any ideas what happened?

I've been working with trying to setup backuppc, but I can't imagine I did anything to samba in doing that

Thanks

Jason

---

### Post by CharlesA on 2010-09-24
Since you are running Lucid, you start/stop/restart samba like so:

```
sudo service smbd start|stop|restart
sudo service nmbd start|stop|restart
```

You can also see if it's running or not by using this command:
```
service smbd status
service nmbd status
```

---

### Post by p2ranger on 2010-09-25
Wow, I had no idea that had changed. Thank you so much for the information

Jason

---

### Post by CharlesA on 2010-09-25
There were a bunch of things converted to upstart. I know there's a list somewhere, but I am not sure where it is off the top of my head.

---

### Post by p2ranger on 2010-09-25
I upgraded from 9.04 to 10.04 recently. I had been running 10.04 for a couple of weeks with no problem. Don't know what would have caused it to stop working. Is there anything new about configuring it I should know about it? The file share and printer still don't show up in my mac or my linux desktop. I saved the files that were in /etc/samba and copied them back into that directory after reinstalling it. I was hoping that the samba.conf file was the only thing that needed to be changed after installing it.

Thanks

Jason

---

### Post by p2ranger on 2010-09-25
Upstart? Never heard of that. Well, that will be a good place to start reading about. Thanks

Does this effect other things such as how apache starts now as well?

Jason

---

### Post by CharlesA on 2010-09-25
> **p2ranger said:**
> I upgraded from 9.04 to 10.04 recently. I had been running 10.04 for a couple of weeks with no problem. Don't know what would have caused it to stop working. Is there anything new about configuring it I should know about it? The file share and printer still don't show up in my mac or my linux desktop. I saved the files that were in /etc/samba and copied them back into that directory after reinstalling it. I was hoping that the samba.conf file was the only thing that needed to be changed after installing it.

Thanks

Jason

I've used the same smb.conf from 9.04 to 10.04 without many problems (my problems weren't caused by smb.conf). However I haven't done printer sharing with it, so I don't know if anything would change.

> **p2ranger said:**
> Upstart? Never heard of that. Well, that will be a good place to start reading about. Thanks

Does this effect other things such as how apache starts now as well?

Jason

Indeed. To start/stop apache2 it is:

```
sudo service spache2 start|stop|restart|status
```

There is some info about upstart [here]("http://upstart.ubuntu.com/"), but it's not very helpful. You'd probably have better luck doing a google or search on the forums.

---

### Post by p2ranger on 2010-09-25
Thanks for your help. That will give me a direction to start.

Jason

---

### Post by p2ranger on 2010-09-29
Been out of town for a few days and couldn't work on this.

So, Samba is running on my server. I know that by this:

```
sudo status smbd
smbd start/running, process 28788
```

But I'm not able to browse my shares or locate my printer on my  mac. On my ubuntu laptop I can print and browse the share without any problem.

That tells me that something is wrong with Samba. I'm not sure how to solve this.

Any ideas?

Thanks for any help

Jason

---

### Post by Vegan on 2010-09-29
cd /etc/samba

and open smb.conf

select all, and paste into this forum

---

### Post by p2ranger on 2010-09-29
Here is what is in my smb.conf file:

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = cotting

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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
  security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

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

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

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
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

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

#Share info
[share]
comment = Files for network to share read and write
path = /media/raid1/share
read only = no
guest ok = yes

[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
public = yes
writable = no
create mode = 0700
printcap name = /etc/printcap
print command = /usr/bin/lpr -P%p -r %s
printing = cups

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
```

---

### Post by Morbius1 on 2010-09-29
Since your [share] share is allowing guest access you might want to check to see if the permissions are set correctly on the directory and it's parent :
```
ls -al /media/raid1
```Your [printers] share seems rather complicated but I'm fairly certain samba is ignoring most of it. If you do a "testparm -s" this is what samba will interpret:
> [printers]
    comment = All Printers
[COLOR=Blue]     path = /tmp[/COLOR]
    create mask = 0700
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No
The problem appears to be the path. It should be:
> path = /var/spool/sambaIs there a reason you changed it?

---

### Post by p2ranger on 2010-09-29
I checked the permissions and they are correct for my share folder.

I don't remember why I changed what I did in the printers section of my .conf file. I looked back at my notes I made when I set this up, and that is what I used. It worked back then.

I changed it to what you recommended, restarted samba, and the printer still doesn't show up when I try to add the printer on the mac.

Thanks

Jason

---

### Post by Morbius1 on 2010-09-29
from the linux machine post the output of the following command:
```
smbtree
```

---

### Post by p2ranger on 2010-09-29
It asks for a password and then there is no output. The next command prompt shows up.

I take it that means something is wrong.

Jason

---

### Post by Morbius1 on 2010-09-29
nmbd isn't running would be my best guess.

See if it's running:
```
sudo service nmbd status
```And start it it it's not:
```
sudo service nmbd start
```

Then see if smbtree has output.

---

### Post by p2ranger on 2010-09-29
You were correct. NMBD was not running. I started it and here is the output from smbtree:

```
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

```

Jason

---

### Post by Morbius1 on 2010-09-29
That specific error message has a fix but you shouldn't be getting it from your own machine. Since all you have are guest accessible shares I would suggest you change your security setting in smb.conf from this:
> security = SHARE
To the default:
```
security = user
```
Then restart samba

---

### Post by p2ranger on 2010-09-29
Wow! That did it. Thank you very much for your help. I have no idea how things changed to cause it to break, but it works now. I really appreciate it.

Jason

---

