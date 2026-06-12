---
title: "Accessing Shares Folder"
date: 2010-07-29
forum: Server Platforms
---

### Post by youngros on 2010-07-29
When I type my ip address into run I get up the window with the shares folder, but I am denied access to this folder. How do I set it so that it can be accessed please. 
I can access by webmin but would also like to be able to via windows.

---

### Post by flatline on 2010-07-29
You need to provide more information about what you are trying to do and what is going wrong.

Are you trying to share a directory from your Ubuntu server to a windows PC?  Have you already installed and configured Samba?

Do you want security enabled, or do you want anyone on your network to be able to view/access/modify the files in the shared directory?

---

### Post by endotherm on 2010-07-29
my guess is that you haven't registered the windows users password with samba (smbpasswd -a <username>) but i'm not even sure you are running samba so...

---

### Post by Morbius1 on 2010-07-29
If you're using Samba why not post the output of the following commands so we can see what method of samba you are using and how your shares are configured:

```
net usershare info
```
```
testparm -s
```

---

### Post by youngros on 2010-07-29
Hi, yes I am using Samba.
I have one user created and I can get access to that folder by adding the username after the ip address and then entering the password at the prompt, but would like to be able to have access to the shares folder.

output from testparm -s

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[allusers]"
Unknown parameter encountered: "pathe"
Ignoring unknown parameter "pathe"
WARNING: No path in service allusers - making it unavailable!
NOTE: Service allusers is flagged unavailable.
Processing section "[homes]"
Unknown parameter encountered: "broweable"
Ignoring unknown parameter "broweable"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = OFFICE
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
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

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[allusers]
        comment = All Users
        valid users = @users
        force group = users
        read only = No
        create mask = 0600
        directory mask = 0771
        available = No

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0700
        directory mask = 0700

as this is only a LAN setup really no need for everything to be password protected, but understand the importance of being able to get them right.

nothing happens if I type in net usershare info

---

### Post by Morbius1 on 2010-07-29
The output from testparm is showing you the problem:
> Unknown parameter encountered: "pathe"
Ignoring unknown parameter "pathe"
WARNING: No path in service allusers - making it unavailable!
NOTE: Service allusers is flagged unavailable.
Processing section "[homes]"
Unknown parameter encountered: "broweable"
Ignoring unknown parameter "broweable"This is one of those situation where I should have asked for the output of the entire smb.conf. I'm guessing that you have a typo on each share that reads "pathe" instead of "path"

Try to change the spelling and restart samba:
```
sudo service smbd restart
```If that doesn't fix it post your entire smb.conf:
```
cat /etc/samba/smb.conf
```

[COLOR=Blue]EDIT: Just saw something else. You have a share with "available = No" as an option. Even if you fix the spelling it still won't work.
Post your entire smb.conf please. Sorry about the mixup[/COLOR]

---

### Post by flatline on 2010-07-29
> **Morbius1 said:**
> The output from testparm is showing you the problem:
This is one of those situation where I should have asked for the output of the entire smb.conf. I'm guessing that you have a typo on each share that reads "pathe" instead of "path"

Try to change the spelling and restart samba:
```
sudo service smbd restart
```If that doesn't fix it post your entire smb.conf:
```
cat /etc/samba/smb.conf
```

[COLOR=Blue]EDIT: Just saw something else. You have a share with "available = No" as an option. Even if you fix the spelling it still won't work.
Post your entire smb.conf please. Sorry about the mixup[/COLOR]


Yeah, and it looks like "browseable" is misspelled as well...

> Processing section "[homes]"
Unknown parameter encountered: "broweable"
Ignoring unknown parameter "broweable"
Loaded services file OK.

---

### Post by youngros on 2010-07-29
the difference it make is instead of just getting shares folder I instead get all users and homes

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

[allusers]
comment = All Users
path = /home/shares/allusers
valid users = @users
force group = users
create mask = 0600
directory mask = 0771
writable = yes

[homes]
comment = Home Directories
broweable = no
valid users = %S
writable = yes
create mask = 0700
directory mask = 0700

---

### Post by Morbius1 on 2010-07-29
> [homes]
comment = Home Directories
[COLOR=Blue] broweable = no[/COLOR]
valid users = %S
writable = yes
create mask = 0700
directory mask = 0700     Change the spelling to browseable 
> [allusers]
comment = All Users
path = /home/shares/allusers
valid users = @users
force group = users
create mask = 0600
directory mask = 0771
writable = yes
I'm trying to figure out how testparm saw an "available = no" option. I can't find it anywhere in your file. The only other oddity is the following combination:
> force group = users
 create mask = 0600Force group will make every remote user appear to be a member of the "users" group. But create mask option will force all new files to have read /write permissions to the user who added the file only. It's late in the day for me maybe I'm missing something here.
>    map to guest = bad userYou want that line in your smb.conf. Without it there's no way to convert an unauthenticated remote user to the default guest account assuming you ever need to create a guest accessible share.

---

### Post by youngros on 2010-07-29
f> orce group = users
 create mask = 0600

came from [http://www.howtoforge.com/ubuntu-10.04-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-10.04-samba-standalone-server-with-tdbsam-backend)

corrected my spellings...will have to be more careful

> map to guest = bad user 			 		

is the first line of the smb.conf file

will see what happens tomorrow...thanks for your time and help

---

### Post by Morbius1 on 2010-07-29
>      Quote:
                                                 orce group = users
[COLOR=Blue]  create mask = 0600                                 [/COLOR]
came from [http://www.howtoforge.com/ubuntu-10....tdbsam-backend]("http://www.howtoforge.com/ubuntu-10.04-samba-standalone-server-with-tdbsam-backend")Another typo, that HowTo had this for the "allusers" share:> 
[allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  force group = users
[COLOR=Blue]  create mask = 0660[/COLOR]
  directory mask = 0771
  writable = yesThat makes more sense since now both owner and group will have read write access and group will all be forced to "users"

---

### Post by youngros on 2010-07-30
Put that down to bad eyesight!! This is the new smb.conf file I still can't log into the All users share folder..should I be able to?

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

[allusers]
comment = All Users
path = /home/shares/allusers
valid users = @users
force group = users
create mask = 0660
directory mask = 0771
writable = yes

[homes]
comment = Home Directories
browseable = no
valid users = %S
writable = yes
create mask = 0700
directory mask = 0700

---

### Post by Morbius1 on 2010-07-30
Only if you did the following from the HowTo and created the "users" group, it's members, and gave them samba passwords:
> **4 Adding And Managing Users **

  In this example, I will add a user named tom. You can add as many users as you need in the same way, just replace the username tom with the desired username in the commands. 
 useradd tom -m -G users
  Set a password for tom in the Linux system user database. If the user tom should not be able to log in to the Linux system, skip this step. 
 passwd tom
  -> Enter the password for the new user.
  Now add the user to the Samba user database:
 smbpasswd -a tom
  -> Enter the password for the new user.


---

### Post by youngros on 2010-07-30
Ahh, got it now. I was trying to log in with my username and pasword and not the one for the user that I had created. 

Confusing the user I created has been given a folder that shows in webmin but the folder is not in the allusers, is this normal? I was thinking that the folder would be withing the allusers folder.

---

### Post by endotherm on 2010-07-30
I'm no samba guru, but this doesn;t look right (or at least consistent)
```

[allusers]
comment = All Users
path = /home/shares/allusers
**valid users = @users**
force group = users
create mask = 0660
directory mask = 0771
writable = yes

[homes]
comment = Home Directories
browseable = no
**valid users = %S**
writable = yes
create mask = 0700
directory mask = 0700

```

---

