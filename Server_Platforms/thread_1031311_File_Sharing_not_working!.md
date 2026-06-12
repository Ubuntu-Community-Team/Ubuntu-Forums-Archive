---
title: "File Sharing not working!"
date: 2009-01-05
forum: Server Platforms
---

### Post by adlabens on 2009-01-05
I'm running Ubuntu 8.10 Server, basically headless.  I've got PuTTY & Webmin installed & am able to use them from my WinXP Pro boxes.  The OS is on one drive, and there's a 4 drive RAID5 array for the data, with one mount point /NW-DATA on it.  I have gone into Webmin's File Manager & shared various folders, which all appear on my Windows Explorer screen - I can see the folders, but cannot access them!  

I really want sub-folders to inherit the sharing qualities of their parent-folders, but, so far, I'm having to share each folder individually (not that it does any good, nothing is accessible!).

Here's my /etc/samba/smb.conf file:
> #
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
	obey pam restrictions = yes
	force group = admin
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	netbios name = RCH-SERVER
	delete readonly = yes
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = RCH-WORKGROUP
	os level = 20
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
   security = user

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
;   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0775

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


[share]
	force create mode = 0660 
	force directory mode = 0770

[NWDATA]
	writeable = yes
	writable = yes
	path = /NW-DATA
	force directory mode = 770
	force create mode = 660
	comment = 
	valid users = april,david
	available = yes

[DATA]
	comment = 
	writable = yes
	public = yes
	path = /NW-DATA/DATA
	available = yes

[FILES]
	comment = 
	writable = yes
	public = yes
	path = /NW-DATA/DATA/FILES
	available = yes

[HARDWARE]
	comment = 
	writable = yes
	public = yes
	path = /NW-DATA/DATA/HARDWARE
	available = yes

[SERVER]
	comment = 
	writable = yes
	public = yes
	path = /NW-DATA/DATA/SERVER
	available = yes

[SOFTWARE]
	comment = 
	writable = yes
	public = yes
	path = /NW-DATA/DATA/SOFTWARE
	available = yes

[USERS]
	comment = 
	writable = yes
	public = yes
	path = /NW-DATA/DATA/USERS
	available = yes

[Woodworking]
	comment = 
	writable = yes
	public = yes
	path = /NW-DATA/DATA/FILES/Woodworking
	available = yes

[Web Sites]
	comment = 
	writable = yes
	public = yes
	path = /NW-DATA/DATA/FILES/Web Sites
	available = yes
Really, the only folder I want to share (with all sub-folders getting the same RW permissions) is the /NW-DATA folder.  Everything on the list below that is a sub-folder of either /NW-DATA, or /DATA, or something below /DATA.

I do have a few questions about the basics -- I understand that the "#" in the first column makes it a comment.  Does the ";" do the same thing (comment), or is that a recognized part of the command?

All help will be greatly appreciated.  

THANK YOU,
David Labens
San Antonio, TX

---

### Post by albinootje on 2009-01-05
> **adlabens said:**
>  I do have a few questions about the basics -- I understand that the "#" in the first column makes it a comment.  Does the ";" do the same thing (comment), or is that a recognized part of the command?


Yes, the ";" is used in /etc/samba/smb.conf and has the same function as "#".

I strongly suggest that you test accessing your shares on the Ubuntu box itself first with smbclient.

Instructions here :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

For example, check your samba config syntax :
```

testparm

```
Test using a share on your Ubuntu box :
```

smbclient //localhost/NWDATA -U david

```
Please post any errors. GL!

---

### Post by adlabens on 2009-01-05
albinootje,

I can access the folders from PuTTY, but only if I use Sudo to get my admin rights.  That kinda tells me that I'm not getting it shared properly, at least not with the proper rights.  

Secondly, almost everything I'm doing on the server is CLI from PuTTY on my WinXP Pro desktop.  The server has no desktop installed, and I don't want it installed - unless there's just no way around it.  All attempts detailed below are via PuTTY from my WinXP Pro Desktop.

That said, here's my first attempt:
> 
david@RCH-SERVER:~$ smbclient //localhost/NW-DATA -U david
Enter david's password:
Domain=[RCH-SERVER] OS=[Unix] Server=[Samba 3.2.3]
**tree connect failed: NT_STATUS_BAD_NETWORK_NAME**
david@RCH-SERVER:~$

So, here's my second attempt:

> 
david@RCH-SERVER:~$ smbclient //RCH-SERVER/NW-DATA -U david
Enter david's password:
Domain=[RCH-SERVER] OS=[Unix] Server=[Samba 3.2.3]
**tree connect failed: NT_STATUS_BAD_NETWORK_NAME**
david@RCH-SERVER:~$

Then, I tried it with Sudo:
> 
david@RCH-SERVER:~$ sudo smbclient //RCH-SERVER/NW-DATA -U david
[sudo] password for david:
Enter david's password:
Domain=[RCH-SERVER] OS=[Unix] Server=[Samba 3.2.3]
**tree connect failed: NT_STATUS_BAD_NETWORK_NAME**
david@RCH-SERVER:~$

I'm seeing a pattern of: **tree connect failed: NT_STATUS_BAD_NETWORK_NAME** - which leads me to believe that I'm either doing something consistently wrong, or there's something else wrong that I need to address.

(Edit: I got the same errors when executing the commands from the CLI directly on the server - using the keyboard & monitor on the server box instead of PuTTY from my WinXP Pro desktop.)

Let me also add that the RAID5 array was actually created in OpenSuSE, and I had it shared and working just fine.  But, I figured out that I don't want to use OpenSuSE long-term, so I pulled out the OS HDD, & inserted a blank one, & installed Ubuntu 8.10 Server on it, got the RAID5 array mounted and I can now see everything on it using PuTTY from the root login (so I know the data is still there).  I'm not sure any of this OS changeover matters, but at least that's the info.

THANK YOU,
David Labens
San Antonio, TX

---

### Post by adlabens on 2009-01-05
I guess I didn't understand the "testparm" instruction, but I do now!

Here's the output from running "testparm":

> david@RCH-SERVER:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[homes]"
Processing section "[share]"
[B]WARNING: No path in service share - making it unavailable!
NOTE: Service share is flagged unavailable.[/B]
Processing section "[NWDATA]"
Processing section "[DATA]"
Processing section "[FILES]"
Processing section "[HARDWARE]"
Processing section "[SERVER]"
Processing section "[SOFTWARE]"
Processing section "[USERS]"
Processing section "[Woodworking]"
Processing section "[Web Sites]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = RCH-WORKGROUP
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        force group = admin
        delete readonly = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[homes]

[share]
        force create mode = 0660
        force directory mode = 0770
        available = No

[NWDATA]
        path = /NW-DATA
        valid users = april, david
        read only = No
        force create mode = 0660
        force directory mode = 0770

[DATA]
        path = /NW-DATA/DATA
        read only = No
        guest ok = Yes

[FILES]
        path = /NW-DATA/DATA/FILES
        read only = No
        guest ok = Yes

[HARDWARE]
        path = /NW-DATA/DATA/HARDWARE
        read only = No
        guest ok = Yes

[SERVER]
        path = /NW-DATA/DATA/SERVER
        read only = No
        guest ok = Yes

[SOFTWARE]
        path = /NW-DATA/DATA/SOFTWARE
        read only = No
        guest ok = Yes

[USERS]
        path = /NW-DATA/DATA/USERS
        read only = No
        guest ok = Yes

[Woodworking]
        path = /NW-DATA/DATA/FILES/Woodworking
        read only = No
        guest ok = Yes

[Web Sites]
        path = /NW-DATA/DATA/FILES/Web Sites
        read only = No
        guest ok = Yes
david@RCH-SERVER:~$


I'm thinking that the message: [B]WARNING: No path in service share - making it unavailable!
NOTE: Service share is flagged unavailable.[/B] has SOMETHING to do with the problem!!!

---

### Post by albinootje on 2009-01-05
> **adlabens said:**
> 
I'm seeing a pattern of: **tree connect failed: NT_STATUS_BAD_NETWORK_NAME** - which leads me to believe that I'm either doing something consistently wrong, or there's something else wrong that I need to address.


Please try smbclient again with the share name NWDATA instead of NW-DATA.

---

### Post by adlabens on 2009-01-05
david@RCH-SERVER:~$ smbclient //RCH-SERVER/NWDATA -U david
Enter david's password:
Domain=[RCH-SERVER] OS=[Unix] Server=[Samba 3.2.3]
smb: \> dir
NT_STATUS_NETWORK_ACCESS_DENIED listing \*

                0 blocks of size 0. 61680 blocks available
smb: \> cd ..
smb: \> cd /NWDATA
cd \NWDATA\: NT_STATUS_NETWORK_ACCESS_DENIED
smb: \>

---

### Post by adlabens on 2009-01-05
albinootje (& anyone else reading this):

I'm getting ready to head off to work (11:15 am to 8 pm, CST), to climb telephone poles and save the world from bad phone service and bad DSL service!  So, I won't be able to try anything again until this evening, but will promptly address any postings provided in the meantime.  

In retrospect, I COULD reconnect the OpenSuSE HDD, boot the server, and read/copy the smb.conf file, to see where THAT one (OpenSuSE) worked and THIS one (Ubuntu) does not.  I'm guessing that Samba is Samba regardless of the OS environment, so that might just hold the clue.  I'll have to do that when I return from the day's employment.

I REALLY APPRECIATE ALL THE HELP!

Thank you,
David Labens
San Antonio, TX

---

### Post by albinootje on 2009-01-05
> **adlabens said:**
> david@RCH-SERVER:~$ smbclient //RCH-SERVER/NWDATA -U david
Enter david's password:
Domain=[RCH-SERVER] OS=[Unix] Server=[Samba 3.2.3]
smb: \> dir
NT_STATUS_NETWORK_ACCESS_DENIED listing \*

                0 blocks of size 0. 61680 blocks available
smb: \> cd ..
smb: \> cd /NWDATA
cd \NWDATA\: NT_STATUS_NETWORK_ACCESS_DENIED
smb: \>

OK, bit of a delay here. 
I wanted to answer the second part right away, but needed to leave for half an hour.

You need the "valid user" line in your shares if you want to use authentication with username/password.
Also, you mentioned using webmin, did you create samba users with the samba module of webmin ?

Another thing, you changed the "guest user=" into something invalid.
If you're not gonna use anonymous access, then that's fine, but for initial testing without authentication it makes sense to correct that, and restart samba.

---

### Post by adlabens on 2009-01-05
> **albinootje said:**
> You need the "valid user" line in your shares if you want to use authentication with username/password.
Also, you mentioned using webmin, did you create samba users with the samba module of webmin ?

Yes, I used the Samba module of Webmin to create Samba users.  And, they show, in the Samba module of Webmin, to be users and to have RW access.  

[QUOTE=albinootje;6498596Another thing, you changed the "guest user=" into something invalid.
If you're not gonna use anonymous access, then that's fine, but for initial testing without authentication it makes sense to correct that, and restart samba.[/QUOTE]
I understand that.

For both of these, I'll insert the OpenSuSE HDD (just move the cable from Ubuntu HDD to OpenSuSE HDD & reboot) and will copy the smb.conf file to my desktop.  Then, I'll change the data cable back to the Ubuntu HDD & reboot.  This will allow me to see the differences, and to make the changes that you're indicating.  I MIGHT be able to just copy the file onto the Ubunto HDD, but then I'd not learn anything from this!

I appreciate the response, and I'll post another one this evening after I've gotten back home.  

THANK YOU!!!
David Labens
San Antonio, TX

---

### Post by albinootje on 2009-01-05
> **adlabens said:**
>  For both of these, I'll insert the OpenSuSE HDD (just move the cable from Ubuntu HDD to OpenSuSE HDD & reboot) and will copy the smb.conf file to my desktop.  Then, I'll change the data cable back to the Ubuntu HDD & reboot. 

Samba is available for Linux but also other non-Linux Operating Systems.
So the /etc/samba/smb.conf of your OpenSUSE should be perfect to compare with. :) GL!

---

### Post by adlabens on 2009-01-06
First, albinootje, let me say "THANK YOU" for your assistance.  You have enabled me to overcome this hump I've been having with respect to getting the Ubuntu 8.10 Server to work with the same capacity that I had working with OpenSuSE.  Now that I have access to my data in Ubuntu, I can wipe out the OpenSuSE HDD and do a fresh install of Ubuntu on it - so that I can better learn what I've done.  And, I'm confident that the data will stay secure, at least long enough for me to start working on the next level.

I did take the OpenSuSE smb.conf file and studied it, side-by-side with the Ubuntu copy.  There were some differences.  While I definitely don't understand the differences, I was able to copy a few of the sections from the OpenSuSE version to the Ubuntu version, changing the file paths accordingly (I had not given the exact same mount point [one had a hyphen & the other had an underscore] to both versions, so I made that adjustment.  Then, I restarted Samba and rebooted my desktop, and suddenly the stars are aligned and I've got access to all the files while using the Ubuntu HDD.  I'm definitely keeping an external version of the smb.conf file, just in case!!!

Like I said, I am very much unsure what some of the entries are, how they work, or why they are needed.  I HATE being unknowledgeable in an area that can have such an impact on our daily lives.  So, I'm probably going to start looking for a good reference to explain how to manually write a smb.conf file from scratch.  I have looked at the [samba.org]("http://us3.samba.org/samba/") web pages detailing their Official HOWTO and their By Example references.  Obviously, I have yet another lifetime of learning ahead of me (this 50 year old ain't going nowhere anytime soon! - well, maybe vacation, but I'm planning on being around at least another 50!).

So, I'm wondering if you might have some suggestions for good resources regarding Samba enlightenment - not just websites, but also any good instructive books?

Again, your guidance has been instrumental in my ability to access our data using Ubuntu even tho it was created in OpenSuSE, and I really appreciate it!

Thank you VERY much!
David Labens
San Antonio, TX

---

### Post by albinootje on 2009-01-06
> **adlabens said:**
>  So, I'm wondering if you might have some suggestions for good resources regarding Samba enlightenment - not just websites, but also any good instructive books? 

Great you have it working well now! :)

If you feel like playing around, see comment #18 here :
[http://ubuntuforums.org/showthread.php?p=6501492#post6501492](http://ubuntuforums.org/showthread.php?p=6501492#post6501492)

There are a few GUI configuration applications for Samba.
There's Swat from the Samba project, but that needs a root password to make changes afair.
Fedora Linux had the "system-config-samba" which is available for Ubuntu too, it looks pretty good.

Concerning books : 
O'Reilly has at least two Samba books,
[http://oreilly.com/catalog/samba/chapter/book/index.html](http://oreilly.com/catalog/samba/chapter/book/index.html)
[http://oreilly.com/catalog/samba2/book/toc.html](http://oreilly.com/catalog/samba2/book/toc.html)
Both a little bit dated, but probably still usuable with Samba 3.x

---

