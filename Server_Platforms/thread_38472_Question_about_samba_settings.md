---
title: "Question about samba settings"
date: 2005-05-31
forum: Server Platforms
---

### Post by oafdaloaf on 2005-05-31
I'm rather new to this, so I'm sorry if I ask a stupid question.  

I've followed the howto listed at ubuntuguide.org, but I'm still having problems setting up my ubuntu system to share directories with my XP Pro machine.

I'm attaching my smb.conf below: 

[HTML]oafdaloaf@draal:/etc/samba $ cat smb.conf
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
# "testparm" to check that you have not many any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = BABCOM
   name = draal

# server string is the equivalent of the NT Description field
   server string = %h (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = 192.168.2.91

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
;   passdb backend = tdbsam guest

;   obey pam restrictions = yes

   guest account = nobody
;   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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

[audio]
comment = Music
path = /audio
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nobody
guest ok = yes

[video]
comment = Video
path = /video
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nobody
guest ok = yes
oafdaloaf@draal:/etc/samba $[/HTML]

My XP system asks for my username and password, and my samba username/password combination that i'm using is the same as the login username/password.  I've even tried logging onto it as //server/username, as it suggests, but to no avail.

I know I'm missing something stupid here.  Anyone care to help?

Thanks in advance!

---

### Post by clb137 on 2005-05-31
Hi, 

Can you tell me how how you added users for Samba?

did you follow the guide [http://www.ubuntuguide.org/#addeditdeletenetworkusers](http://www.ubuntuguide.org/#addeditdeletenetworkusers)

if you did there should be no problem, if you add users to your samba file another way can you please let me know


thanks 

clinton

---

### Post by oafdaloaf on 2005-05-31
[QUOTE=clb137]Hi, 

Can you tell me how how you added users for Samba?

did you follow the guide [http://www.ubuntuguide.org/#addeditdeletenetworkusers](http://www.ubuntuguide.org/#addeditdeletenetworkusers)

if you did there should be no problem, if you add users to your samba file another way can you please let me know


thanks 

clinton[/QUOTE]

Yes I have (only one user.)  Still not working.

Any other ideas or things I can check?

~oaf

---

### Post by LordHunter317 on 2005-05-31
The fact you're doing security=share by default worries me.  I'm also not sure "name" is a valid parameter and have to wonder if Samba's even loading correctly.

Forcing the user and group to the guest account like that is a bad idea.  Cut that out.  Use "guest only = yes" instead, which handles the authentication properly.  If you do that, everything should just work, unless you added a Samba account for the nobody user.  If you did, delete it.  That will break tons of things.

Your create and directory masks are dangerous as well if you'll ever have anyone you don't trust accessing the shares.  You probably (definetely) want to change them.

A better idea for you might be to explain what you want to share, and then someone will tell you how to do it correctly.  Samba's quite a beast to setup, and it's very easy to do it wrong.

---

### Post by oafdaloaf on 2005-05-31
> **LordHunter317]The fact you're doing security=share by default worries me.  I'm also not sure "name" is a valid parameter and have to wonder if Samba's even loading correctly.[/QUOTE]

From [http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare:](http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare:)

[HTML]4. Find this line

...
 said:**
> 

That's why I did it.  I'll change it back though.


[QUOTE=LordHunter317]Forcing the user and group to the guest account like that is a bad idea.  Cut that out.  Use "guest only = yes" instead, which handles the authentication properly.  If you do that, everything should just work, unless you added a Samba account for the nobody user.  If you did, delete it.  That will break tons of things.

Where should I do this?  Under the [audio] and [video] sections?

[QUOTE=LordHunter317]Your create and directory masks are dangerous as well if you'll ever have anyone you don't trust accessing the shares.  You probably (definetely) want to change them.[/QUOTE]

I don't anticipate anyone accessing them other than myself, as they're behind a hardware and software firewall independent of the system.

[QUOTE=LordHunter317]A better idea for you might be to explain what you want to share, and then someone will tell you how to do it correctly.  Samba's quite a beast to setup, and it's very easy to do it wrong.[/QUOTE]

I just want to have my music and video files available to other computers in my house, which I'm in the process of networking.

Thanks for the constructive criticism.  I know I have a lot to learn.  As a high school teacher I understand the value of gently coaxing people along in unfamiliar territory to get them to understand new concepts, and I appreciate all the help I get.

~oaf

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=oafdaloaf]That's why I did it.  I'll change it back though.[/quote]For the record, anyone who tells you to use security=share probably doesn't understand Samba security.  

> Where should I do this?  Under the [audio] and [video] sections?Yes.  

Also, what Samba accounts did you add and how did you add them?

After you make any changes to the Samba configuration, make sure to restart it with:```
sudo /etc/init.d/samba restart
```Also, as it is setup now, the nobody user will need filesystem permissions to the files/directories in question.

---

### Post by oafdaloaf on 2005-06-01
[QUOTE=LordHunter317]For the record, anyone who tells you to use security=share probably doesn't understand Samba security. [/QUOTE]

Is there another site you'd refer me to other than ubuntuguide.org, since it seems to have erroneous information?

[QUOTE=LordHunter317]Also, what Samba accounts did you add and how did you add them?[/QUOTE]

Again, from [http://ubuntuguide.org/#addeditdeletenetworkusers](http://ubuntuguide.org/#addeditdeletenetworkusers) 

[HTML]To add network user

   1. Read How to add/edit/delete system users?

   2. smbpasswd -a oafdaloaf
       sudo gedit /etc/samba/smbusers

   3. Insert the following line into the new file

oafdaloaf = "oafdaloaf"[/HTML]

oafdaloaf is both the samba username and the linux account username I'm using.    As far as I know that's the only smbuser I have on the system.  It's the only linux account I have made on the system.  Is there another way I need to do this?

[QUOTE=LordHunter317]After you make any changes to the Samba configuration, make sure to restart it with:```
sudo /etc/init.d/samba restart
```Also, as it is setup now, the nobody user will need filesystem permissions to the files/directories in question.[/QUOTE]

I don't know what the nobody user is.  Is this a user I have to add to smbusers and if so, do I set it up to my linux account or a "nobody" linux account?

Sorry for all the stupid questions
~oaf

---

### Post by LordHunter317 on 2005-06-01
[QUOTE=oafdaloaf]Is there another site you'd refer me to other than ubuntuguide.org, since it seems to have erroneous information?[/quote]The information isn't so much erroneous as just as a bad way of doing things.  I'm sure it works, if everything's setup correctly.  But security=share is just a bad idea.

The offical samba HOWTO on it's site is dense, but good.  You just have to sit down and read through the proper sections and understand it.


> oafdaloaf is both the samba username and the linux account username I'm using.    As far as I know that's the only smbuser I have on the system.  It's the only linux account I have made on the system.  Is there another way I need to do this?No, what you did was fine, though step 3 is totally unnecessary.

> I don't know what the nobody user is.  Is this a user I have to add to smbusers and if so, do I set it up to my linux account or a "nobody" linux account?It's an account that exists on your system for guest access.  It's part of your base install and you don't need to do anything special for Samba, besides note it as the guest account (which you already have done).    

In theory, just toggling security=user, marking the shares 'guest only' and restarting Samba should provide you access.

---

