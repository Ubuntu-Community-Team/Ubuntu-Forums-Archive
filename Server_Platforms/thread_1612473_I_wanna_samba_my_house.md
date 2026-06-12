---
title: "I wanna samba my house"
date: 2010-11-03
forum: Server Platforms
---

### Post by arnavk007 on 2010-11-03
Ya every one I have one question
could anyone explain to me the use of smbusers in samba
is it like this
If I have a win pc with a user abc then I need to have a user abc with Same passed in both ubuntu and samba or is it something else
is it possible for me to directly share th whole file system or should I share /dev/sda
otherwise I have already set up shares

---

### Post by HermanAB on 2010-11-03
Yes, it is easiest if the usernames and passwords are exactly the same everywhere:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

However, NFS is way easier:
[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

---

### Post by arrrghhh on 2010-11-03
NFS is better, but doesn't work so well with Windows machines.  I think there's some framework you can install that adds NFS support to Windows clients, but OOB Samba is preferred for Windows clients as they don't need anything additional.  I use both, as I have a mixed environment of clients.

---

### Post by CharlesA on 2010-11-03
You are on the right track.

How you set up the shares depends on what you want to do with it.

See here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by Morbius1 on 2010-11-03
>  could anyone explain to me the use of smbusers in sambaAre you talking about /etc/samba/smbusers?
As I remember it ( I think I used it only once ) that's usually used for special access to the server. For example if you want to give remote user "john" root access then you would add a line to /etc/samba/smbusers:
```
root = john
```If this is just a peer-to-peer home network I can't imagine why you would need something like this.
>  If I have a win pc with a user abc then I need to have a user abc with  Same passed in both ubuntu and samba or is it something elseIt's not a requirement that you use the same username and password although it does make thing simpler if Windows is the client because of a design fluke in Windows. Windows passes the logged in user's actual login username and login password automatically when accessing the server. If the server has a username and samba password that matches it then the Windows user is not prompted for authentication. I think this is the origin of the samba myth that all usernames and passwords have to match. The same phenomenon does not happen if the client is another Linux box.
>  is it possible for me to directly share th whole file system or should I share /dev/sdaYou can't share /dev/sda because that's a device not a partition. As for sharing the whole filesystem, I wouldn't do it on a drunken bet. But that's just me. :wink:

---

### Post by arnavk007 on 2010-11-03
thank you everyone
i was able to access my lappie from windows by rightclick then explore
windows asked me for a username and password 
taraa everything works
now will work to accomplish everything else
ajaxplorer will be last thing to do

---

### Post by arrrghhh on 2010-11-03
> **arnavk007 said:**
> ajaxplorer will be last thing to do

Please read their [documentation](http://www.ajaxplorer.info/documentation-3/)... It's pretty straight-forward.

---

### Post by arnavk007 on 2010-11-03
yes but i cant access it
never mind
windoze is constantly asking me for username and password but it is not doing anything
which username and password should i put

---

### Post by CharlesA on 2010-11-03
You need to set the samba password with this:

```
sudo smbpasswd -a *username*
```

---

### Post by arrrghhh on 2010-11-03
> **arnavk007 said:**
> yes but i cant access it
never mind
windoze is constantly asking me for username and password but it is not doing anything
which username and password should i put

Whatever you created for samba...?  You did add a user/pass to samba, yes?

---

### Post by arnavk007 on 2010-11-03
ya

---

### Post by arnavk007 on 2010-11-03
sorry
it is still showing an error any other tip

---

### Post by CharlesA on 2010-11-03
If you are just going to constantly bump the thread, it will be closed, just like your last thread.

---

### Post by Morbius1 on 2010-11-03
Can you post your smb.conf file so we can see how you are set up:
```
testparm -s
```

---

### Post by arnavk007 on 2010-11-03
this is the output

> 
  Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: Change this to the workgroup/NT-domain name your Samba server will part of
Processing section "[homes]"
Processing section "[Everything]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[cdrom]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = home server (Samba, Ubuntu)
    interfaces = eth0
    security = SHARE
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[homes]
    comment = Home Directories
    guest ok = Yes

[Everything]
    comment = everything
    path = /
    read only = No
    create mask = 0777
    directory mask = 0777
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    guest ok = Yes

[cdrom]
    comment = Samba server's CD-ROM
    path = /cdrom
    guest ok = Yes
    locking = No
 

is it ok ??

---

### Post by Morbius1 on 2010-11-03
To start:
>      encrypt passwords = No
Change that to:
```
     encrypt passwords = Yes
```
Then restart samba:
```
sudo service smbd restart
```

---

### Post by arnavk007 on 2010-11-03
is this right
> 

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: Change this to the workgroup/NT-domain name your Samba server will part of
Processing section "[homes]"
Processing section "[Everything]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[cdrom]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = home server (Samba, Ubuntu)
    interfaces = eth0
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[homes]
    comment = Home Directories
    guest ok = Yes

[Everything]
    comment = everything
    path = /
    read only = No
    create mask = 0777
    directory mask = 0777
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    guest ok = Yes

[cdrom]
    comment = Samba server's CD-ROM
    path = /cdrom
    guest ok = Yes
    locking = No




---

### Post by arnavk007 on 2010-11-03
this is my smb.conf

---

### Post by Morbius1 on 2010-11-03
Aside from this error:
> params.c:Parameter() - Ignoring badly formed line in configuration file:  Change this to the workgroup/NT-domain name your Samba server will part  ofWhich you can correct by placing a # sign in front of this line:
```
## Browsing/Identification ###

[COLOR=Blue]**#**[/COLOR]Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
```And the fact that you are allowing guest access not only to everyone's home folder but to the entire filesystem itself you should be good to go.

BTW, This will not allow write access despite the "read only = no":
> [Everything]
comment = everything
path = /
guest ok = yes
read only = no
browseable = yes
create mask = 0777
directory mask = 0777Because "/" has permissions of 755 by default. It needs to be 777 to actually allow a write. I should be banned from this forum for even suggesting it but since you're allowing guest access anyway the damage has already been done.

I have to ask you what is your goal here. If your goal is remote administration this is not the way. There are better ways explained in this forum elsewhere.

---

### Post by CharlesA on 2010-11-03
Hopefully not derailing the thread but:

Morbius1: Is there a difference between "encrypt passwords = yes" and "encrypt passwords = true"

I found that by accident while poking around in my smb.conf file. I probably changed it a while ago and never noticed it until now, as the default smb.conf that is included with Ubuntu has "encrypt passwords = no"

---

### Post by Morbius1 on 2010-11-03
CharlesA, 
Either one works. Samba is fairly flexible when it comes to this sort of thing like:
> writeable
writable> as the default smb.conf that is included with Ubuntu has "encrypt passwords = no"Are you sure about that? That would render file sharing unusable out of the box since even guest access has to be encrypted. I don't remember ever changing that parameter unless I had to rebuild smb.conf from /usr/share/samba/. But I'm getting old an feeble so maybe I just forgot. :)

---

### Post by CharlesA on 2010-11-03
> **Morbius1 said:**
> 
Are you sure about that? That would render file sharing unusable out of the box since even guest access has to be encrypted. I don't remember ever changing that parameter unless I had to rebuild smb.conf from /usr/share/samba/. But I'm getting old an feeble so maybe I just forgot. :)

The smb.conf file I was looking at was in /usr/share/samba/smb.conf.

I just installed samba on a VM to see what smb.conf looked like and "encrypt passwords = true" was there.

Guess that answers that.

Thanks. :)

---

### Post by arnavk007 on 2010-11-04
Morbius this was my earlier thread which got closed cuz of a 'Beeep' you and constant bumping
my motive is to have a Network Attached Device which gives me Network Attached Storage and Printing
works as an mp3 player when i want 
 I have attached a pair of cheapo chinese headphones which i found in my drawer and they are good for the purpose
i also wanted a ps3 server and i have one
i have also installed subsonic but have not tried using it.
Morbius you will not be banned as the thing you were asking me to do is what i want
any tips on making / 0777 as in the cmd the ls -l result is not what i want
i want it to be rwxrwxrwx 

[http://ubuntuforums.org/showthread.php?t=1585441&highlight=network+house](http://ubuntuforums.org/showthread.php?t=1585441&highlight=network+house)

Charles how did you set up a virtual machine so fast 

i am able to see the full everything share but it doesnt open anything else 
if i go to /media/arnav data it still says no permissions

---

### Post by Morbius1 on 2010-11-04
In looking at this and your other post it appears that because of all the responses you got you've got a little bit of this and a little bit of that installed and configured.

You do not need and you should never share your "/" directory. I tried to say that several times - once using sarcasm ( which apparently never works in print ). You do not need and you should never set your "/" directory to 777. It's not clear that you even need the "homes" share enabled - and if you do it should never be set to allow guest access. 

All of this ajax / apache stuff is unnecessary. You can achieve all this with straight Samba. You could probably do the same thing with NFS - but I'm not personally in favor of bolting a foreign networking application on Windows - which has it's own issues to deal with. You need to read the documentation on subsonic to get that working.

> if i go to /media/arnav data it still says no permissions     If you want to access /media/arnav then share /media/arnav - don't go through "/" to get there.

If I were you I would reset smb.conf back to the default and start sharing directories in a more logical manner. To reset smb.conf:
[http://art.ubuntuforums.org/showpost.php?p=9505697&postcount=13](http://art.ubuntuforums.org/showpost.php?p=9505697&postcount=13)

---

### Post by arnavk007 on 2010-11-04
the ajax apache stuff is for access from outside the network.
as far as subsonic is concerned i will look into it.
actually the name of the drive is "arnav data" i am not able to rename it otherwise would have done so.
actually there is a time lag between us
till what time will u be awake
i will try your tip

---

### Post by arnavk007 on 2010-11-05
bumppp
How do i really install ajaxplorer
cant understand their documentation
subsonic installed fine and it works great

---

### Post by arrrghhh on 2010-11-05
> **arnavk007 said:**
> bumppp
How do i really install ajaxplorer
cant understand their documentation
subsonic installed fine and it works great

What do you mean you can't understand it...?  What have you done?  I installed it in like 2 minutes, it was a breeze...

---

### Post by arnavk007 on 2010-11-05
After extracting the zip file to /var/www what to do

---

### Post by arrrghhh on 2010-11-05
> **arnavk007 said:**
> After extracting the zip file to /var/www what to do

Is it in a folder?  It should be.  Browse to that folder on your apache server in your browser...?

---

### Post by arnavk007 on 2010-11-06
> **arrrghhh said:**
> Is it in a folder?  It should be.  Browse to that folder on your apache server in your browser...?


So that means I go to [http://192.168.1.100/ajaxplorer-core-3.0.3/](http://192.168.1.100/ajaxplorer-core-3.0.3/) right 
but from the same machine I get no permissions error
should I try from another machine
btw I have removed the index.HTML file
should I have not done so
even from another machine the same error
i tired of configuring samba

the vista machine can see the mediatomb server on this machine and i can even listen to songs from it.
ajaxplorer is also a PITA for me.
any alternatives for ajaxplorer and samba 
please suggest
i am able to see everything using the vista machine even things not listed in the smb.conf
but am only able to access things on the hdd but cant access the external hdd and folders in it

---

### Post by arnavk007 on 2010-11-07
I am having a problem 
I cannot access the external Hard drives
What should i do
i have also shared my desktop folder and i can read and write to it

---

### Post by arrrghhh on 2010-11-07
Need to add them to samba?  If you don't share at the root, you need to share everything piecemeal.  I share at the root, which isn't recommended - but samba doesn't leave my LAN.

---

### Post by arnavk007 on 2010-11-09
> **arrrghhh said:**
> Need to add them to samba?  If you don't share at the root, you need to share everything piecemeal.  I share at the root, which isn't recommended - but samba doesn't leave my LAN.
samba wont leave my lan
i tried sharing the root but still one cannot access the external hdds

also after doing force user = arnav
windows cannot access the pc only as i think that guest access has been restricted

---

### Post by Morbius1 on 2010-11-09
> **arnavk007 said:**
> > Quote:
                                                                      Originally Posted by **arrrghhh**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10085396#post10085396")                 
                 *Need to add them to samba?  If you  don't share at the root, you need to share everything piecemeal.  I  share at the root, which isn't recommended - but samba doesn't leave my  LAN.*
samba wont leave my lan
i tried sharing the root but still one cannot access the external hdds

also after doing force user = arnav
windows cannot access the pc only as i think that guest access has been restricted
I can't offer you any help because I really have no idea what's going on here any more. But I would one last time like to caution you on what you are doing.

You are sharing your entire root directory.
You are allowing guest access to the root directory.
You are using "force user" to convert the remote user to you.

There's an excellent chance that I'm wrong about this but somewhere in these posts you mentioned that the server is a laptop so sooner or later you will in fact leave the LAN.

All of this adds up to be a very bad idea.

---

### Post by CharlesA on 2010-11-09
> **Morbius1 said:**
> I can't offer you any help because I really have no idea what's going on here any more. But I would one last time like to caution you on what you are doing.

You are sharing your entire root directory.
You are allowing guest access to the root directory.
You are using "force user" to convert the remote user to you.

There's an excellent chance that I'm wrong about this but somewhere in these posts you mentioned that the server is a laptop so sooner or later you will in fact leave the LAN.

All of this adds up to be a very bad idea.

Definitely hit it on the head Morbius1.

Samba really isn't that hard to get set up, but the way the OP has set up the permissions means that if anyone got onto their lan (even with an invalid account) they'd be able to read everything, and write to specific areas.

EDIT: Here's my smb.conf so that you might get back on the right track.

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

# server string is the equivalent of the NT Description field
  server string =

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

#[printers]
#   comment = All Printers
#   browseable = no
#   path = /var/spool/samba
#   printable = yes
#   guest ok = no
#   read only = yes
#   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
#[print$]
#   comment = Printer Drivers
#   path = /var/lib/samba/printers
#   browseable = yes
#   read only = yes
#   guest ok = no
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


[Charles]
        comment = Charles' Folder
        invalid users = clone,htpc
        create mode = 660
        path = /array/charles
        write list = charles
        directory mode = 770

[Clone]
        browseable = no
        invalid users = htpc
        path = /array/clone
        write list = clone,charles
        comment = Clonezilla Folder
        create mode = 660
        directory mode = 770

[VM]
        browseable = no
        invalid users = clone,htpc
        path = /array/vms
        write list = charles
        comment = Windows Stuff
        create mode = 660
        directory mode = 770

```

---

### Post by arnavk007 on 2010-11-09
> **Morbius1 said:**
> I can't offer you any help because I really have no idea what's going on here any more. But I would one last time like to caution you on what you are doing.

You are sharing your entire root directory.
You are allowing guest access to the root directory.
You are using "force user" to convert the remote user to you.

There's an excellent chance that I'm wrong about this but somewhere in these posts you mentioned that the server is a laptop so sooner or later you will in fact leave the LAN.

All of this adds up to be a very bad idea.

i am not sharing the root directory
the post before me suggested that
i am allowing guest access to the external hdd only.
yes i am using force user as in one of your earlier posts in another thread you had suggested that to another guy in the same problem
i am using a laptop just cuz i dont have another spare pc

---

### Post by CharlesA on 2010-11-09
Post yer current smb.conf file please.

---

### Post by arnavk007 on 2010-11-09
will this do

```

[global]
netbios name = homeserver
server string = Samba file and print server
workgroup = WORKGROUP
security = SHARE
hosts allow = 192.168.1.
interfaces = lo eth0
bind interfaces only = true
remote announce = 192.168.1.255
remote browse sync = 192.168.1.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spools = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no
forceuser = arnav

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = no
printable = no
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
guest ok = Yes
printable = Yes
use client driver = Yes
browseable = No

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

[data]
path = /media/Arnav Data
comment = data
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = no
locking = no
strict locking = no
directory mask = 0777
create mode = 0777



```

---

### Post by CharlesA on 2010-11-09
Just post the file in [noparse]```

```[/noparse] tags please.

It's easier to break it down if you don't have to open it in a seperate program.

How did you create that smb.conf file? There are a ton of options that should have been commented out that you don't need.

---

### Post by arnavk007 on 2010-11-09
> **CharlesA said:**
> Just post the file in [noparse]```

```[/noparse] tags please.

It's easier to break it down if you don't have to open it in a seperate program.

How did you create that smb.conf file? There are a ton of options that should have been commented out that you don't need.
thanks for doing so
i made that smb.conf by typing
```
 sudo cp /etc/samba/smb.conf /home/arnav/Desktop 
```
i edited by reading various docs and what not

---

### Post by CharlesA on 2010-11-09
Well it's totally messed up. Take a look at my smb.conf and compare the two.

Note: The default smb.conf that comes with Ubuntu should work fine for most applications, you would have just needed to add the shares.

---

### Post by arnavk007 on 2010-11-10
ok will try that
i thought of backing up all data then i should follow the guide on woodel.com

---

### Post by CharlesA on 2010-11-10
That would probably be a good idea. :)

---

### Post by arnavk007 on 2010-11-10
> **CharlesA said:**
> That would probably be a good idea. :)
so then my next update should be in the next 2-3 days as my new pc will arrive by then.
thank you charlesA for all your help
can i ask the questions which i may need to ask in this thread only

---

### Post by CharlesA on 2010-11-10
If the questions aren't related to Samba, start a new thread, since it would be offtopic for this one.

---

### Post by arnavk007 on 2010-11-10
> **CharlesA said:**
> If the questions aren't related to Samba, start a new thread, since it would be offtopic for this one.
okssssssssss

---

### Post by Morbius1 on 2010-11-10
> **arnavk007 said:**
> ok will try that
i thought of backing up all data then i should follow the guide on woodel.com
I took a quick look at the woodel.com documentation and that explains why your current smb.conf looks the way it does and why it will probably look that way again after you are done.

There are two kinds of samba servers. A small "s" server that's in a peer-to-peer network where everyone is basically a server and a client and shares folders to everyone else. And a big "S" server which has a totally different function. It looks like you are trying to build a big "S" server.

Based on your original post:
> Ya every one I have one question
could anyone explain to me the use of smbusers in samba
is it like this
If I have a win pc with a user abc then I need to have a user abc with  Same passed in both ubuntu and samba or is it something else
is it possible for me to directly share th whole file system or should I share /dev/sda
otherwise I have already set up shares     It looks like you have a small number of users and are only using the server as a small file, backup, and perhaps print server. If that is correct that how to goes way beyond your needs.

What is the intended purpose of this server? And how many users will access this server?

In fairness you did post in the "Server Platforms" section of the forums something which I did not notice because of the nature of your first post.

---

### Post by CharlesA on 2010-11-10
> **Morbius1 said:**
> 
Based on your original post:
It looks like you have a small number of users and are only using the server as a small file, backup, and perhaps print server. If that is correct that how to goes way beyond your needs.

That's probably true. That guide is fairly good, but there's a lot of stuff that isn't really needed for the average home user.

It's a good way to learn tho. :)

---

### Post by arnavk007 on 2010-11-10
> **Morbius1 said:**
> I took a quick look at the woodel.com documentation and that explains why your current smb.conf looks the way it does and why it will probably look that way again after you are done.

There are two kinds of samba servers. A small "s" server that's in a peer-to-peer network where everyone is basically a server and a client and shares folders to everyone else. And a big "S" server which has a totally different function. It looks like you are trying to build a big "S" server.

Based on your original post:
It looks like you have a small number of users and are only using the server as a small file, backup, and perhaps print server. If that is correct that how to goes way beyond your needs.

What is the intended purpose of this server? And how many users will access this server?

In fairness you did post in the "Server Platforms" section of the forums something which I did not notice because of the nature of your first post.

Sorry for answering late

lemme answer your questions

> **Morbius1 said:**
>  It looks like you have a small number of users and are only using the  server as a small file, backup, and perhaps print server. If that is  correct that how to goes way beyond your needs.

What is the intended purpose of this server? And how many users will access this server?
 

The purpose you guessed is correct. It will act like a file, backup and print server with a capital 'S'
No. of users would be  only 3 .
I would like it to act like a NAS if i am correct but i also would want it to download torrents
i think i can set up rtorrent to do so
also it should share my printer

[http://ubuntuforums.org/showpost.php?p=9965956&postcount=31](http://ubuntuforums.org/showpost.php?p=9965956&postcount=31)

i think you did not read my earlier thread fully.

---

### Post by mr_Loki on 2010-11-10
&#1096;&#1090;

in smb.conf:
[resource name]
path = directory
browseable = yes
writable = yes
**public = yes** //no passwd
create mode = 0777
directory mode = 0777

have NAT?

---

### Post by Morbius1 on 2010-11-10
> **arnavk007 said:**
> The purpose you guessed is correct. It will act like a file, backup and print server with a capital 'S'
No. of users would be  only 3 .
I would like it to act like a NAS if i am correct but i also would want it to download torrents
i think i can set up rtorrent to do so
also it should share my printer

[http://ubuntuforums.org/showpost.php?p=9965956&postcount=31](http://ubuntuforums.org/showpost.php?p=9965956&postcount=31)

i think you did not read my earlier thread fully.
What you just described above is a server with a little "s". However, based on your link you obviously have a vision for this server that is much bigger if you want to print a file from your mobile phone so I wish you well.

---

### Post by arnavk007 on 2010-11-10
Yup you right
ya I have nat in my router

---

### Post by arrrghhh on 2010-11-10
> **arnavk007 said:**
> Yup you right
ya I have nat in my router

I don't get it... Are you still having samba issues?  There's no reason for these 6 page threads dude, it's ludicrous.

---

### Post by arnavk007 on 2010-11-11
> **arrrghhh said:**
> I don't get it... Are you still having samba issues?  There's no reason for these 6 page threads dude, it's ludicrous.
Yes i still have an issue which says that i cannot access external drives on the network
after that my smb.conf according to them is messed up
currently i have no idea of what should i do

also it is ridiculous not ludicrous
my thread is only 1 page long

---

### Post by Morbius1 on 2010-11-11
I made a promise to myself that I would leave this thread and yet here I am again :(

You have an error in your current ( if it still is your current ) smb.conf:

It's not:
> forceuser = arnavIt's:
>  force user = arnavYou have about 128 other parameters ( that might be a slight exaggeration ) in your smb.conf that might interfere with things but some of them I've never seen before.

If the [data] share is pointing to an external ntfs or fat32 partition then that's likely the reason you can't get remote access. It will mount to arnav with permissions for only arnav to read and write. "force user" is a legitimate way around this but since you're using classic samba sharing it would be better if it where in the [data] section and not the [global] section. Especially if you ever decide to share "/" again.

---

### Post by arnavk007 on 2010-11-11
> **Morbius1 said:**
> I made a promise to myself that I would leave this thread and yet here I am again :(

You have an error in your current ( if it still is your current ) smb.conf:

It's not:
It's:
You have about 128 other parameters ( that might be a slight exaggeration ) in your smb.conf that might interfere with things but some of them I've never seen before.

If the [data] share is pointing to an external ntfs or fat32 partition then that's likely the reason you can't get remote access. It will mount to arnav with permissions for only arnav to read and write. "force user" is a legitimate way around this but since you're using classic samba sharing it would be better if it where in the [data] section and not the [global] section. Especially if you ever decide to share "/" again.
Man you hit the bullseye of the problem.

---

### Post by CharlesA on 2010-11-11
I modified smb.conf with what you are trying to do:

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

# server string is the equivalent of the NT Description field
  server string = Samba file and print server

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

#[printers]
#   comment = All Printers
#   browseable = no
#   path = /var/spool/samba
#   printable = yes
#   guest ok = no
#   read only = yes
#   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
#[print$]
#   comment = Printer Drivers
#   path = /var/lib/samba/printers
#   browseable = yes
#   read only = yes
#   guest ok = no
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


[Data]
        comment = Data
        path = /media/Arnav\ Data
        write list = arnav
        directory mode = 770
        create mode = 660
        force user = arnav
```

The space in "Arnav Data" will probably cause problems, but I escaped it, so maybe it'll work.

You'd be better off creating a manual mount and mounting it there in fstab.

---

### Post by arnavk007 on 2010-11-11
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

# server string is the equivalent of the NT Description field
  server string = Samba file and print server

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
   load printers = yes

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
   guest ok = yes
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
#[print$]
#   comment = Printer Drivers
#   path = /var/lib/samba/printers
#   browseable = yes
#   read only = yes
#   guest ok = no
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


[Data]
        comment = Data
        path = /media/Arnav\ Data
        write list = arnav
        directory mode = 770
        create mode = 660
        force user = arnav

```

Is this good?

---

### Post by CharlesA on 2010-11-11
Make a backup of the current smb.conf file and copy/paste that one in then reboot. See if that'll work.

---

### Post by arnavk007 on 2010-11-11
i am not able to see this laptop after reboot
even though i can see the mediatomb server running on it

---

### Post by CharlesA on 2010-11-11
Are you able to connect by using the ip address?

If yes, then add an entry in the /etc/hosts file to point to the ip of that machine.

---

### Post by arnavk007 on 2010-11-11
> **arnavk007 said:**
> ```

 

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

changed this to

interfaces = eth0




####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

changed this to 

security = share



```Is this good?

now i can connect but the external ntfs hdd is still giving the same not browsable error

any permanent solution for this problem

---

### Post by CharlesA on 2010-11-11
Change the mountpoint. It's probably the space that is screwing it up.

---

### Post by Morbius1 on 2010-11-11
This may be a problem:
>  path = /media/Arnav\ DataSmb.conf is probably the only place in all of Linuxdom where this is an acceptable format:
> path = /media/Arnav DataI tried to do it on my own system: /home/morbius/Shared\ Files and got a "Failed to Mount" error. Got rid of the "\" and I was good to go.

Then I tried it using system-config-samba and it also produced the line without a '\'.

---

### Post by CharlesA on 2010-11-11
Ah, I didn't know that.

Those darn spaces!

---

### Post by arrrghhh on 2010-11-11
> **CharlesA said:**
> Ah, I didn't know that.

Those darn spaces!

Seriously.  In some places you have to escape them with a simple \.  Sometimes you have to do a \020.  In this case you don't need to escape it at all!!  Oy ve.



7 pages is both ridiculous and ludicrous.  Perhaps gratuitous.

---

### Post by arnavk007 on 2010-11-11
> **arrrghhh said:**
> Seriously.  In some places you have to escape them with a simple \.  Sometimes you have to do a \020.  In this case you don't need to escape it at all!!  Oy ve.



7 pages is both ridiculous and ludicrous.  Perhaps gratuitous.
Ok will remove the backslash when I have access to the computer 
is there any way to check if it's working without using another comp

btw what do you mean by ludicrous and gratuitous

---

### Post by CharlesA on 2010-11-11
Run ***testparm*** to check the smb.conf.

Otherwise there's really no real way to make sure it's working except to use another machine.

---

### Post by arnavk007 on 2011-01-23
I am sorry for bumping this thread.
I am now sitting on an even bigger mess.
my pc arrived and now my holidays have started.
i tried file sharing again using another laptop as the server.
after exploding my head i still couldnt get both of em to see each other

---

### Post by arrrghhh on 2011-01-23
> **arnavk007 said:**
> I am sorry for bumping this thread.
I am now sitting on an even bigger mess.
my pc arrived and now my holidays have started.
i tried file sharing again using another laptop as the server.
after exploding my head i still couldnt get both of em to see each other

Really?  With all the tips and guidance in this thread you can't give us at least a little more information?  What stage you're at?  What's not working?  What have you tried?  Honestly, you need to learn how to do basic troubleshooting - you need to be more methodical so we can help you.  If you just go about trying things willy nilly, it's nearly impossible to pinpoint where you're going wrong.

---

### Post by arnavk007 on 2011-01-24
> **arrrghhh said:**
> Really?  With all the tips and guidance in this thread you can't give us at least a little more information?  What stage you're at?  What's not working?  What have you tried?  Honestly, you need to learn how to do basic troubleshooting - you need to be more methodical so we can help you.  If you just go about trying things willy nilly, it's nearly impossible to pinpoint where you're going wrong.
Lets see
I found another laptop with a bigger hdd to make the server
i decide to use the older one for other purposes.
i have installed ubuntu 10.10 desktop on it.
i installed freenx on it so that i could manage it.
i gave it a static ip address.
i installed samba on it.
when i try to see my win 7 pc with it it does not see it
my win 7 pc also does not see it.

---

### Post by arrrghhh on 2011-01-24
> **arnavk007 said:**
> Lets see
I found another laptop with a bigger hdd to make the server
i decide to use the older one for other purposes.
i have installed ubuntu 10.10 desktop on it.
i installed freenx on it so that i could manage it.
i gave it a static ip address.
i installed samba on it.
when i try to see my win 7 pc with it it does not see it
my win 7 pc also does not see it.

testparm?  samba config?  C'mon man.  Let's troubleshoot one thing - samba.  Let's focus on that...

Also, I'm assuming you've done the network basics - can you ping the Win7 box from the Ubuntu box and visa-versa?

---

### Post by mstjohn1974 on 2011-09-18
You could get it to work without username and password if you like...

just look at my website I posted one article/video regarding samba

[http://www.ubuntuvideocast.com](http://www.ubuntuvideocast.com)

---

### Post by HermanAB on 2011-09-19
Hmmm, why faff around with Samba in the first place?  It is much, much, much easier to get NFS to work, since it requires only two lines of configuration - one line on the server and one line on the client.  

Samba is for masochists...
;)

---

### Post by Morbius1 on 2011-09-19
> **HermanAB said:**
> Hmmm, why faff around with Samba in the first place?  It is much, much, much easier to get NFS to work, since it requires only two lines of configuration - one line on the server and one line on the client.  

Samba is for masochists...
;)
Samba works out of the box unless the user goes out of his way to mess up his smb.conf file. Samba requires only two lines of configuration - one line on the server, for example:
> net usershare add documents /home/morbius/Documents "morbius documents" username:F guest_ok=yAnd one line on the client, for example:
> gvfs-mount smb://server-name/documentsOr better yet do it the by ip address:
> gvfs-mount smb://192.168.0.100/documentsNFS is for people who know where and what they are trying to connect to whereas Samba is a "browseable" protocol. It's the "browseability" aspect of samba that fills this forum with support questions since it relies on things outside of Samba ( firewalls, name lengths, name services. etc... ) to be set up correctly.

---

