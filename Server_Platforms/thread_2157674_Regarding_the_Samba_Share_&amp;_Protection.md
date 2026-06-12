---
title: "Regarding the Samba Share &amp; Protection"
date: 2013-06-26
forum: Server Platforms
---

### Post by slkamath on 2013-06-26
Hi all,

I installed SAMBA in ubuntu 12.04LTS.

I can access the SAMBA share. if I try to open the share it's asking the user name, domain name, password. I tried with the user name which i configured in the server. but it's not opening. can anyone help me?

How to implement the below mentioned securities?

1. User authentication to access folders or files.
2. User copy protection.
3. User print protection.
4. User edit protection (2 users can esit, others are not permitted).
5. User delete protection.
6. If possible user logs (who are all accessed).

My smb.conf is like this
********************************************************************************************************
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
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    obey pam restrictions = yes
    write list = administrator,@sambagrp
    map to guest = bad user
    passdb backend = tdbsam
    passwd program = /usr/bin/passwd %u
    wins support = yes
    dns proxy = no
    netbios name = FILESERVER
    writeable = yes
    server string = %h server (Samba, Ubuntu)
    unix password sync = yes
    workgroup = UBUNTU
    os level = 20
    syslog = 0
    security = user
    usershare allow guests = yes
    panic action = /usr/share/samba/panic-action %d
    max log size = 1000
    pam password change = yes
    force user = administrator

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server

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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[share]
    force user = administrator    
    comment = Ubuntu File Server Share
    read list = ema,ma,maintenance,marketing,mproduction,mqc,qa,stores
    writeable = no
    browsable = yes
    path = /srv/samba/share
#    create mask = 0644
#    directory mask = 0755

[qms 9001]
    force user = administrator
    writeable = no
    read list = ema,ma,maintenance,marketing,mproduction,mqc,qa,stores
    path = /home/qms 9001/
```

********************************************************************************************************

Shares & rights are you can see in the picture.
[ATTACH=CONFIG]244181[/ATTACH]


Please guide me. 

Thanks in advance.

Regards

Lokesh Kamath

---

### Post by volkswagner on 2013-06-26
Webmin is not supported by Ubuntu.  It can give unexpected results.

With that said, do all of your samba users exist as regular Linux users?
You can see your Linux users in /etc/passwd.

```
cat /etc/passwd
```

From what platform are you accessing the share? Windows?
Does the client username/password match the samba username and password (case sensitive)?

---

### Post by slkamath on 2013-06-26
> **volkswagner said:**
> Webmin is not supported by Ubuntu.  It can give unexpected results.

With that said, do all of your samba users exist as regular Linux users?
You can see your Linux users in /etc/passwd.

```
cat /etc/passwd
```

From what platform are you accessing the share? Windows?
Does the client username/password match the samba username and password (case sensitive)?

*****************************************************
Thanks for your reply. Output of cat /etc/passwd is shown below.

[ATTACH=CONFIG]244206[/ATTACH]

I am accessing the samba share from windows 7, windows xp, and ubuntu desktop.

Windows systems are having windows Domain Controller. 
Cilent user name & password is not match with samba user name password. In samba I configured user name as department name. (So as per your information I need to configure client user name & password has to match with the samba user name & password.) i.e. I need to reconfigure the user name & password right.

any other changes i need to do?

Thanks once again.

Lokesh Kamath

---

### Post by volkswagner on 2013-06-27
I'm sorry I don't have much experience with SAMBA joining a Windows Domain.

Perhaps you should describe your network setup and goals before proceeding.

You will likely want to join your SAMBA fileserver to your windows domain to get password
authentication working via the PDC.  Have you done this already?

May I ask why you chose department names over usernames?

Technically you should be able to connect as a different user as that of your client, but this behavior can be
different and even problematic, particularly on Windows 7 clients.

---

### Post by slkamath on 2013-06-27
I am also using SAMBA first time.
I have PDC as windows Domain Controller.

In each department we have nearly 4 to 5 systems so I thought each department I can create one user means anyone in that department use the same name (this is my thinking).

My Network Setup: 
We have nearly 15 Windows Systems, 25 Ubuntu Desktop's.
IP Address is 192.192.0.1/24

Purpose: 
We have certain work instruction and formats which will be useful for all, but they should not take print, copy, edit, delete.
Audit we need to show this type scenario to customers and auditors.

---

### Post by newbie-user on 2013-06-27
You can specify access by groups:
```
valid-users = @sambagroup
```
You can also create different shares of the same folder with different permissions:
```

[read/write share]
comment = samba share
path = /path/to/samba/share
browsable = yes
guest ok = no
read only = no
create mask = 0777
valid users = @smbgroup

[read-only share]
comment = samba share
path = /path/to/samba/share
browsable = yes
guest ok = yes
read only = yes

```

---

### Post by slkamath on 2013-06-27
Thanks for your suggestion. 

I will try to implement this and will get back to you.

Lokesh Kamath

Sorry to say that still it's asking password.

Lokesh Kamath

---

### Post by volkswagner on 2013-07-01
Have you joined your SAMBA server to your Windows domain?

Are you still using webmin?  You can have adverse affects when using webmin and editing smb.conf directly!

What does testparm output?

```
testparm
```

Can you access the shares from the server itself?

```
smbclient //localhost/share -U administrator -L
```

with administrator you should be able to list files/dir's and create a test directory 

```
smb: \>  ls
```
```
smb: \>  mkdir test
```

Quit to exit:
```
smb: \>  quit
```

Do your samba users exist as expected? List your samba users:
```
sudo pdbedit -L
``` 

Try logging in to a share they have read access to with smbclient command above:


What are the permissions of your shares?

```
ls -l /srv/samba/share
```

```
ls -l /home/qms\ 9001/
```

---

### Post by SeijiSensei on 2013-07-01
Your list of restrictions may require additional controls than just the normal read/write/execute permissions that Unix implements.  For instance, if a user can read a file, he or she can copy it.

Samba has some extensions to use more fine-grained access control lists (ACLs).  I've never used any of this, so all I can do is suggest you read this: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2613459](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2613459), and in particular, [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2614541](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2614541).

---

### Post by slkamath on 2013-07-01
Thanks for your reply.

I will check and revert back.

Lokesh Kamath

---

### Post by slkamath on 2013-07-01
> **volkswagner said:**
> Have you joined your SAMBA server to your Windows domain?

Are you still using webmin?  You can have adverse affects when using webmin and editing smb.conf directly!

What does testparm output?

```
testparm
```

Can you access the shares from the server itself?

```
smbclient //localhost/share -U administrator -L
```

with administrator you should be able to list files/dir's and create a test directory 

```
smb: \>  ls
```
```
smb: \>  mkdir test
```

Quit to exit:
```
smb: \>  quit
```

Do your samba users exist as expected? List your samba users:
```
sudo pdbedit -L
``` 

Try logging in to a share they have read access to with smbclient command above:


What are the permissions of your shares?

```
ls -l /srv/samba/share
```

```
ls -l /home/qms\ 9001/
```




testparm output

screen shot inculded.


access the shares from the server
Cant access. Screen Shot included.

[ATTACH=CONFIG]244313[/ATTACH][ATTACH=CONFIG]244314[/ATTACH][ATTACH=CONFIG]244313[/ATTACH][ATTACH=CONFIG]244314[/ATTACH]

---

### Post by volkswagner on 2013-07-02
I'd really like to help, but posting four pictures of your testparm command is not really helpful.

Why are you posting screenshots instead of pasting actual output (to copy text from terminal hold <shift>+<ctrl>+C)?

Why didn't you post output of other commands in my post (like "pdbedit -L" to list SAMBA users)?

It appears your users/passwords are not setup properly.

I'd dump webmin and follow the [server docs]("https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html") for properly setting up samba.

If you can't access samba shares from command line, you surely won't be able to access shares from other clients.

---

### Post by Morbius1 on 2013-07-02
Sorry for the interruption but there is one thing I'd like to point out:

If I run "testparm -s" against your original posted smb.conf I get this for the [COLOR=#0000cd]**[global]**[/COLOR] section:
> [global]
    workgroup = UBUNTU
    netbios name = FILESERVER
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
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    write list = administrator, @sambagrp
    force user = administrator
    read only = No
What you posted for testparm in your last post was this for the [global] section:
> idmap config * : backend = tdb
If you are going to make such dramatic changes to your smb.conf between posts it will be nearly impossible for any one to help you debug your problem.

---

### Post by slkamath on 2013-07-02
> **volkswagner said:**
> I'd really like to help, but posting four pictures of your testparm command is not really helpful.

Why are you posting screenshots instead of pasting actual output (to copy text from terminal hold <shift>+<ctrl>+C)?

Why didn't you post output of other commands in my post (like "pdbedit -L" to list SAMBA users)?

It appears your users/passwords are not setup properly.

I'd dump webmin and follow the [server docs]("https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html") for properly setting up samba.

If you can't access samba shares from command line, you surely won't be able to access shares from other clients.



I was really dont know how to post the output... I am sorry.... Now only i come to know..... Thanks...
Output of pdbedit -L:

```
root@dataserver:/home/administrator# pdbedit -L
nobody:65534:nobody
administrator:1000:administrator
admini:4294967295:
slkamath:1001:
loks:4294967295:
slk:4294967295:
nageshur:1002:
root@dataserver:/home/administrator#
```

> **Morbius1 said:**
> Sorry for the interruption but there is one thing I'd like to point out:

If I run "testparm -s" against your original posted smb.conf I get this for the [COLOR=#0000cd]**[global]**[/COLOR] section:

What you posted for testparm in your last post was this for the [global] section:

If you are going to make such dramatic changes to your smb.conf between posts it will be nearly impossible for any one to help you debug your problem.

Hi,

**_Output of testparm -s is:_**

```
root@dataserver:/home/administrator# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[qms]"
Unknown parameter encountered: "guest"
Ignoring unknown parameter "guest"
Processing section "[formats]"
Unknown parameter encountered: "guest"
Ignoring unknown parameter "guest"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        idmap config * : backend = tdb

[qms]
        comment = Welcome to QMS Share
        path = /home/shares/qms
        read only = No

[formats]
        comment = Welcome to Formats
        path = /home/shares/formats
        read only = No
root@dataserver:/home/administrator#


_**Also output of smb.conf is:**_

root@dataserver:/home/administrator# sudo vi /etc/samba/smb.conf
[global]
workgroup = WORKGROUP
security = user
encrypt passwords = yes

[qms]
comment = Welcome to QMS Share
path = /home/shares/qms
read only = no
browsable = yes
writeable = yes
guest = yes
[formats]
comment = Welcome to Formats
path = /home/shares/formats
read only = no
browsable = yes
writeable = yes
guest = yes
```

Very sorry I am newly configuring the SAMBA...

Hi,

Now SAMBA share is not asking password. The link which you sent of Server Docs it helped me.. THANKS... :popcorn:

Ubuntu machine I can access the Samba shares but from Windows 2003 server machine I cant access shares. :(

Now How I need to secure the Samba Share. 
I need only one user have full permission to do (add files, delete files, change files, copy files print files, rest all should have only read permission)

Lokesh Kamath

---

### Post by volkswagner on 2013-07-03
You should add the following to your [global] section:

```
map to guest = bad user
```

You have errors in your shares as seen from output of testparm:

```
guest = yes
```

Should be:

```
guest ok = yes
```

You still have several unanswered questions from previous posts!

When accessing from Server2003, are you logged in as administrator?  Does administrator password match for server2003 and SAMBA?

---

### Post by slkamath on 2013-07-04
Windows 2003 is is Domain Controller the password of Windows DC & Samba is different. Windows DC Name is LAXMIELEC. Sama is WORKGROUP.

How to give read only access to all users except administrator? (administrator should have full control).

Lokesh Kamath

---

### Post by volkswagner on 2013-07-04
It appears you are not even reading the help you have been offered.

---

### Post by slkamath on 2013-07-08
Thanks for your help.... I am trying it... I will reply once it's done...

---

