---
title: "windows 7 and samba file share server"
date: 2012-05-30
forum: Server Platforms
---

### Post by amngco on 2012-05-30
Hello Everybody

I am working on a samba server for months now. I got the samba share working for XP and now all computers have upgraded to windows 7. I'm running ubuntu 11.04 with samba (per synaptic package manager) version 2:3.5.8. I have searched all over the Internet for help on this and have tried everything from the registry edits to reduce the security measures, I have researched all the reasons that I can find about my problem, and all the fixes have not worked. :( 
   


The problem I am having is that you can see the server in the network and it's in the right workgroup. You can see the shares list from the server, the permissions trigger correctly, (you try to access a share you don't have permission for it tells you), and user credentials register are setup.
   However if you do have permissions to a certain directory, and you try to map to or simply browse it. it gives an error saying the network path cannot be found. My research into this problem says that windows 7 has different default security settings than what samba uses. I have found tutorials all over the place as to how this can be resolved, but I've tried everything that they said (disable digital signing, use NTLM2 only if negotiated, disable ipv6 tunneling, etc, etc, etc) and I still get the same error.

Does anyone have any idea where I could in the system either on the windows client or on the server where I might find more information on what's been happening?

Has anyone else had this? As I understand, it's been a big issue between and the Samba dev team.

Something else I forgot to mention, the error code is: 0x80070035
and has been the same one this whole time. Also the windows 7 versions range from home to ultimate SP1

---

### Post by CharlesA on 2012-05-30
network path not found usually means the network name wasn't resolved via broadcast or the path doesn't exist. Are the shares set up correctly?

Have you run testparm -s on the samba server itself?

Also might want to run smbtree and see what it says.

---

### Post by amngco on 2012-05-30
smbtree Returned:

Unknown parameter encountered: "client plaintext"
Ignoring unknown parameter "client plaintext"
Enter superuser1's password: 
WORKGROUP
    \\RNPD34ABA              
Server requested LM password but 'client lanman auth' is disabled
Server requested plaintext password but 'client plaintext auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
    \\MAINSERVER             mainserver server (Samba, Ubuntu)
        \\MAINSERVER\data               Data Directory
        \\MAINSERVER\superuser1         Home directory of superuser1
        \\MAINSERVER\IPC$               IPC Service (mainserver server (Samba, Ubuntu))
        \\MAINSERVER\Kens-shortcuts     
        \\MAINSERVER\Susan watson's shorcuts    
        \\MAINSERVER\Whitbros' shortcuts    
        \\MAINSERVER\Viri's Shortcuts    
        \\MAINSERVER\Marisela's shortcuts    
        \\MAINSERVER\Jeremy's shortcuts    
        \\MAINSERVER\George's shortcuts    
        \\MAINSERVER\Felipe's shortcuts    
        \\MAINSERVER\Elba's Shortcuts    
        \\MAINSERVER\daya's shortcuts    
        \\MAINSERVER\David strange's shortcuts    
        \\MAINSERVER\David Gamez's shortcuts    
        \\MAINSERVER\Consultation's Shortcuts    
        \\MAINSERVER\Belinda's Shortcuts    
        \\MAINSERVER\Becky's shortcuts    
        \\MAINSERVER\Araceli's Shortcuts    
        \\MAINSERVER\print$             Printer Drivers
        \\MAINSERVER\homes              
    \\ANN-PC                 
cli_start_connection: failed to connect to ANN-PC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
    \\ACCT03                 
    \\ACCT02                 
    \\A1123704               
cli_start_connection: failed to connect to A1123704<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\A1123703               
cli_start_connection: failed to connect to A1123703<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\A1123702               
cli_start_connection: failed to connect to A1123702<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\A1123701               
        \\A1123701\print$             Printer Drivers
        \\A1123701\IPC$               Remote IPC
        \\A1123701\HP LaserJet 5      HP LaserJet 5
        \\A1123701\D$                 Default share
        \\A1123701\C$                 Default share
        \\A1123701\ADMIN$             Remote Admin
    \\A1123204               
cli_start_connection: failed to connect to A1123204<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\A1123203               
    \\A1123202               
cli_start_connection: failed to connect to A1123202<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\A1123201               
cli_start_connection: failed to connect to A1123201<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\A1123101               
cli_start_connection: failed to connect to A1123101<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\A1122701               Ken's Computer
    \\A1115101               File Server

testparm didn't show any errors other than the plaintext error, which it then ignored.

---

### Post by CharlesA on 2012-05-30
Where did you add the "client plaintext" ??

MAINSERVER is your ubuntu box?

---

### Post by bab1 on 2012-05-31
> **amngco said:**
> smbtree Returned:

Unknown parameter encountered: "client plaintext"
Ignoring unknown parameter "client plaintext"
Enter superuser1's password: 
WORKGROUP
    \\RNPD34ABA              
Server requested LM password but 'client lanman auth' is disabled
Server requested plaintext password but 'client plaintext auth' is disabled
...

***testparm didn't show any errors other than the plaintext error, which it then ignored.***

What about these errors?```
cli_start_connection: failed to connect to ANN-PC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
\\ACCT03
\\ACCT02
\\A1123704
cli_start_connection: failed to connect to A1123704<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
\\A1123703
cli_start_connection: failed to connect to A1123703<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
\\A1123702
cli_start_connection: failed to connect to A1123702<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
\\A1123701
\\A1123701\print$ Printer Drivers
\\A1123701\IPC$ Remote IPC
\\A1123701\HP LaserJet 5 HP LaserJet 5
\\A1123701\D$ Default share
\\A1123701\C$ Default share
\\A1123701\ADMIN$ Remote Admin
\\A1123204
cli_start_connection: failed to connect to A1123204<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
\\A1123203
\\A1123202
cli_start_connection: failed to connect to A1123202<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
\\A1123201
cli_start_connection: failed to connect to A1123201<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
\\A1123101
cli_start_connection: failed to connect to A1123101<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
```

This in particular```
Error [COLOR="Red"]**NT_STATUS_BAD_NETWORK_NAME**[/COLOR]
```

Post the /etc/samba/smb.conf file for us to see and comment on.

---

### Post by amngco on 2012-05-31
I don't know what is with the bad network name error.  Nor the NT_STATUS_UNSUCCESSFUL error. 
I put the client plaintext in the global options because one of the places that I looked for fixes said that worked for them. 

And yes MAINSERVER is the ubuntu box. And as I said in the first post, this worked with XP.

The smb.conf is posted below. and the:
      ntlm auth = yes
;    lanman auth = yes
    client NTLMv2 auth = yes
;    client lanman auth = yes
    client plaintext = yes
    server signing = auto

Were added to the global section after the upgrade.

Code:

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
    wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

;    follow symlinks = yes
    wide links = yes
    unix extensions = no
;    ntlm auth = yes
;    lanman auth = yes
    client NTLMv2 auth = yes
;    client lanman auth = yes
    client plaintext = yes
    server signing = auto


#### Networking ####


;   interfaces = 127.0.0.0/8 eth0


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
;    encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

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

# CUPS printing.  See also the cupsaddsmb(:cool: manpage in the
# cupsys-client package.
;    printing = cups
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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
    security = user
;    guest ok = no
;    guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
[homes]
#    comment = Home Directories
#    browseable = yes


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
#    read only = no

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
    valid users = %S

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
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

[01-Active]
    path = /home/superuser1/Whitdata/01-Active
    writeable = yes
    browseable = no
    guest ok = yes

[02-Archived]
    path = /home/superuser1/Whitdata/02-Archived
    writeable = yes
    browseable = no
    guest ok = yes

[03-Lists-Forms]
    path = /home/superuser1/Whitdata/03-Lists-Forms
    writeable = yes
    browseable = no
    guest ok = yes

[04-Scheduling]
    path = /home/superuser1/Whitdata/04-Scheduling
    writeable = yes
    browseable = no
    guest ok = yes

[05-Personal]
    path = /home/superuser1/Whitdata/05-Personal
    writeable = yes
    browseable = no
    guest ok = yes

[06-Finance]
    path = /home/superuser1/Whitdata/06-Finance
    writeable = yes
    browseable = no
    guest ok = yes

[07-Research & Misc]
    path = /home/superuser1/Whitdata/07-Research & Misc
    writeable = yes
    browseable = no
    guest ok = yes

[08-Storage]
    path = /home/superuser1/Whitdata/08-Storage
    writeable = yes
    browseable = no
    guest ok = yes

[09-Mail]
    path = /home/superuser1/Whitdata/09-Mail
    writeable = yes
    browseable = no
    guest ok = yes

[10-Admin]
    path = /home/superuser1/Whitdata/10-Admin
    writeable = yes
    browseable = no
    guest ok = yes

[11-Miscans]
    path = /home/superuser1/Whitdata/11-Miscans
    writeable = yes
    browseable = no
    guest ok = yes

[12-GS]
    path = /home/superuser1/Whitdata/12-GS
    writeable = yes
    browseable = no
    guest ok = yes

[13-Immagration]
    path = /home/superuser1/Whitdata/13-Immagration
    writeable = yes
    browseable = no
    guest ok = yes

[14-Obits]
    path = /home/superuser1/Whitdata/14-Obits
    writeable = yes
    browseable = no
    guest ok = yes

[15-WSA]
    path = /home/superuser1/Whitdata/15-WSA
    writeable = yes
    browseable = no
    guest ok = yes

[16-CLE Programs]
    path = /home/superuser1/Whitdata/16-CLE Programs
    writeable = yes
    browseable = no
    guest ok = yes

[17-Calendars]
    path = /home/superuser1/Whitdata/17-Calendars
    writeable = yes
    browseable = no
    guest ok = yes

[18-Backups]
    path = /home/superuser1/Whitdata/18-Backups
    writeable = yes
    browseable = no
    guest ok = yes

[Araceli's Shortcuts]
    path = /home/superuser1/Whitdata/Araceli's Shortcuts
    writeable = yes
;    browseable = yes
    valid users = araceli, davids, george, mack

[Becky's shortcuts]
    path = /home/superuser1/Whitdata/Becky's shortcuts
    writeable = yes
;    browseable = yes
    valid users = becky, davids, george, mack

[Belinda's Shortcuts]
    path = /home/superuser1/Whitdata/Belinda's Shortcuts
    writeable = yes
;    browseable = yes
    valid users = belinda, george, mack

[Consultation's Shortcuts]
    path = /home/superuser1/Whitdata/Consultation's Shortcuts
    writeable = yes
;    browseable = yes
    valid users = consultation, davids, george, mack

[David Gamez's shortcuts]
    path = /home/superuser1/Whitdata/David Gamez's shortcuts
    writeable = yes
;    browseable = yes
    valid users = davidg, george, mack

[David strange's shortcuts]
    path = /home/superuser1/Whitdata/David strange's shortcuts
    writeable = yes
;    browseable = yes
    valid users = davids, george, mack

[daya's shortcuts]
    path = /home/superuser1/Whitdata/daya's shortcuts
    writeable = yes
;    browseable = yes
    valid users = davids, daya, george, mack

[Elba's Shortcuts]
    path = /home/superuser1/Whitdata/Elba's Shortcuts
    writeable = yes
;    browseable = yes
    valid users = davids, elba, george, mack

[Felipe's shortcuts]
    path = /home/superuser1/Whitdata/Felipe's shortcuts
    writeable = yes
;    browseable = yes
    valid users = felipe, george, mack

[George's shortcuts]
    path = /home/superuser1/Whitdata/George's shortcuts
    writeable = yes
;    browseable = yes
    valid users = davids, george, mack

[IO's Shortcuts]
    path = /home/superuser1/Whitdata/IO's Shortcuts
;    writeable = No
    browseable = no
    valid users = consultation, davids, george, mack

[Jeremy's shortcuts]
    path = /home/superuser1/Whitdata/Jeremy's shortcuts
    writeable = yes
;    browseable = yes
    valid users = george, jeremy, mack

[Marisela's shortcuts]
    path = /home/superuser1/Whitdata/Marisela's shortcuts
    writeable = yes
;    browseable = yes
    valid users = davids, george, mack, marisela

[Viri's Shortcuts]
    path = /home/superuser1/Whitdata/Viri's Shortcuts
    writeable = yes
;    browseable = yes
    valid users = george, mack, viri

[Whitbros' shortcuts]
    path = /home/superuser1/Whitdata/Whitbros' shortcuts
    writeable = yes
;    browseable = yes
    valid users = george, mack, whitbros

[Susan watson's shorcuts]
    path = /home/superuser1/Whitdata/Susan watson's shorcuts
    writeable = yes
;    browseable = yes
    valid users = davids, george, mack, susanw

[Kens-shortcuts]
    path = /home/superuser1/Whitdata/Kens-shortcuts
    writeable = yes
;    browseable = yes
    guest ok = yes
```

---

### Post by amngco on 2012-05-31
Also I don't know if it helps but the shares were setup using the system-config-samba package. don't know if that helps but thought I'd mention it.

---

### Post by CharlesA on 2012-05-31
> **amngco said:**
> Also I don't know if it helps but the shares were setup using the system-config-samba package. don't know if that helps but thought I'd mention it.
It shouldn't matter, the share definitions look ok.

Are you able to access the machine via IP from the Windows 7 box?

---

### Post by amngco on 2012-05-31
yes I can mount the machine, but I can't access the shares. They list, they ask for access authentication, then it can't find the network path. So i guess that the short answer is no.

---

### Post by CharlesA on 2012-05-31
> **amngco said:**
> yes I can mount the machine, but I can't access the shares. They list, they ask for access authentication, then it can't find the network path. So i guess that the short answer is no.
Does that occur for all shares?

Did you add the users to the samba server with:

```
sudo smbpasswd -a username
``` 

?

---

### Post by amngco on 2012-05-31
Yes all users are added and they all have correct passwords. and yes it happens to all the shares.

---

### Post by spynappels on 2012-05-31
Maybe not very helpful, but I found that when mapping a drive in Win7, it insisted in putting you in a domain when you entered a username. 

Putting a backslash before the username fixed that.

---

### Post by amngco on 2012-05-31
Well in this case it's using the domain name that identifies the computer in the network as the domain name and It's not in a textbox so I can't change it. Tried the backslash idea and it didn't work either.

---

### Post by CharlesA on 2012-05-31
> **amngco said:**
> Yes all users are added and they all have correct passwords. and yes it happens to all the shares.
Ok. Try this then:

Make a backup of the current smb.conf file and make a new one by copy/pasting this:

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


```

Add this share definition:

```
[TEST]
        browseable = yes
        path = /home/superuser1/Whitdata
        write list = someuser
        create mode = 660
        directory mode = 770

```

Change someuser to a valid user.

Then restart the smbd and nmbd daemons:

```
sudo service smbd restart
sudo service nmbd restart
```

EDIT:
> **spynappels said:**
> Maybe not very helpful, but I found that when mapping a drive in Win7, it insisted in putting you in a domain when you entered a username. 

Putting a backslash before the username fixed that.

I haven't noticed that with my Win7 boxes, but I have passwords synced up, so I'm not prompted for my password. :p

---

### Post by amngco on 2012-05-31
No good, still the exact same error. I guess that was an extract from a samba server that was working with it's windows 7 clients?

---

### Post by CharlesA on 2012-05-31
So the error is "network path not found" ?

Do this from the samba box:

```
ls -ld /home/superuser1/Whitdata
```

---

### Post by amngco on 2012-05-31
Yes that's the error. 
the command returned:

drwxrwxrw- 49 superuser1 sambashare 4096 2012-04-06 10:14 (highlighted in green) /home/superuser1/Whitdata

EDIT: It's saying the network name can't be found maybe that's some help?

---

### Post by CharlesA on 2012-05-31
OK, check the log then:

```
nano /var/log/samba/log.machninename
```

Where machinename is the name of the machine you are trying to connect from.

You can also try checking /var/log/samba/log.smbd:

```
tail /var/log/samba/log.smbd
```

---

### Post by amngco on 2012-05-31
[FONT=monospace]last entry (using the time stamp) says:
code:
[/FONT][2012/05/31 11:40:35.632661,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:35.634015,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:36.285568,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:36.287544,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:36.312314,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:36.314285,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:36.338839,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:36.340860,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:36.365950,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:36.367914,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:37.000771,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:37.002558,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:37.018868,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:37.031625,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:37.033589,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service TEST, path /home/superuser1/Whitdata
[2012/05/31 11:40:49.907987,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2012/05/31 11:40:49.908077,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.


log.smbd says:

standard input is not a socket, assuming -D option
[2012/05/31 11:36:36,  0] smbd/server.c:1123(main)
  smbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2012/05/31 11:36:36.691721,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option
[2012/05/31 11:40:25.598785,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2012/05/31 11:40:45.608827,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown

I got to go, if you come up with any more ideas keep posting. I'll try anything at this point.

---

### Post by CharlesA on 2012-05-31
Did you install the server with an encrypted home directory?

The error says it cannot access the directory for some reason.

Are the users added to the sambashare group, by chance?

---

### Post by Morbius1 on 2012-05-31
@CharlesA, I don't know if my eyes are failing me or not but this doesn't look right:
> [COLOR=Blue]**drwxrwxrw-** [/COLOR]49 superuser1 sambashare 4096 2012-04-06 10:14 (highlighted in green) /home/superuser1/WhitdataIf you take your test share:
> [TEST]
browseable = yes
path = /home/superuser1/Whitdata
write list = someuser
create mode = 660
directory mode = 770The only way "someuser" is going to get any kind of access is if he is a member of the "sambashare" group because the execute bit on /home/superuser1/Whitdata is turned off for "others". 

I guess it depends on how he created the users on the server.

[COLOR=Blue]EDIT[/COLOR]: Didn't read to the end of your post where you said the exact same thing in only 10 words :oops:

---

### Post by CharlesA on 2012-05-31
Ah, I missed the missing x bit on "ALL"
That would mess everything up for anyone that isn't superuser1 or in the sambashare group.

Good catch!

---

### Post by amngco on 2012-05-31
Well since ecryptfs-utils package isn't installed I would have to guess no. And yes all the users are added to the samba share group. 

And I don't know if you saw but I did say that the error has changed now. it now says that network NAME not found not network path. error code changed from 0x 80070035 to 0x 80070046. Don't know if I'm going backward or forward but there has been a change.

scratch that, It's back to network path now.

---

### Post by Morbius1 on 2012-05-31
Don't mean to beat a dead horse but move up the chain. The entire path to the share has to have the execute bit for "other" enabled. 

```
ls -al /home/superuser1
```Is /home or /home/superuser1 also at drwxrwxrw-.

---

### Post by amngco on 2012-05-31
Well Morbius I have a small problem with that. There is also a desire for off-site automatic backup, and if the home directories of the 2 machines are not restricted to the owner ssh will not auto authenticate. That was about a month of research and hacking to make work there.

You mentioned something about permissions made me decide to try something. If I try to map the samba share on the window 7 box, using the superuser1 name and password, I have full access to everything with no problems. The problem is that for some reason samba doesn't appear to recognize the  group permissions, therefore if the computer tries to use the logged in account credentials provided by windows it rejects them not allowing it to find the folder on the server. 
Is there and option that I can add to the smb.conf to allow that? or do I need to start adding owners to all the appropriate directories?

---

### Post by Morbius1 on 2012-05-31
Not sure I followed that. The only way a given user can access a shared folder is if the entire path can be traversed.

It appears as though /home/superuser1/Whitdata has the correct permissions as long as all remote users are members of the sambashare group:
> [COLOR=Blue]**drwxrwxrw-** [/COLOR]49 superuser1 sambashare 4096 2012-04-06 10:14 (highlighted in green) /home/superuser1/Whitdata                      But if /home/superuser1 is also at 776 or 756 or really XX6 then unless you changed the group to sambashare on /home/superuser1 no one will get to the Whitdata folder and beyond. The same thing will happen if you changed /home itself from the default 755.

Please post the output of:
```
ls -al /home
```

---

### Post by amngco on 2012-05-31
The output of 

Code:
ls -al /home
total 88
drwxr-xr-x 22 root         root         4096 2011-11-30 15:29 .
drwxr-xr-x 21 root         root         4096 2012-05-31 14:03 ..
drwxr-xr-x  2 ann          ann          4096 2011-08-31 13:34 ann
drwxr-xr-x  2 araceli      araceli      4096 2011-08-31 13:30 araceli
drwxr-xr-x  2 becky        becky        4096 2011-08-31 13:28 becky
drwxr-xr-x  2 belinda      belinda      4096 2011-08-31 13:29 belinda
drwxr-xr-x  2 consultation consultation 4096 2011-08-31 13:30 consultation
drwxr-xr-x  2 davidg       davidg       4096 2011-08-31 13:35 davidg
drwxr-xr-x  2 davids       davids       4096 2011-08-31 13:36 davids
drwxr-xr-x  2 daya         daya         4096 2011-08-31 13:29 daya
drwxr-xr-x  2 elba         elba         4096 2011-08-31 13:28 elba
drwxr-xr-x  2 felipe       felipe       4096 2011-08-31 13:42 felipe
drwxr-xr-x  2 george       george       4096 2011-08-31 13:44 george
drwxr-xr-x  2 jeremy       jeremy       4096 2011-09-24 13:23 jeremy
drwxr-xr-x  2         1019         1019 4096 2011-08-31 13:43 ken
drwxr-xr-x  2 mack         mack         4096 2011-08-31 13:34 mack
drwxr-xr-x  2 marisela     marisela     4096 2011-08-31 13:32 marisela
drwxr-xr-x  3 remoteuser1  remoteuser1  4096 2011-11-30 15:35 remoteuser1
drwxr--r-- 38 superuser1   sambashare   4096 2012-05-31 15:08 superuser1
drwxr-xr-x  2 susanw       susanw       4096 2011-09-26 15:16 susanw
drwxr-xr-x  2 viri         viri         4096 2011-08-31 13:28 viri
drwxr-xr-x  2 whitbros     whitbros     4096 2011-08-31 13:33 whitbros

---

### Post by amngco on 2012-05-31
Well I did what you said and changed the permissions on the home directory, now everything is working fine. Thanks for all your help. I've been walking into blank walls for weeks on this. A couple of things were taken offline but I can get them up and running again without too much trouble. Thanks again.

---

### Post by Morbius1 on 2012-05-31
It took so long to write a response you fixed it yourself.

---

### Post by amngco on 2012-05-31
Well I have to say thanks again it wasn't an easy walk but now we can  start using the server, which is a lot of ground covered from before.  Unfortunately somewhere along the way my users and permissions got  nuked, so I'm going to have to rebuild that, but compared to the  mountain I just crossed that will be easy. Thanks again for your help.

---

### Post by CharlesA on 2012-05-31
Glad you got it working and that it was a permissions issue.

Nice job Morbius! :)

If you are still having problems with backing up via ssh, start a new thread. :)

---

