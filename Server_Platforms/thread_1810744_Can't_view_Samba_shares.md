---
title: "Can't view Samba shares"
date: 2011-07-23
forum: Server Platforms
---

### Post by Smith oo4 on 2011-07-23
I have a fresh installation of Ubuntu 10.04 LTS – I have installed Boxee on it that is all – and I am trying to set it up as a Samba Server.  I have followed the instructions on following page:

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html")

On the box that I am trying to setup as a Samba Server using Nautilus I can view the shares no problem.  On another Ubuntu box no such luck.  I can get too Windows Network and I can see my workgroup.  When I try and open the workgroup I get the following dialogue box for some time:    

Opening "WORKGROUP".
You can stop this operation by clicking cancel.

And then this error dialogue box:

Unable to mount location
Failed to retrieve share list from server

I have spent sometime trying to resolve this myself but have had little luck.  As far as I know I have no firewalls in place; Ubuntu does not have one by default is that correct?  At this time I don't have a Windows computer to try to connect too the server at this time, but plan to in the future that is why I want to use Samba.

I am connecting the two boxes with an D-Link DIR-825 router; both boxes are on the same subnet.  Are there settings in the router that could be affecting this?   

Can any one give me some help on how to troubleshoot and get this working?

Cheers

---

### Post by brighty22 on 2011-07-23
In my samba experience, these errors are almost always either permissions or smb.conf written incorrectly. Very rarely is it a firewall or router. Can you post the contents of /etc/samba/smb.conf for starters?

---

### Post by Morbius1 on 2011-07-23
Here's a preliminary checklist to go through when you have the dreaded "Failed to retrieve share list from server" error:

**[1]** Machine name.
By default Samba uses the machine name to broadcast itself to the rest of the network. But there are rules - it has to be 15 characters or less in length. So run the following command:
```
hostname
```If it's more than 15 characters you have a problem. To fix this edit /etc/samba/smb.conf as root and add the following line to the [global] section:
```
netbios name = something-less-that-15-characters-in-length
```
It can be anything you want but keep it to less than or equal to 15 characters.

Then restart samba:
```
sudo service smbd restart
```**[2]** Firewall
If you did anything to firewall on any of your machines disable it at least long enough to see if it's getting in the way.

**[3]** Services
Make sure the following services are running:
```
sudo service smbd restart
sudo service nmbd restart
```**[4]** Path Permissions
If your path is /srv/samba/share then /srv, /srv/samba, and /srv/samba/share have to be at least 755 ( actually the first 2 only need to be 711 but let's not quibble ).

If the above does nothing for you then I would do the following:
[B]
[1][/B] See if Samba on both the server and the client are functioning. From the client machine run the following command:
```
nautilus smb://192.168.0.100
```Change 192.168.0.100 to the ip addres of the server. This way you are not browsing for the server by name you are accessing it directly by ip address. If it works then the problem isn't samba its the network - name services I suspect.

**[2] **Run the following command:
```
smbtree
```It should output every workgroup on your lan, and within every workgroup every host, and within every host every share. If it finds a problem it will give you an error message. The error message can then be a starting point for further investigation.

---

### Post by Smith oo4 on 2011-07-23
I have gone through your check list and everything passed, but I still can't view the shares.  But I can view the them fine when I use IP address.  When I ran the smbtree command I go the the following output:

WORKGROUP
	\\LAPTOP         		morgan-Pangolin-Performance server (Samba, Linux
cli_start_connection: failed to connect to LAPTOP<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\BOXEE          		morgan-laptop server (Samba, Ubuntu)
cli_start_connection: failed to connect to BOXEE<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

Laptop is my LAPTOP which I am using as client, and BOXEE is the server.  BOXEE is an older laptop with a broken keyboard I am trying to re-purpose.

I don't have much time to look into the error message right now.  I hope to tomorrow but if you can give some in-site it would be appreciated.

Also, you talked about a name services; what is this, can your recommend some good reading on this? I  don't remember coming across anything that recommended setting up a name server as part of samba, is this something I should have done?

Here is my smb.conf file:
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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = boxee

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
   security = user

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

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```

---

### Post by brighty22 on 2011-07-23
Setting up a name server is optional.

Make a copy of your existing smb.conf, and build up from the basics:

```
[global]
workgroup = WORKGROUP
netbios name = boxee
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000

security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
map to guest = bad user

[share]
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0777
directory mask = 0777
```

Then run
```
[sudo] chmod -R 777 /srv/samba/share
```

By making the share completely accessible, you can eliminate permissions as the problem. Make little changes at a time, restarting samba after each.

---

### Post by Morbius1 on 2011-07-24
> But I can view the them fine when I use IP address.Then Samba itself is working.
> Error NT_STATUS_UNSUCCESSFULGive this a shot. On all your Linux machines make the following change:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
name resolve order = bcast host lmhosts wins
```Save the smb.conf file and back in the terminal restart samba:
```
sudo service smbd restart
```[COLOR=Blue]*BTW, I'm old school when it comes to permissions so I would not recommend you do the following:*[/COLOR]
> [sudo] chmod -R 777 /srv/samba/shareSince /srv/samba/share is allowing guest access you do need 777 on the shared folder itself so the following is necessary ( without the -R ):
```
sudo chmod 777 /srv/samba/share
```If you feel the need to change permissions on all the files and subfolders within that share then I would use this command instead:
```
sudo chmod -R a+rwX /srv/samba/share
```[COLOR=Blue]*Note the big "X" is not a little "x".*[/COLOR]

A "chmod -R 777" will make every folder executable ( which you want to do ) but also make every file executable ( which you do not want to do ).

A "chmod -R a+rwX" will make every folder executable but will not make every file executable unless it's executable already.

---

### Post by Smith oo4 on 2011-07-24
Adding “name resolve order = bcast host lmhost wins” has fixed things.  I also did some reading on the topic and I think I understand why it worked.  Thank you for your help.

---

### Post by lordnikon on 2012-03-21
Smith oo4,

  Just curious where you did your reading about that entry in the samba config file.  Thanks..

---

### Post by Morbius1 on 2012-03-22
I hope you don't mind but you are going to be subjected to a rant.;)

To answer your question first though it can be found here: [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

Now the rant part: The official Samba documentation is an exercise on "circular knowledge". It seems at times that every single sentence presumes that the reader has knowledge of some other component of samba or networking in general. Attempts have been made by Samba to provide documentation in a more linear mode but it's audience is still not the home user that uses Samba in a more peer-to-peer mode.

The default setting of "name resolve order" is: [I]lmhosts host wins bcast

** [/I]lmhosts and host are not set up by default for samba so they are non functional for this purpose.[I]
** [/I]wins refers to a WINS server and that too is not set up by default.
** That makes bcast as the only working mechanism available and it's listed last.

If everything was working properly it shouldn't matter what order they are in since samba will use one method and if it fails move on the to next one ( just like Windows does ), but in some cases it gets stuck at wins before it gets to bcast and never moves on. Samba was originally created for UNIX servers in an enterprise environment. In an enterprise environment with hundreds of clients you don't want to use bcast where everyone is broadcasting their presence to everyone else - it would slow everything down - so it was listed last and is probably just removed from the list in that kind of set up. In a home environment you want just the opposite - bcast first.

---

