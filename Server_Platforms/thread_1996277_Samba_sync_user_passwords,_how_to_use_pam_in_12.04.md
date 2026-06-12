---
title: "Samba sync user passwords, how to use pam in 12.04?"
date: 2012-06-04
forum: Server Platforms
---

### Post by archknight on 2012-06-04
So, I have successfully created a samba server on an Ubuntu server, which I can access from a windows machine on the local network. However, I had to set an aribtrary samba password for it and access it from a specific windows user name, which is fine for me but I cannot have everyone who uses this system doing that. 
 
My goal is to make it so that users can use samba to access their personal files on a linux server from any account on any local windows machine, logging into their linux account using their regular password for that account, which is kept synchronized. There are many users and most are students and so completely new to Linux. I need to make this seemless for them, so I cannot have them setting their samba passwords or configuring anything at all on their own. Likewise, I do not and cannot know their passwords. I have been led to believe that PAM is able to sync up passwords and handle this sort of thing for me. I have no idea how to get it to work though! I am willing to do any amount of setup so long as only I have to do it and I don't need to directly deal with anybody's passwords.
 
All of the best tutorials fail right away because they are talking about starting and stopping a service called "samba" but it is called "smbd" for me and whenever I try to do what they say, it doesn't work at all. I think a lot of the information I am finding is out of date. I am running the latest version, Ubuntu 12.04 Precise Pangolin. I willing to uninstall/reinstall everything and start from scratch. Can someone please tell me how to do this or point me in the right direction?
 
P.S. I know there are lots of threads and tutorials about setting up a samba server and how to use PAM. But I have spent hours and hours reading through most of it and have been miserably unsuccessful in what I want to do. It just seems some of the best information is out of date and useless to me.

---

### Post by volkswagner on 2012-06-04
Have you added the users to SAMBA?  I believe the sync will work only after you have added the user to the samba service.  This may be a security model, so the admin can decide which users are allowed access to samba resources.

Do you have libpam-smbpass installed?

Check out[ this thread ]("http://ubuntuforums.org/showthread.php?t=1541129")for Ubuntu 10.04.

I believe the following command will list samba users;
```
sudo pdbedit -L
```

or a more verbose output
```
sudo pdbedit -L -v
```

What I have yet to find out is how to add the Unix user to the SAMBA user list without changing the password.

---

### Post by volkswagner on 2012-06-04
From the man page of pdbedit:

>        -a
           This option is used to add a user into the database. This command needs a user name specified with the -u switch. When adding a new user, pdbedit will also ask for the password to be used.

           Example: pdbedit -a -u sorce

               new password:
               retype new password

               Note
               pdbedit does not call the unix password syncronisation script if unix password sync has been set. It only updates the data in the Samba user database.

               If you wish to add a user and synchronise the password that immediately, use smbpasswd´s -a option.



I don't see any other options while using smbpassd to keep the unix password (always get prompted for password).  I think this is the key to the puzzle.

---

### Post by Vegan on 2012-06-04
samba needs to be configured to use one or another user scheme

at its most basic is using hard coded users in the samba.conf

samba can also use windows AD or Linux etc

visit samba.org where there is an excellent manual on the product

:guitar:

---

### Post by archknight on 2012-06-07
> **volkswagner said:**
> Do you have libpam-smbpass installed?
 
Check out[ this thread ]("http://ubuntuforums.org/showthread.php?t=1541129")for Ubuntu 10.04.
 
No, I did not have that installed but I do now.
 
And funny story, it seems I did the same thing as the guy in this thread. I thought samba wasn't working but I was just doing things wrong...
:lolflag:
 
Samba was actually configured properly for what I wanted BY DEFAULT. I just needed to create shares for it. The reason I didn't create any shares was because I thought they were going to work the same way as it did when I was using 10.04 (i.e. ask for a password). I didn't realize everything was already configured properly. Whenever I tried following any of the instructions for setting up samba with pam, either the changes were already made or I was being asked to do something that was not possible anymore because the instructions were out of date. So, realizing that I hadn't actually set anything up and all of the instructions being wrong, confusing, and/or irrelevant, I figured it wasn't setup yet.
 
So, I guess in the end, my problem is solved. For those who are interested, I will share everything I did and all my info. First, you need to install samba and this is how I did it:
 
sudo apt-get install samba samba-common system-config-samba
 
I also installed libpam-smbpass later. With the way our network is set up, I didn't need winbind but that doesn't mean someone else may not, so you should look into it if curious.
 
After a user is created, I just need to make a share in samba to their home directory (/home/$USERNAME) and I do that by opening up system-config-samba and going to File->Add Share. For the directory, I navigate to the home folder of the user I want to add "/home/username". The Share Name will automatically get filled in with the name of the folder, which should be the username in this case and I prefer it that way. It doesn't matter what it is though. It is just the name that of the share that you use when connecting from another computer (like a windows machine, as in my case): [\\computername\sharename]("file://\\computername\sharename"). I then check writable and visible. Lastly, I go to the Access tab and select the username from the list (which should have automatically been added there) so that they are the only ones who can access the share to their home folder. 
 
And done! That user can now access their files on this linux machine from any local windows computer by running \\[linuxcomputername\sharename]("file://\\linuxcomputer\username") in Explorer or the run window. Then when prompted for a password, they just need to enter the name linuxcomputername\linuxusername and then enter their regular linux password. And then their home folder will open and be accessible!
 
For those who are interested, here are the contents of every related configuration file that I can think of (in case things don't just magically work by default for you like they did for me).
 
Here is /etc/pam.d/common-password:
```

# here are the per-package modules (the "Primary" block)
password        [success=1 default=ignore]      pam_unix.so obscure sha512
# here's the fallback if no module succeeds
password        requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password        required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
password        optional                        pam_smbpass.so nullok use_authtok use_first_pass
password        optional                        pam_gnome_keyring.so 

```
 
/etc/pam.d/samba (I guess I did modify this file to include the last line, which was not there originally):
```

@include common-auth
@include common-account
@include common-session-noninteractive
@include common-password

```
 
/etc/samba/smb.conf (this one is long!):
```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
        workgroup = workgroup

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;       encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;       passdb backend = tdbsam

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
;       printing = cups
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
;       usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
        usershare allow guests = yes
        username map = /etc/samba/smbusers
        security = user
;       guest ok = no
;       guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
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
;       guest ok = no
;       read only = yes
        create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
;       browseable = yes
;       read only = yes
;       guest ok = no
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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[homes]
        read only = no
;       guest ok = no
;       browseable = no

```

---

### Post by bab1 on 2012-06-07
> **archknight said:**
> ..this is how I did it:
 
sudo apt-get install samba samba-common system-config-samba **[COLOR="Red"]winbind[/COLOR]**
 
I also installed libpam-smbpass later.
 


Somethings die hard.  Explain why you installed winbind.  What did you think it would do for you?

---

### Post by archknight on 2012-06-08
> **bab1 said:**
> Somethings die hard.  Explain why you installed winbind.  What did you think it would do for you?

I love this... I ask for help on forums and I am told to follow an online guide. I follow a guide online and I am damned for doing that as well! Do you know how long the howto is on samba.org? I have spent hours reading it, trying to figure it out and it never made any sense. So, I found this guide [http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/) from Googling around and since it was the only thing I could find that was actually UP-TO-DATE for a change, I did what it said... I have no idea what winbind was going to do for me and I didn't really care so long as I could get it to work. 

That being said, is it not necessary? If so, I don't mind uninstalling and updating the info I provided so it is more useful to everyone else as a solution.

---

### Post by bab1 on 2012-06-09
> **archknight said:**
> I love this... I ask for help on forums and I am told to follow an online guide. I follow a guide online and I am damned for doing that as well! Do you know how long the howto is on samba.org? I have spent hours reading it, trying to figure it out and it never made any sense. So, I found this guide [http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/) from Googling around and since it was the only thing I could find that was actually UP-TO-DATE for a change, I did what it said... I have no idea what winbind was going to do for me and I didn't really care so long as I could get it to work. 

That being said, is it not necessary? If so, I don't mind uninstalling and updating the info I provided so it is more useful to everyone else as a solution.
Who's damning anyone?  What makes you think life was easy or that the solution should just fall to hand.  I would never install something I didn't know what it was for and how it worked.

At this point I can only tell you that for a simple peer to peer LAN (no domain accounts) that  this particular howto is wrong on at least 2 points.

I know it sounds like you are starting over, but the key to installing Samba correctly is to understand what it can (and can't) do.  I'll help you, but we should start with all the information needed to insure success.

How about we start with what type of install you do have and what you expect it to provide.  Is this a p2p situation or a domain with centralized user management?  How many IP segments are involved (do you have separate subnets?)  How many user accounts are involved?

Before you ask; yes, I have read you posts in this thread.   ;-)

---

### Post by archknight on 2012-06-09
> **bab1 said:**
> What makes you think life was easy or that the solution should just fall to hand.  I would never install something I didn't know what it was for and how it worked.

Nobody suggested that life ought to be easy, only that one should be able to install and run software without having to know every detail about how it works. Because if that was the requirement for installing a program, why wouldn't I just write it myself instead of learning someone else's program in full detail? Besides, modern operating systems have hundreds of megabytes, if not gigabytes, of data in them and have you installed an OS while knowing how all of it works? I doubt it is possible... It certainly isn't reasonable.

> **bab1 said:**
> At this point I can only tell you that for a simple peer to peer LAN (no domain accounts) that  this particular howto is wrong on at least 2 points.

I see... That sucks...

> **bab1 said:**
> I know it sounds like you are starting over, but the key to installing Samba correctly is to understand what it can (and can't) do.  I'll help you, but we should start with all the information needed to ensure success.

I don't mind starting over at all! (Even though it is working fine for me at the moment... >_>) If you are willing to help, I will gladly follow your instructions. Frankly, I am surprised at the offer. Most of the help I have seen on these forums has seemed not very useful... So, thank you! VERY MUCH!

> **bab1 said:**
> Before you ask; yes, I have read you posts in this thread.   ;-)

I wasn't going to ask. I recognize I didn't provide all details about my setup and I don't think you are asking anything I already provided. If you had said something useless like "visit samba.org where there is an excellent manual on the product" after I said "I know there are lots of threads and tutorials about setting up a samba server and how to use PAM. But I have spent hours and hours reading through most of it and have been miserably unsuccessful in what I want to do", then I would be a bit annoyed...

> **bab1 said:**
> How about we start with what type of install you do have and what you expect it to provide.  Is this a p2p situation or a domain with centralized user management?  How many IP segments are involved (do you have separate subnets?)  How many user accounts are involved?

I don't know what information is useful and what is irrelevant so I will just tell you as much as I know and hope I am not wasting your time. We have a freshly installed Ubuntu 12.04 system, the x86-64 desktop version, which is supposed to act as a server for computational research done by a few users. It is unlikely we will ever have more than 10 users accessing the system at once, but we will probably have dozens of accounts on the system (but probably less than a hundred). All users access the server through SSH and SFTP from computers on the same network (except the other administrator of the server uses the desktop for some image-editing/GUI/graphics-card-related stuff from time to time). The server does have Internet access but is hidden behind the network firewall and so is not directly accessible off-site (which is fine by us). 

The situation with the network is a bit weird. The network we are on uses active directory and all of the controlled machines (i.e. not personal machines) are on the domain. This server is not. And the network administrators will not let us do anything fancy at all with the network (and I know next to nothing about AD so forgive me if I say something ignorant related to it). In fact, the sys admins have completely disowned this machine because it is too much of a hassle for them to set up and control, so us researchers are just doing it by ourselves (we prefer it this way). However, they did grant us a static IP (DHCP) which should correctly resolve the server name for all computers on the network (including across subnets, I believe). The network we are on consists almost entirely of windows computers, which are the likely terminals that will be connecting to this server. Everyone on this network has a domain login but like I said, we won't have access to the domain controllers (nor do we really want to) so I will be creating server-specific logins for everyone who needs it (we are a very small part of the network). 

It was requested that we set up samba so that on their windows machines, users could create a network drive which connects to their home folder on the server. We don't plan on printer sharing through samba or anything else like that. I just want to set this up for everyone while maintaining the security of their data. I hope that answers everything. Thanks again!

---

### Post by bab1 on 2012-06-09
> **archknight said:**
> Nobody suggested that life ought to be easy, only that one should be able to install and run software without having to know every detail about how it works. 
Not how it works more like what it does.> 
Because if that was the requirement for installing a program, why wouldn't I just write it myself instead of learning someone else's program in full detail?
Once again, understanding what the software does in the end does not mean that you have to be able/need to write any code.  It does help to know and understand what the expected results are supposed to be. > 
 Besides, modern operating systems have hundreds of megabytes, if not gigabytes, of data in them and have you installed an OS while knowing how all of it works? I doubt it is possible... It certainly isn't reasonable.
It is possible and very reasonable.  Without knowing a line of code that is in my favorite editor I know how it works and how to configure it for my personal use.> 
I don't know what information is useful and what is irrelevant so I will just tell you as much as I know and hope I am not wasting your time. 

We have a freshly installed Ubuntu 12.04 system, the x86-64 desktop version, which is supposed to act as a server for computational research done by a few users. It is unlikely we will ever have more than 10 users accessing the system at once, but we will probably have dozens of accounts on the system (but probably less than a hundred). 
In this context we are interested in user accounts, not how many humans are accessing the system.  On the other hand what is the reason for more user accounts that actual users?> 

All users access the server through SSH and SFTP from computers on the same network (except the other administrator of the server uses the desktop for some image-editing/GUI/graphics-card-related stuff from time to time). 
Why are the users accessing the server (Samba) using ssh?  I can understand SFTP to move files.  In fact if you were to only offer SFTP all you need is OpenSSH server on that host.> 
The server does have Internet access but is hidden behind the network firewall and so is not directly accessible off-site (which is fine by us). 

The situation with the network is a bit weird. The network we are on uses active directory and all of the controlled machines (i.e. not personal machines) are on the domain. This server is not[on the domain]. And the network administrators will not let us do anything fancy at all with the network (and I know next to nothing about AD so forgive me if I say something ignorant related to it). 

In fact, the sys admins have completely disowned this machine because it is too much of a hassle for them to set up and control, so us researchers are just doing it by ourselves (we prefer it this way). However, they did grant us a static IP (DHCP) which should correctly resolve the server name for all computers on the network (including across subnets, I believe).
Are all the folks that will be using this server be on this same subnet?> 
The network we are on consists almost entirely of windows computers, which are the likely terminals that will be connecting to this server. Everyone on this network has a domain login but like I said, we won't have access to the domain controllers (nor do we really want to) so I will be creating server-specific logins for everyone who needs it (we are a very small part of the network).By "server specific, I assume these are the user accounts on the server; right?  My suggestion is to make these the same username/password as the domain accounts of those folks that will be accessing the server.  Can you provide me with the output from the terminal of this```
sudo pdbedit -L
```> 
It was requested that we set up samba so that on their windows machines, users could create a network drive which connects to their home folder on the server. We don't plan on printer sharing through samba or anything else like that. I just want to set this up for everyone while maintaining the security of their data. I hope that answers everything. Thanks again!
So as I understand it the Samba server will have a *share* for each users home directory.  Samba has a type of share just for that.

I think I understand enough now.  At this point I would like you to remove winbind and return the /etc/nsswitch.conf file back to it's default configuration.  To remove winbind you can do this from the terminal ```
sudo apt-get purge winbind
```

What I am thinking will work best for this situation is to consider the Samba server as operation on a LAN (no subnet) with local login only (no domain control) and setting up what is called a [homes] share.  This one share will expand to all users.  From the users perspective they will have a private home directory.  You only need to administrate on *share*.  An unfortunate use of the term.  A share is really a CIFS reasource that you can locate with //NETBIOS_NAME/share.  Its worth noting that you do not strictly need DNS name services in a small LAN.  All you need is NetBIOS broadcasts.  Ultimately you need to either convert DNS names to NetBIOS names or broadcast the NetBIOS name from the start.  FYI when you share with Windows you use NetBIOS name broadcasts.  ;-)

I don't see any shares configured in the smb.conf file you posted.  What do you get with this command from the terminal```
net usershare info --long
```

---

### Post by archknight on 2012-06-09
> **bab1 said:**
> In this context we are interested in user accounts, not how many humans are accessing the system.  On the other hand what is the reason for more user accounts that actual users?

What? How can you have more accounts on a system than there are users? Users can't access the system except if they have an account, so the numbers are equal. I said that there won't likely be more than 10 people signed in and using the system at a single moment in time. This is in case you needed to know about the sort of load that might be expected. Of course the total number of user accounts on the system is greater than the number of people typically connected at once. Not everyone is always logged in... As I said, I don't know what is and isn't relevant so I just listed everything I could think of. I am sorry if it causes confusion.

> **bab1 said:**
> Why are the users accessing the server (Samba) using ssh?  I can understand SFTP to move files.  In fact if you were to only offer SFTP all you need is OpenSSH server on that host.

This is not just a file server. It is a server for performing computation. People are connecting with ssh so they can compile and run code on the server. I only mentioned this because I wanted to explain that we will have several users simultaneously connecting with ssh and sftp in order to compile/run code, manage data, etc. and that is the primary way everyone connects to this system. I understand that having sftp and setting up samba is redundant (and rather stupid) but samba was requested by some users for purposes of ease of access (basically, because they are lazy).

> **bab1 said:**
> Are all the folks that will be using this server be on this same subnet?

I am not 100% certain about how the network is laid out, so my word can't be trusted. However, some people will be accessing the server from a neighboring building and I think different buildings (even different floors) are on different subnets. However, I have been able to ping and even ssh into the server from a different building before, so I am certain the name will resolve correctly. However, I have only tested the samba features of this server from a nearby computer (i.e. in a room next door) so I don't know if samba will work right across buildings. That is something I will test out soon.

> **bab1 said:**
> By "server specific", I assume these are the user accounts on the server; right?  My suggestion is to make these the same username/password as the domain accounts of those folks that will be accessing the server.

Yes, I will be creating user accounts on the server for those who would like to use the system. Like I said, we will not be granted access to the domain controllers. So we are not able to verify the existence of a domain user, much less synchronize passwords. Users on this server will be free to set their password to whatever they want. If it is the same password as their domain account, that is fine. But I will have no way of knowing that fact or controlling it.

> **bab1 said:**
> Can you provide me with the output from the terminal of this```
sudo pdbedit -L
```

No, I cannot. This command lists all samba users, which is all users on the system. I can tell you it looks like this (except is lists all current users on the system and not just me):

```
nobody:65534:nobody
myusername:1000:My Full Name
anotheruser:10001:Their Full Name
...
```

> **bab1 said:**
> I think I understand enough now. At this point I would like you to remove winbind and return the /etc/nsswitch.conf file back to it's default configuration.  To remove winbind you can do this from the terminal ```
sudo apt-get purge winbind
```

The command was run, winbind was removed, and I deleted the word "wins" from /etc/nsswitch.conf

> **bab1 said:**
> What I am thinking will work best for this situation is to consider the Samba server as operation on a LAN (no subnet) with local login only (no domain control) and setting up what is called a [homes] share.  This one share will expand to all users.

Yes, assume just that. It all sounds good. Except, what do you mean expand the share? I assume I am going to create a share to the home directory of each user. That seems to be working out pretty well for me so far...

> **bab1 said:**
> I don't see any shares configured in the smb.conf file you posted.  What do you get with this command from the terminal```
net usershare info --long
```

That is because I had not created any shares yet when I copy/pasted it. I didn't want people copying my smb.conf file and having info in it that would be wrong for their system (and I mentioned separately how to add shares). I do have shares listed in it though. If you want to see what it looks like, I can tell you. This is appended at the end of the file:

```

[myusername]
        path = /home/myusername
        writeable = yes
;       browseable = yes
        valid users = myusername

```

When I run your "net usershare info --long" command, it doesn't return anything (even when run as root).


So, uh... Basically, I just removed winbind because it was unnecessary. Seeing how samba was working fine with it installed, was there any real reason for this?

---

### Post by bab1 on 2012-06-09
> **archknight said:**
> What? How can you have more accounts on a system than there are users? ...
You don't know what you don't know.  There are mortal users and there are system users...and there are users that misguided folks make for multiple humans to use such as *guest* or *staff* for instance.  You can list users with ```
getent passwd 
```> 

This is not just a file server...
We're only interested in the servers (daemons) called smbd (Samba) and nmbd> 

I am not 100% certain about how the network is laid out, so my word can't be trusted. However, some people will be accessing the server from a neighboring building and I think different buildings (even different floors) are on different subnets.
This is not good.  Your client will not be able to browse Network Neighborhood to find their share(s).  Samba (Windows sharing) is not a technology that crosses routers normally.  I'd check to see if all the hosts involved are in the same subnet.  If not then you're going to need help from your network  administrator.> 
However, I have been able to ping and even ssh into the server from a different building before, so I am certain the name will resolve correctly. 
These are DNS names.  Samba uses NetBIOS names.  For the most part you are limited to local LAN for browsing.> 
However, I have only tested the samba features of this server from a nearby computer (i.e. in a room next door) so I don't know if samba will work right across buildings. That is something I will test out soon.
Test sooner rather than later> 

Yes, I will be creating user accounts on the server for those who would like to use the system. Like I said, we will not be granted access to the domain controllers. So we are not able to verify the existence of a domain user, much less synchronize passwords. Users on this server will be free to set their password to whatever they want. If it is the same password as their domain account, that is fine. But I will have no way of knowing that fact or controlling it.
The Windows machine will provide the user name when browsing to the Samba share.  Just make sure that the local user and Samba user also (all 3 users) have the same username.> 
No, I cannot. This command lists all samba users, which is all users on the system. I can tell you it looks like this (except is lists all current users on the system and not just me):

```
nobody:65534:nobody
myusername:1000:My Full Name
anotheruser:10001:Their Full Name
...
```
Fine by me, at least you do know the command and can verify the Samba user has been created later on.> 
... It all sounds good. Except, what do you mean expand the share? I assume I am going to create a share to the home directory of each user. That seems to be working out pretty well for me so far...

I do have shares listed in it though. If you want to see what it looks like, I can tell you. This is appended at the end of the file:

```

[myusername]
        path = /home/myusername
        writeable = yes
;       browseable = yes
        valid users = myusername

```
With the use of the share [homes] you only need to define the share once.  Samba internally creates the user specific share for the home directory.  Read about it [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  Look for the [homes] section> 
...

So, uh... Basically, I just removed winbind because it was unnecessary. Seeing how samba was working fine with it installed, was there any real reason for this?
It's not needed and it's one more variable the can cause erratic behavior with name resolution.  FYI: WINS is the NETBIOS name server for SMB/CIFS (Samba and Windows sharing).  Winbindd integrates local linux users to Windows style security.  You have stated that you aren't involved with your network's AD infrastructure so you don't need Winbind.  Also, Winbind has nothing to do with WINS.

To summarize, you should check the network topology for routers in between the Samba server and its Windows clients (traceroute maybe). and investigate the use of the [homes] share.  Has the issue of the syncing the local Ubuntu users password with the samba password been resolved to your satisfaction?

---

### Post by archknight on 2012-06-10
> **bab1 said:**
> This is not good. Your client will not be able to browse Network Neighborhood to find their share(s). Samba (Windows sharing) is not a technology that crosses routers normally.  I'd check to see if all the hosts involved are in the same subnet.  If not then you're going to need help from your network  administrator.

I checked it out and it is alright. Like I said before, when they gave us a static IP, they made our name resolve across subnets. I was able to access a samba share from a completely distant building without problems.

> **bab1 said:**
> The Windows machine will provide the user name when browsing to the Samba share. Just make sure that the local user and Samba user also (all 3 users) have the same username.

Users have already been instructed that when they try to connect to samba (regardless of how they are logged into a domain computer), they are to provide their Linux username and password when prompted. I mentioned this in my solution post, but they must type in: "servername\linuxusername". Obviously, the default of "domainusername@domain.com" will not work. Also, the samba users are made automatically and synced by pam to the linux users, so those names must be the same by default. So there is nothing for me to make sure of in that regard; all 3 users are always going to be the same.

> **bab1 said:**
> With the use of the share [homes] you only need to define the share once. Samba internally creates the user specific share for the home directory. Read about it [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"). Look for the [homes] section.

I did not know about this! I have tried removing all existing shares and added the following to the end of my smb.conf file:

```

[homes]
        read only = no
;       guest ok = no
;       browseable = no

```

And it works! A share gets created for all users automatically so I don't have to bother creating a samba share every time I add a user. Thanks for the tip!!!

> **bab1 said:**
> Has the issue of the syncing the local Ubuntu users password with the samba password been resolved to your satisfaction?

Well, yes, it was actually resolved before you posted... That is why I marked the thread as [SOLVED] a while ago. If there are no other issues, I will update my earlier post with my current setup. Thanks again for taking so much time to help out! I've never received so much help on a forum before and it just makes me sad that it was on an issue where my biggest concern was already solved... But my appreciation is the same regardless!

---

### Post by bab1 on 2012-06-10
Glad I could contribute the details about the [homes] section.  It makes life easier as you only need to add the user.  They have automatically access their configured [homes] share.

My original question was really to both you and subsequent users re: The appropriate use of winbind and wins.

---

