---
title: "accessing server"
date: 2009-03-19
forum: Server Platforms
---

### Post by wordmaster on 2009-03-19
I am an old hand with DOS and windoze, but new to linux. I am experimenting with setting up an Ubuntu server and and having trouble with the smb.conf file in Samba...at least I think that is where I am going wrong.

Exactly how do I set up a share directory in that file? From my win98se client, I go to windows explorer, put the ip address in the bar and it comes up and says "It Works!" which I "assume" means that I have actually connected to the server. However, trying to follow that with any of the directories I thought were shared gives me a "not found" error.

What I have used to connect is:

//10.3.9.195/

When I add any dir name to this I get the error. Any and all help greatly appreciated.

---

### Post by HermanAB on 2009-03-19
Uhmmm, the "It Works!" comes from the default installation of the Apache web server.  That doth not Samba make...

Samba is a file server.  Here is some debug information:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by hictio on 2009-03-19
Also take a look at the [Ubuntu Server docs](https://help.ubuntu.com/8.10/serverguide/C/), specifically, the [Windows Networking](https://help.ubuntu.com/8.10/serverguide/C/windows-networking.html) section.

Another thing, to connect to a Samba server/ share, you have to use the backlashes (\\), a quick way to do that is, on the Windows box, typing the Windows key Logo + R, and in the 'Run' box that pops up, typing this:

```

\\ip.address.samba.server\share\

```

---

### Post by papenpj on 2009-03-20
I use samba to share my media the the windows XP machines on our network.
For some reason I can't use either IP that is assigned to my server to acccess the shared file but i can use the computer name as it appears on the windows workgroup pages.
meaning that
"\\Patrickmedia\Media" is the name I use to get access to my shared folder.

In /etc/samba/smb.conf
my entry looks like this
```

[Media]
        path = /home/shared
        valid users = ps3media, root
        read only = No
        create mask = 0755
        directory mask = 0755

```
The folder is owned by root, and if i select as the user name to login I can add and modify files from the windows share that I mapped as a network drive.  However, my roomamtes use PS3media with only read, execute

---

### Post by wordmaster on 2009-03-25
Thank all of you for your help. I have tried everything, I have been to the urls mentioned and done what they said to set up shares in the smb.conf file, I have tried all different variations of access addresses from my win98se box and am still unable to connect to my linux box. 

The furthest I have gotten is the "it works" page which is apparently the Apache server, not the samba server. As soon as I add the share directory I get a page not found. I have tried various path commands and it is still the same. I have restarted samba, done everything I could think of, but no joy.

Would it be OK to post my smb.conf file so perhaps someone could tell me what is wrong? Thank you for any and all help.

---

### Post by BkkBonanza on 2009-03-25
If you type the address into Explorer it will assume the default protocol http. You need to specify the protocol smb so it's knows to use the smb port not the http port. Your address should be like this,

smb://10.3.9.195/

And yes, paste your smb.conf and maybe we can help. Also note that to view other shares from Ubuntu the default smb client is present but to share files from Ubuntu to other machines you need to install Samba server. Not sure if you did this yet. Look on desktop menu, System->Administration->Services and enable "Folder Sharing Service" (Samba).

---

### Post by wordmaster on 2009-03-25
Thank you. I tried the smb: address and got page not found. I have tried to set up samba with minimum security til I learn more about how to use it. Here is what I have in my smb.conf file. Also, I restarted samba just to be sure it is running.:

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
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = users
   

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
 ;  dns proxy = yes

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
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# Older servers may not support the higher level of defaul security for
# password negotiation and may require uncommenting the following line.
  client lanman auth = yes

# Older servers may not support the higher level of defaul security for
# password negotiation and may require uncommenting the following line.
  lanman auth = yes

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;   passdb backend = tdbsam

;   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
;   passwd program = /usr/bin/passwd %u
;   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;  domain logons = yes
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
         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
   domain master = no

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
   winbind enum groups = yes
   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755


# Maximum number of usershare. 0 (default) means that usershare is disabled.
   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   read only = no
   share modes = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = yes
   browseable = yes
   create mask = 0775
   directory mask = 0775

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
[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /cdrom
   guest ok = yes

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
   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


Now there it is, where did I go wrong?

---

### Post by theRick on 2009-03-25
I don't necessarily know what is causing your problem, but here is how my share is setup on my ubuntu fileserver which is sharing flawlessly throughout several computers and miscellaneous operating systems in my home network.

Make sure your workgroup is users on the 98 machine - and my smb.conf contains the following... perhaps you can try this with your path

[windows file share]
comment = Public Folder
path = media/mediastorage
guest ok = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

Reloaded samba and it shows up on all the machines including the OSX machine.

edit: I also did chmod 777 to the shared folder.

---

### Post by BkkBonanza on 2009-03-25
For just starting out I did not need to touch smb.conf at all. In your case since you seem to be getting nowhere and may have altered something to cause issues it may make sense to backtrack. Turn off the service, uninstall samba, remove smb.conf and then re-install and turn on the service. It really should work without touching smb.conf. And once it does then you can try adding things in for security and control. Just my 2 cents.

Also, yes, make sure all your machines are on the same workgroup. Mine seemed to be HOME by default. Or maybe it detected that from my windows machine. Don't know.

---

### Post by koenn on 2009-03-25
Samba isn't the problem here.
The "it works" page and "page not found" are returns from a web server. That means your Win98 explorer is talking to port **80**, the http port of your server. It should be connecting to the smb ports. I forgot which ones are those (137-139 udp ?), but it doesn't matter : Explorer should know how to connect to a file server.

So either
- you're using Internet Explorer, not explorer ?
- you're prepending your addresses with http:// ?
- any other user mistake ?

If it's not a case of PEBKAC, the only explanation I can come up with for now is that explorer falls back to http bcause it finds nothing useful at the smb ports. I don't know if that's even the expected behavior of explorer, but you might want to check

* according to your smb.conf, the network path to your share should be \\servername\share, or \\serveripaddress\share.

* the directory  /srv/samba/share actually exists on your server ?

* the share "[share]" is defined twice in your smb.conf. I don't know if that can cause problems, but maybe try with one definition anyway :)
restart samba after changes

If all else fails, try ```
 START \\servername\share 
``` in a command window and see what it says/does.

---

### Post by wordmaster on 2009-03-27
Well, I set up a client for Microsoft networks, went to user level access control, and changed my workgroup name to "users" and I think I finally am able to connect to the Ubuntu server. Previously I only had the client for Netware networks in place.

However, while it appears to connect, a block pops up asking for a password. I never set up a password in the smb.conf file and I didn't (at least intentionally) set up anything in there to require a password. 

I tried my root password, I tried leaving the password blank, and I tried several other things, but nothing was accepted. Can someone please tell me what I need to put in the smb.conf to add a password and make this thing finally work? Thank you for any help.

---

### Post by wordmaster on 2009-03-27
Can anyone help?

---

### Post by koenn on 2009-03-27
> **wordmaster said:**
> Can anyone help?

First, make sure WORKGROUP is the same on the server as on the clients. 

Samba uses "user level security" by default, which requires samba user accounts, which you create with ```
smbpasswd -a <username> 
```

*username* will be the account that you authenticate with when the password popup pops up.

[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#smb](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#smb)
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-security-modes.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-security-modes.html)

---

