---
title: "Samba question..."
date: 2006-03-25
forum: Server Platforms
---

### Post by xmastree on 2006-03-25
Well, I've searched, but I'm stuck. :confused: 

As far as I can tell, I have samba configured and running. My question is what am I supposed to do at the XP end to see the shared folder on my ubuntu machine?
I've tried the 'add new network place', and browsing for it, but all I can see from the XP box is the XP box itself...

Here's my smb.conf, my changes in red:
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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = [COLOR="Red"]cginternet[/COLOR]

# server string is the equivalent of the NT Description field
   server string = %h [COLOR="Red"]homeserver[/COLOR] (Samba, Ubuntu)

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
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

   guest account = nobody
   invalid users = root

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
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[COLOR="Red"][music]
   comment = Music
   path = /mnt/sata/mp3
   read only = no
   guest ok = yes[/COLOR]

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

The boxes are connected, I can access the net from XP via the ubuntu box, so it's not a cable problem.

---

### Post by odin on 2006-03-25
I'm also trying to set it up and have a question that might be also your problem. Do I have to install a samba client in every XP machine I want to share folders with?

Thank's in advanced

---

### Post by LordHunter317 on 2006-03-25
Did you try connecting by IP?  What happened when you did.  Without error messages or more details, it's impossible to help.

---

### Post by xmastree on 2006-03-25
[QUOTE=LordHunter317]Did you try connecting by IP?  What happened when you did.  Without error messages or more details, it's impossible to help.[/QUOTE]
I'm not sure what that means. The samba server is running, but when I try to browse the network from the XP box I can't see it. No error message, it's as if it's not there.

---

### Post by lbates35476 on 2006-03-25
You either need to map a drive to the server share or create a Network shortcut.

To map a drive: 

Open command prompt

enter 
net use f: \\<server_string>\music

after that drive f: should point to your music.

Note: You may want a short server string in smb.conf

or you can 
- double click My Network Places
- click Add Network Place
- click next
- Choose another network location
- Enter \\<server_string>\music
- click next
- give you shortcut a name (or accept the one suggested)

Folder should open showing you contents of music folder on your server

Hope information helps.

---

### Post by LordHunter317 on 2006-03-25
As in, did you try typing \\192.0.0.1\share  in the Run box or the address bar of explorer to load the share?  If not, you haven't verified there is a problem yet?

Replacing 192.0.0.1 with the actual IP, of course.

---

### Post by xmastree on 2006-03-25
If I type \\192.168.0.100\music in the network address field of the Add Network Place Wizard, it crashes.
[ATTACH]7625[/ATTACH]

If I type \\homeserver\music it says it's not valid.
[ATTACH]7626[/ATTACH]

](*,) 

I can ping 192.168.0.100 from the windows box. The ubuntu box is running the dhcp, from which the Windows box gets its ip.

---

### Post by Iowan on 2006-03-26
My Samba server uses the **hostname** instead of the server string.  I was of the opinion that the server string line is only a description.

BTW, I don't remember setting the "netbiosname = " parameter, but I suppose that's a possibility.

---

### Post by xmastree on 2006-03-27
[QUOTE=Iowan]My Samba server uses the **hostname** instead of the server string.  I was of the opinion that the server string line is only a description.

BTW, I don't remember setting the "netbiosname = " parameter, but I suppose that's a possibility.[/QUOTE]
Well, I tried putting netbiosname in there, but that didnt' work either.

I give up.

I'll copy the files to another disk, and move them physically. It's easier.

---

### Post by Iowan on 2006-03-27
My only other question would be if the Windows box is set to use **cginternet** as a workgroup.  

I suspect you've already got the files moved by now...

---

### Post by wylie348 on 2006-03-27
Some other possibilities that have worked for me is to re-install both smbfs and samba (synaptic) and when I refer to my shares on the network I often use:
\\\\192.168.0.100\\sharename

For some reason this work better for me?

Regardless, try using the mount option:

mount -t smbfs ...

the mount --help command includes the options...
:rolleyes:

---

### Post by webfoot0 on 2006-03-27
What happens if in a command window on the XP box you type:
net view \\192.168.xxx.xxx substitute numbers for your ubuntu box1

Keith

---

### Post by xmastree on 2006-03-27
[QUOTE=webfoot0]What happens if in a command window on the XP box you type:
net view \\192.168.xxx.xxx substitute numbers for your ubuntu box1
[/QUOTE]

System error 53 has occurred. :rolleyes: 

The network path was not found.


The windows' workgroup is cginternet. If I try to browse the network, it can only see itself in the share.

I need to move this computer now, but I really would like to figure this out. in all my years messing with linux (about 5 n all, on and off) I have *never* succeeded with file sharing.

Should I sacrifice a goat or something? Or a maybe haddock, to please the great penguin god...

---

### Post by Buffalo Soldier on 2006-03-28
*** assumption: the username that you use to logon into your ubuntu = **john**

I was having a hard time configuring samba. But I finally manage to get it. Perhaps this might work for you: [list]
[*] open/create a file smbusers:
```
sudo gedit /etc/samba/smbusers
```

[*] Insert the following line into the new file:
```
john = "network username"
```

[*] Run this command at command line:
```
sudo smbpasswd -a john
```
After entering the usual sudo password, you will be asked to enter a new password (twice). This will be the password Windows user need to login to enter to your shared folder. Assume we entered **12345** as password.


[*] Edit your smb.conf file:[list]
[*] ```
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = user
```into
```

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = user [color=red]username map = /etc/samba/smbusers[/color]
```
   
[*] ```
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700
```into
```
[color=red]**;**[/color][homes]
[color=red]**;**[/color]   comment = Home Directories
[color=red]**;**[/color]   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
[color=red]**;**[/color]   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
[color=red]**;**[/color]   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
[color=red]**;**[/color]   directory mask = 0700
```

[*] ```
[music]
   comment = Music
   path = /mnt/sata/mp3
   read only = no
   guest ok = yes
```into
```
[music]
   comment = Music
   path = /mnt/sata/mp3
   [color=red]public = yes
   writable = no
   valid users = system_username1 system_username2
   create mask = 0700
   directory mask = 0700
   force user = nobody
   force group = nogroup[/color]
```[/list]

[*] test your samba configuration
```
sudo testparm
```

[*] restart samba
```
sudo /etc/init.d/samba restart
```

[*] Restart the Windows XP computer.


[*] When trying to browse to Ubuntu shared folder from Windows XP computer, you will be asked for authentication, use:[list]
[*]  username: john
[*]  password: 12345[/list]
[/list]

---

### Post by webfoot0 on 2006-03-28
[QUOTE=xmastree]System error 53 has occurred. :rolleyes: 

The network path was not found.


The windows' workgroup is cginternet. If I try to browse the network, it can only see itself in the share.

I need to move this computer now, but I really would like to figure this out. in all my years messing with linux (about 5 n all, on and off) I have *never* succeeded with file sharing.

Should I sacrifice a goat or something? Or a maybe haddock, to please the great penguin god...[/QUOTE]

System error 53 sounds as though samba is not running - windows can find no sharing on the box - have you run testparm against your smb.conf this will allow errors to be found.  If there are errors in smb.conf samba will not start.

The following about testparm copied from elsewhere:
==========================================
Test Your Config File with testparm
It's important to validate the contents of the smb.conf file using the testparm program. If testparm runs correctly, it will list the loaded services. If not, it will give an error message. Make sure it runs correctly and that the services look reasonable before proceeding. Enter the command: 

	root#  testparm /etc/samba/smb.conf
	
Testparm will parse your configuration file and report any unknown parameters or incorrect syntax. It also performs a check for common misconfigurations and will issue a warning if one is found. 

Always run testparm again whenever the smb.conf file is changed! 

The smb.conf file is constantly checked by the Samba daemons smbd and every instance of itself that it spawns, nmbd and winbindd. It is good practice to keep this file as small as possible. Many administrators prefer to document Samba configuration settings and thus the need to keep this file small goes against good documentation wisdom. One solution that may be adopted is to do all documentation and configuration in a file that has another name, such as smb.conf.master. The testparm utility can be used to generate a fully optimized smb.conf file from this master configuration and documtenation file as shown here: 
=================================
hope that helps

Keith

---

### Post by xmastree on 2006-03-28
[QUOTE=webfoot0]System error 53 sounds as though samba is not running - windows can find no sharing on the box[/QUOTE]That's right. It's as if the server isn't running at all. testparm seems to suggest that all's well.
Buffalo, your help is appreciated, but since the Windows box can't even see the ubuntu box in the first place, I don't get as far as entering any passwords.

Something has just occured to me, do I need to install any additional protocol in on the Windows box? (it's now a '98 box, since the XP is in service now, and I'm using the one it replaced. I don't need to connect them, but I *want* to, just so that I know how in future).
I have TCP/IP, IPX/SPX, and Net BIOS (running on IPX) installed. Usually the file and print sharing is only bound to NetBIOS, but I've enabled it on all three, just in case.

Am I missing something here? I seem to remember seeing Samba is SMB compatible. Is SMB a protocol or something? Do I need to install that?

I'm actually clueless when it comes to networking. I've bluffed my way through so far, learning by trying and doing but without actually knowing what I'm doing. In fact, I don't even know the difference between a host and a domain.

---

### Post by Iowan on 2006-03-28
Springboarding from **webfoot0's** post, does **ps aux** show smbd and/or nmbd running?

I didn't have to install anything on my XP or win98 boxes to allow them to see the server.  I DID have to tell my win98 box to log onto Windows network.

---

### Post by Buffalo Soldier on 2006-03-28
xmastree,

just doing what i can to help :) cause i was having kind of a same problem earlier and I know how frustrating it feels. The only different about my problem was my Ubuntu box can see my WinXP box, but my WinXP box cannot see my Ubuntu box.

It seems that Samba "hides" my Ubuntu box from my WinXP box if I do not properly set the security/authentication settings.

it wasn't until i read this [post](http://ubuntuforums.org/showpost.php?p=607885&postcount=5) that I finally got to understand samba.

---

### Post by LordHunter317 on 2006-03-28
[QUOTE=xmastree]Something has just occured to me, do I need to install any additional protocol in on the Windows box?[/quote]No, in fact, if oyu did, remove them.  You're making the issue wirse.

>  (it's now a '98 box, since the XP is in service now, and I'm using the one it replaced. I don't need to connect them, but I *want* to, just so that I know how in future).
I have TCP/IP, IPX/SPX, and Net BIOS (running on IPX) installed. Usually the file and print sharing is only bound to NetBIOS, but I've enabled it on all three, just in case.You likely don't have NetBIOS over TCP properly mapped anymore.  I'd bet money it's not listening for TCP connections.

---

### Post by 1oki on 2006-03-28
I am using samba as a PDC and with that I have the local samba share maped as a users network drive when logged onto the PDC. Here is my samba config file:

```

[global]
   workgroup = WRS-DOMAIN
   netbios name = SERVER1
   server string = %h server (Samba, Ubuntu)

   
   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS
   
   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = no


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no

[allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes


```

You may have to add permissions to your "Music" section. Your music section is much like my allusers. Also, if you are mounting the share onto your linux box, try installing "smbfs" (apt-get install smbfs). This is a mountable Linux smb filesystem used only by Linux. Without it, Linux wont see the samba share... I hope it helps! 8)

---

### Post by Kosh42 on 2006-03-28
I am having an almost identical problem to xmastree... Tried various things and nothing...

In XP (x64), I can see the Ubuntu box under the workgroup, but when I click, I get:

[IMG]http://homepages.nildram.co.uk/~kosh42/ubuntu/hmm.png[/IMG]

I can ping it, but net view //ip gives me no joy...

I can't see XP from Ubuntu, though...

ps aux gives me:
```
root     26052  0.0  0.8   6704  1956 ?        Ss   23:19   0:00 /usr/sbin/nmbd
root     26054  0.0  1.1   8976  2676 ?        Ss   23:19   0:00 /usr/sbin/smbd
root     26055  0.0  1.1   8976  2664 ?        S    23:19   0:00 /usr/sbin/smbd

```

My samba.conf is:

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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOME

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
   security = user
   username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

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
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

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

Any ideas?

---

### Post by xmastree on 2006-03-28
[QUOTE=LordHunter317]You likely don't have NetBIOS over TCP properly mapped anymore.[/QUOTE]Hmm...:-k 
The option for NetBIOS over TCP is greyed out. It's only available for IPX.

[QUOTE=Iowan]**ps aux** show smbd and/or nmbd running?
[/QUOTE]
```
chris@xmastree:~$ ps aux | grep smb
root     10099  0.0  0.2   8832  2628 ?        Ss   Mar28   0:00 /usr/sbin/smbd -D
root     10100  0.0  0.2   8832  2616 ?        S    Mar28   0:00 /usr/sbin/smbd -D
chris@xmastree:~$ ps aux | grep nmb
root     10097  0.0  0.1   6652  2020 ?        Ss   Mar28   0:00 /usr/sbin/nmbd -D

```

---

### Post by xmastree on 2006-03-30
I just had a thought... :-k
This ubuntu box has two NICs. One for the incoming internet conenction, and one for the LAN. Do I need to tell samba which one to use?

---

### Post by Iowan on 2006-03-31
[http://hr.uoregon.edu/davidrl/samba.html]("http://hr.uoregon.edu/davidrl/samba.html")> interfaces = 192.168.0.0/255.255.255.0 127.0.0.1
bind interfaces only = Yes
It's useful to limit the interfaces on which Samba will run if you have a multi-homed (more than one IP address) server. A common mistake is to set the interfaces line to the specific IP address of the box, when it is actually the IP subnet that your interface is on that you want to use. You'll have to specify "bind interfaces only = Yes" for this to work, however. 

---

### Post by s7eam on 2006-03-31
I assume you've allready created a username with the following command:
```
sudo smbpasswd -a your_smb_username
```
Now you've created a username to use with samba. 
Don't forget the password. ;) 

Next edit or create the following file:
```
sudo nano /etc/samba/smbusers
```
The file /etc/samba/**smbusers** should contain the following line:
```
your_smb_username = "network username"
```
Save it and exit.

Now edit smb.conf
```
sudo nano /etc/samba/smb.conf
```

Directly under [global] put the following lines:
```
hosts allow = 192.168.x. 127.
```

**Note:** x in the ip address above stands for your subnet number. Mark even the dots (.) after IPs. You don't have to type whole address!

Under #### Authentication #### section type or change to following lines:
```
security = user
username map = /etc/samba/smbusers
```

Don't type smb_username map = /etc..  -  it should be exactly as it appear above!!
The other guy who posted his smb.conf file is ok on these lines though. I just mention it in case. ;)

Now under [homes] type or create these lines:
```

[homes]
comment = Home Directories
browseable = yes
valid users = your_smb_username
path = /home/themap

```

Now issue commend.
```
sudo testparm 
```
to see that smb.conf file syntax is OK. It it is, the smb.conf content should appear.

Restart samba:
```
sudo /etc/init.d/samba restart
```

Before you test it on your Windows machinge test it right now on your Ubuntu server with this command:
```
sudo mount -t smbfs -o username=your_smb_usr,password=your_smb_pass //localhost/homes /mnt/test
```

On your Windows cmd write the following:
```
net use x: \\ip_to_ubuntu_serv\homes
```

P.S
Check that your firewall has opened ports for samba.
Good Luck!

---

### Post by Kosh42 on 2006-03-31
[QUOTE=s7eam]P.S
Check that your firewall has opened ports for samba.
Good Luck![/QUOTE]

What are the ports? Wondering if the firewall built into my router modem may be to blame...

---

### Post by s7eam on 2006-03-31
[QUOTE=Kosh42]What are the ports? Wondering if the firewall built into my router modem may be to blame...[/QUOTE]

Your modem should not be problem as long as you first try with **mount -t** command as I described above. If mounting samba from the local machine goes than it should work fine from Windows also.

To see what ports samba uses use command:

```
grep netbios /etc/services
```

---

### Post by Kosh42 on 2006-04-01
mount -t works a treat on localhost...

[QUOTE=s7eam]```
grep netbios /etc/services
```[/QUOTE]

This gives me:

```
netbios-ns      137/tcp                         # NETBIOS Name Service
netbios-ns      137/udp
netbios-dgm     138/tcp                         # NETBIOS Datagram Service
netbios-dgm     138/udp
netbios-ssn     139/tcp                         # NETBIOS session service

```

Windows built in firewall doesn't let in tcp and udp on every port... Only one or the other... May tyr that out....

---

### Post by xmastree on 2006-04-01
Wouldn't it be nice if it just worked, like most other things in ubuntu? I read through s7eam's post, and thought what the...? eh...?
> Note: x in the ip address above stands for your subnet number. Mark even the dots (.) after IPs. You don't have to type whole address!I cant' work out what that means. subnet number? the subnet is 255.255.255.0
How would that fit into 192.168.x.127?
I'm too tired to try this now anyway. Gonna have a beer instead.

See post #13:
> In all my years messing with linux (about 5 in all, on and off) I have never succeeded with file sharing.
At least I haven't spoiled my record. It can't be done. You guys who are doing it must be using some kind of magic. :rolleyes:

---

### Post by s7eam on 2006-04-01
[QUOTE=xmastree]Wouldn't it be nice if it just worked, like most other things in ubuntu? I read through s7eam's post, and thought what the...? eh...?
I cant' work out what that means. subnet number? the subnet is 255.255.255.0
How would that fit into 192.168.x.127?
I'm too tired to try this now anyway. Gonna have a beer instead.

See post #13:

At least I haven't spoiled my record. It can't be done. You guys who are doing it must be using some kind of magic. :rolleyes:[/QUOTE]

Sorry I'm very bad at explaining stuff I see now. 

Your network consists of a subnet number. That means if you have 1 network in your home this is probably **192.168.1.255** there 255 could be any number between 0 and 255. If you have 2 networks than your IP probably begins with **192.168.2.** but You decide what IP address you have on your computer so this is no rule just recommendation.

My "x" above means that you should write your subnet number instead of "x". Either **192.168.1.** or **192.168.2.** NOT 192.168.x.   

DONT'T write **127.** directly after 192.168.1. you MUST have a space in between! 127. is for your loopback address (Ubuntu box address).

The dot (**.**) after the number 127 and after 192.168.1 means that it could be any IP number beginning with 127 or 192. Don't worry IPs beginning with 127 could just be your local and **not** outside of your network. The same goes for 168 IPs.


**Kosh42:** That's right. These are the ports for samba, from 137 - 139.

---

### Post by Kosh42 on 2006-04-03
Sucess!!! Needed a clean install as I managed to kill the file system (power down during boot-up)...

From there I used the GUI in Gnome. In system > ???? > Shared Folders. It installed samba on the way, then I just set the folder to share and its properties, and selected the workgroup name in the general setting bit.

I could then get a log-in prompt from the Win XP machine and just needed to smbpasswd -a to set a user and password and it worked like a dream...

---

### Post by mccyron on 2006-04-06
The 2 computers are in the same workgroup/domain and subnet I assume?
Samba shares can take their time being "discovered" in the Windows network environment. You can force the issue by typing in the NETBIOS name and share in the "Address" bar that you've set up in your smb.conf...Hmmm...I can't seem to find your Samba servers's NETBIOS name in the smb.conf. (It would help if you'd delete ALL the lines begining with # when you post your smb.conf)  Windows expects each computer to have a unique "name" and this is what the network browser displays.  

I'm still learning Ubuntu too but this is what I've learned from other Linux/BSD Samba servers.

Let me know what you discover.

Thanks

---

### Post by nekr0z on 2006-05-09
Well I had the same situation here, and I finally managed it to work, so now I do have an X: drive on my Windows notebook connected to a share on the Ubuntu box. But I still cannot access any share on that Ubuntu machine via Network Neighbourhood in Windows. Is there any way to do that?

---

