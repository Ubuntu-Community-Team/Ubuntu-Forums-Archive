---
title: "Sub folder permissions generated in Windows"
date: 2013-04-11
forum: Server Platforms
---

### Post by thunter1995 on 2013-04-11
Hi Everyone.

This is my first post in this forum so I hope I'm getting this right.

I have just build a Ubuntu File server, (12.04) on a stand alone box for my business. I have 4 Windows 8 machines on the network. I have SAMBA running and have it setup so the group can access the server. I have created a folder that is called "CUSTOMERS" on the server and giving it group permissions to RWX.

Where my problem is, when someone creates a folder via their Windows machines and saves it to the CUSTOMERS Folder on the server, "THEY" are the only ones that have permissions to write to the folder. No one else in the group can use it. Is there a way to have all folders created by the group on their Windows machines have group permissions to RWX by default when saved to the server? In other words, the permissions that are used for the main folder are applied to all sub folders. 

Thank you in advance for your help. I'm really enjoy getting to know Ubuntu and Linux. 

Tom

---

### Post by trundlenut on 2013-04-11
Windows doesn't understand *nix file permissions therefore the parent folder permissions are applied to any new folders.


I think...

---

### Post by bab1 on 2013-04-11
> **thunter1995 said:**
> ... it. Is there a way to have all folders created by the group on their Windows machines have group permissions to RWX by default when saved to the server? In other words, the permissions that are used for the main folder are applied to all sub folders. 

Yes and no.  The group ownership is an Ubuntu group, not a Windows group.  You can set the GID so that the Ubuntu group ownership is inherited.  See [[COLOR="#FF0000"]**_here_**[/COLOR]]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for more info.  The permissions are set by default at 0775 for directories and 0664 for files by the *umask setting*.  To confirm this you can do this at the terminal prompt```
umask
```...this should return 0002.  

As the raw permissions are 0777 for directories, subtracting 0002 get you 0775.  Similarly 0666 for files and subtracting 0002 gets you 664.  The leading 0 is implied if not stated.  The leading 2 (e.g. 2775) is what sets the group inheritance (SGID). 

To set the group inheritance all you need to do is set the group ownership that you want on the shared directory (I user the group *users*  for that purpose).  The specific command is ```
sudo chgrp <group_name>  <directory_name>
```...This sets the group ownership of that directory.  If that directory is not under the current working directory you will need to supply the path to that directory (i.e. /path/to/the/directory) in the command.

Then you set the GID inheritance on that directory like this ```
sudo chmod 02775 <directory_name>
```...At this point any file or directory created will have the owner of the creator and the group that you applied (in my case it is the group *users*.  The only thing you need to do manually will be changing the GID and permissions of the existing files and directories in the share.

This type of inheritance is the default on UNIX hosts such as Solaris or the BSD distros.  Linux (and in particular Debian based distro's) you need to configure this.

If you don't understand this, please ask questions.  I will help you set this up.

---

### Post by thunter1995 on 2013-04-12
Hi Bab1
Thank you for taking the time to explain all this. 

I did study what you said and sort of have an idea of what you are talking about and I went though the steps you described.

Didn't fully understand the umask part of your post but will work on that.

I did the rest and it WORK! To a point&#8230; after running sudo chmon 02775 now all the directories the group creates and drop onto the subfolder on the sever have the group name that is carried in the main folder, but it only has r-x privileges. The group privileges for the mail folder are rwx. I think you mentioned this was going to happen and I would have to manually go in there and change the permissions to 0775 for every new folder created which really defeats the purpose of what I&#8217;m trying to do. I want people on their windows machines to create and save files and folder to the server where others can modify. 

Maybe this can&#8217;t be done? But if every time a file/folder is created I have to manually change the permissions&#8230; life will get very tedious.

Again thank you for your help. It does give me a better understanding of what is going on and I&#8217;ll re-read it again to be sure I&#8217;m doing everything right.

---

### Post by bab1 on 2013-04-12
> **thunter1995 said:**
> Hi Bab1
Thank you for taking the time to explain all this. 

I did study what you said and sort of have an idea of what you are talking about and I went though the steps you described.

Didn't fully understand the umask part of your post but will work on that.

I did the rest and it WORK! To a point… after running sudo chmon 02775 now all the directories the group creates and drop onto the subfolder on the sever have the group name that is carried in the main folder, but it only has r-x privileges. The group privileges for the mail folder are rwx. I think you mentioned this was going to happen and I would have to manually go in there and change the permissions to 0775 for every new folder created which really defeats the purpose of what I’m trying to do. I want people on their windows machines to create and save files and folder to the server where others can modify. 

You have to be very precise, not just close.  The command is umask -- not unmask.  The tool chmod also has a d at the end not n at the end (chmod not chmon).  If you set a folders permissions to 0775 you loose the inheritance.  It must start with 2 (i.e 2775 not 0775). 

There also is a a difference between copying a file to the folder and creating a file in the folder that is shared.
> 

Maybe this can’t be done? But if every time a file/folder is created I have to manually change the permissions… life will get very tedious.

Again thank you for your help. It does give me a better understanding of what is going on and I’ll re-read it again to be sure I’m doing everything right.
I think there are other considerations that are affecting your setup.  The umask is a tricky thing to get right, but it can be done.  Post the output of the directory that we are dealing with.  The directory itself can be shown with this ```
ls -ld <path to the directory>
```
The contents can be shown with this command ```
ls -l <path to the directory>
```

NOTE: these are two different commands.

---

### Post by thunter1995 on 2013-04-13
Hi Bab1

You're right about getting the spelling right. I Did see the error on umask vs. unmask. And I did the chmod right, just didn't type it right in my response. 

I will try to send you a screen cap of the directory output to see what is going on. I did do some reading and I "think" where I need to get to is the umask setting. If I can figure out how to set the parent folder's umask bit, it should apply to all folders/files created in Windows and saved on the Ubuntu server so anyone in the group with that folders permissions, will be able to edit.

Im also wondering if something in SAMBA could do this? I'm not sure what the big deal is with SAMBA when it comes to setting rwx settings since chmod over-writes whatever you set in SAMBA? To me, SAMBA, main purpose is to allow windows users to connect to the server. I could be all wrong in this (good money says I am...) about SAMBA.

Thanks again for your time and help on this. I will let you know what the directory tree and settins are. BTW my umask no. 002

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> Hi Bab1

You're right about getting the spelling right. I Did see the error on umask vs. unmask. And I did the chmod right, just didn't type it right in my response. 

I will try to send you a screen cap of the directory output to see what is going on. I did do some reading and I "think" where I need to get to is the umask setting. If I can figure out how to set the parent folder's umask bit, it should apply to all folders/files created in Windows and saved on the Ubuntu server so anyone in the group with that folders permissions, will be able to edit.

Unfortunately you can't set umask on individual directories (folders).  But, you can set umask in Samba for individual shares.  I personally like to get as much of this done at the system level (O/S) before setting the final bits at the Samba level.> 

Im also wondering if something in SAMBA could do this? I'm not sure what the big deal is with SAMBA when it comes to setting rwx settings since chmod over-writes whatever you set in SAMBA? To me, SAMBA, main purpose is to allow windows users to connect to the server. I could be all wrong in this (good money says I am...) about SAMBA.
Like I said above Samba is very configurable.  I need to see the settings you have so I can advise how to re-create (or modify) the share you created.
> 

Thanks again for your time and help on this. I will let you know what the directory tree and settins are. BTW my umask no. 002
It might be a good idea to post  the following ```
cat /etc/samba/smb.conf
```...and ```
net usershare info --long
```...and ```
smbtree
```...as well as what I asked for before.  ;-)

---

### Post by thunter1995 on 2013-04-13
Hi Bab1

Below is the output you wanted to see: (I hope)

drwxrwxrwT 5 tom sbtgroup 4096 Apr 13 09:16 /srv/data
tom@SBTG-SERVER1:/srv/data$ ls -l /srv/data
total 24
drwxr-xr-x  4 cindy cindy 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxr--r--  1 cindy cindy 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxr-xr-x 11 cindy cindy 4096 Apr 13 09:16 SBT Graphics Info
drwxr-xr-x  3 cindy cindy 4096 Apr 12 23:24 Scan Images
tom@SBTG-SERVER1:/srv/data$

Just to be clear. the Folder /srv/data has sbtgroup permissions. When "cindy" creates a folder with files on a windows machine and copies them to the /srv/data folder, "She" is the only one who has permissions to those files.

Let me know if there is anything more you need. 

Thanks again for your help

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> Hi Bab1

Below is the output you wanted to see: (I hope)

drwxrwxrwT 5 tom sbtgroup 4096 Apr 13 09:16 /srv/data
tom@SBTG-SERVER1:/srv/data$ ls -l /srv/data
total 24
drwxr-xr-x  4 cindy cindy 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxr--r--  1 cindy cindy 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxr-xr-x 11 cindy cindy 4096 Apr 13 09:16 SBT Graphics Info
drwxr-xr-x  3 cindy cindy 4096 Apr 12 23:24 Scan Images
tom@SBTG-SERVER1:/srv/data$

Just to be clear. the Folder /srv/data has sbtgroup permissions. When "cindy" creates a folder with files on a windows machine and copies them to the /srv/data folder, "She" is the only one who has permissions to those files.

Let me know if there is anything more you need. 

Thanks again for your help

Hmmm, not what I expected to see...

When posting data please put the data between the ```
 blocks (use the # icon at the top for that)

This is not chmod 2775
[CODE]drwxrwxrwT 5 tom sbtgroup 4096 Apr 13 09:16 /srv/data
```... what did you use to get this?

If I were to chmod 2775 a directory named public it looks like this```
drwxrwsr-x  2 bab [COLOR="#FF0000"]users[/COLOR] 4.0K Apr 13 16:52 public
```...note that I also changed the group to *[COLOR="#FF0000"]**users**[/COLOR]*.  Does the sbtgroup hold the all the users you want?  What is the output of ```
getent group sbtgroup
```

Why didn't the user cindy have the SGID for the group sbtgroup in this directory?

Where are the rest of the items I asked for in my last post?

---

### Post by thunter1995 on 2013-04-13
Bab1 Here is the smb.conf output
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
 
[SBT Files]
        comment = Where we keep everything
        path = /srv/
        read only = no
        writable = yes
        browsable = yes
        user = sbtgroup
 
[Data]
        comment = Where the customer files live
        path = /data
        readonly = no
        writable = yes
        browsable = yes
        valid users = @sbtgroup
 
[NTFS Drive]
        comment = This is a 2TB NTFS drive
        path = /media/data
        read only = no
        writeable = yes
        browsable = yes
        guest ok = no
        valid users = @sbtgroup

---

### Post by thunter1995 on 2013-04-13
The getent output

#
tom@SBTG-SERVER1:~$ getent group sbtgroup
sbtgroup:x:1004:carlos,tom,cindy

I hope I'm getting the [code] block set right to copy in here? 

Thanks Bab1

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> Bab1 Here is the smb.conf output

**[COLOR="#FF0000"]Let's use the ```
 blocks PLEASE!!![/COLOR]** 
It would look like this  :-)> 
[CODE]#
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
 
[SBT Files]
        comment = Where we keep everything
        path = /srv/
        read only = no
        writable = yes
        browsable = yes
        user = sbtgroup
 
[Data]
        comment = Where the customer files live
        path = /data
        readonly = no
        writable = yes
        browsable = yes
        valid users = @sbtgroup
 
[NTFS Drive]
        comment = This is a 2TB NTFS drive
        path = /media/data
        read only = no
        writeable = yes
        browsable = yes
        guest ok = no
        valid users = @sbtgroup
```

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> The getent output

#
tom@SBTG-SERVER1:~$ getent group sbtgroup
sbtgroup:x:1004:carlos,tom,cindy

I hope I'm getting the [code] block set right to copy in here? 

Thanks Bab1

Nope, the [code] block icon is at the top of the editor (3rd from the right on the second row).

---

### Post by thunter1995 on 2013-04-13
Sorry if I'm sending you the code block wrong Bab1. Not sure where the "Switch" is here that I should be pushing before I copy/past the output to the post.

---

### Post by thunter1995 on 2013-04-13
```
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
 
[SBT Files]
        comment = Where we keep everything
        path = /srv/
        read only = no
        writable = yes
        browsable = yes
        user = sbtgroup
 
[Data]
        comment = Where the customer files live
        path = /data
        readonly = no
        writable = yes
        browsable = yes
        valid users = @sbtgroup
 
[NTFS Drive]
        comment = This is a 2TB NTFS drive
        path = /media/data
        read only = no
        writeable = yes
        browsable = yes
        guest ok = no
        valid users = @sbtgroup

```

---

### Post by thunter1995 on 2013-04-13
Found the switch. Was using the "Post Quick Reply" and didn't see this. 

Ok, what can I give you now that will help?

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> Bab1 Here is the smb.conf output
#
```

 
[SBT Files]
        comment = Where we keep everything
        path = /srv/
        read only = no
        writable = yes
        browsable = yes
        user = sbtgroup
 
[Data]
        comment = Where the customer files live
        path = /data
        readonly = no
        writable = yes
        browsable = yes
        valid users = @sbtgroup
 
[NTFS Drive]
        comment = This is a 2TB NTFS drive
        path = /media/data
        read only = no
        writeable = yes
        browsable = yes
        guest ok = no
        valid users = @sbtgroup
```

These shares don't look right either.  Based on what you said the share should be at /srv/data.  It doesn't have to be, but that is what you showed me earlier.

So let's start at the very beginning.  I guess we need to create a test directory to share.  Do you have all of the data backed up somewhere else?

---

### Post by thunter1995 on 2013-04-13
yea, this is all TEST I haven't made the server LIVE yet.

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> yea, this is all TEST I haven't made the server LIVE yet.

Then I suggest we start with the /srv/data directory.

You can cut and paste my commands.  First we need to see the /srv structure.  Post the output of ```
ls -ld /srv
```

Also post the output of ```
ls -ld /srv/data
```

And also the output of ```
ls -l /srv/data
```

Note the last 2 commands are different.  I want to see all 3 of them.

---

### Post by thunter1995 on 2013-04-13
Here is the smb tree you wanted to see

```
WORKGROUP
        \\GINGER
HOMEGROUP
        \\GOFLEX_HOME                   GoFlex Home
                \\GOFLEX_HOME\GoFlex_Home       GoFlex Home usb port
                \\GOFLEX_HOME\IPC$              IPC Service (GoFlex Home)
                \\GOFLEX_HOME\External Storage  GoFlex Home (External Storage)
                \\GOFLEX_HOME\GoFlex Home Public        GoFlex Home (GoFlex Home Public)
                \\GOFLEX_HOME\GoFlex Home Backup        GoFlex Home (GoFlex Home Backup)
                \\GOFLEX_HOME\GoFlex Home Personal      GoFlex Home (GoFlex Home Personal)
HOME
        \\TOMS_VAIO                     toms_Vaio_notebook
                \\TOMS_VAIO\Users
                \\TOMS_VAIO\IPC$                Remote IPC
                \\TOMS_VAIO\C$                  Default share
                \\TOMS_VAIO\ADMIN$              Remote Admin
        \\TOM-PC
                \\TOM-PC\Users
                \\TOM-PC\Share folder
                \\TOM-PC\SBT Backup Drive       Customer and Data backup
                \\TOM-PC\print$                 Printer Drivers
                \\TOM-PC\Photo Drive            Where Tom keeps his photos
                \\TOM-PC\IPC$                   Remote IPC
                \\TOM-PC\F$                     Default share
                \\TOM-PC\EPSON Stylus Photo 1400 Series EPSON Stylus Photo 1400 Series
                \\TOM-PC\E$                     Default share
                \\TOM-PC\E
                \\TOM-PC\CF Card PC             CF Card in PC
                \\TOM-PC\CF Card
                \\TOM-PC\C$                     Default share
                \\TOM-PC\ADMIN$                 Remote Admin
        \\SBTG-SERVER1                  SBTG-SERVER1 server (Samba, Ubuntu)
                \\SBTG-SERVER1\IPC$             IPC Service (SBTG-SERVER1 server (Samba, Ubuntu))
                \\SBTG-SERVER1\NTFS Drive       This is a 2TB NTFS drive
                \\SBTG-SERVER1\Data             Where the customer files live
                \\SBTG-SERVER1\SBT Files        Where we keep everything
                \\SBTG-SERVER1\print$           Printer Drivers
        \\CINDY-PC                      CIndy's PC

```

---

### Post by bab1 on 2013-04-13
I thought we were starting over.  :-(

I'm confused.  Why do we need smbtree at this point?

---

### Post by thunter1995 on 2013-04-13
Sorry Bab1 Just saw this was something I failed to send you before and thought you might want it. I'm all set to start over.

---

### Post by bab1 on 2013-04-13
See post #19 of this thread.

---

### Post by thunter1995 on 2013-04-13
Ok, here is the info from post 19 you requested bab1

```

tom@SBTG-SERVER1:~$ ls -ld /srv
drwxr-xr-x 9 root root 4096 Apr 10 06:43 /srv
tom@SBTG-SERVER1:~$

tom@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxr-xr-x  4 cindy cindy 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxr--r--  1 cindy cindy 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxr-xr-x 11 cindy cindy 4096 Apr 13 09:16 SBT Graphics Info
drwxr-xr-x  3 cindy cindy 4096 Apr 12 23:24 Scan Images
tom@SBTG-SERVER1:~$

tom@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxr-xr-x  4 cindy cindy 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxr--r--  1 cindy cindy 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxr-xr-x 11 cindy cindy 4096 Apr 13 09:16 SBT Graphics Info
drwxr-xr-x  3 cindy cindy 4096 Apr 12 23:24 Scan Images
tom@SBTG-SERVER1:~$

```

I hope I got all you need bab1. Thanks again for helping me out.

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> Ok, here is the info from post 19 you requested bab1

```

tom@SBTG-SERVER1:~$ ls -ld /srv
drwxr-xr-x 9 root root 4096 Apr 10 06:43 /srv
tom@SBTG-SERVER1:~$

tom@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxr-xr-x  4 cindy cindy 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxr--r--  1 cindy cindy 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxr-xr-x 11 cindy cindy 4096 Apr 13 09:16 SBT Graphics Info
drwxr-xr-x  3 cindy cindy 4096 Apr 12 23:24 Scan Images
tom@SBTG-SERVER1:~$

tom@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxr-xr-x  4 cindy cindy 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxr--r--  1 cindy cindy 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxr-xr-x 11 cindy cindy 4096 Apr 13 09:16 SBT Graphics Info
drwxr-xr-x  3 cindy cindy 4096 Apr 12 23:24 Scan Images
tom@SBTG-SERVER1:~$

```

I hope I got all you need bab1. Thanks again for helping me out.

Let's change the group ownership on the directory /srv/data.  We can do that with this command```
sudo chgrp -R sbtgroup /srv/data 
```

Show me the output of this command```
ls -l /srv/data
```

---

### Post by thunter1995 on 2013-04-13
Here it is

```
tom@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxr-xr-x  4 cindy sbtgroup 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxr--r--  1 cindy sbtgroup 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxr-xr-x 11 cindy sbtgroup 4096 Apr 13 09:16 SBT Graphics Info
drwxr-xr-x  3 cindy sbtgroup 4096 Apr 12 23:24 Scan Images
tom@SBTG-SERVER1:~$


```

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> Here it is

```
tom@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxr-xr-x  4 cindy sbtgroup 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxr--r--  1 cindy sbtgroup 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxr-xr-x 11 cindy sbtgroup 4096 Apr 13 09:16 SBT Graphics Info
drwxr-xr-x  3 cindy sbtgroup 4096 Apr 12 23:24 Scan Images
tom@SBTG-SERVER1:~$


```

Now we will change the basic permissions for the directories and files with this command ```
sudo chmod -R u=rwX,g=rwX,o=rX /srv/data
```

Post me the output of these 3 commands```
ls -l /srv/data

ls -l /srv/data/"SBT Graphics Info"

ls -l /srv/data/"Scan Images"


```

---

### Post by thunter1995 on 2013-04-13
WOW! I think this worked Bab1
```
tomr@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxrwxr-x  4 cindy sbtgroup 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxrwxr-x  1 cindy sbtgroup 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxrwxr-x 11 cindy sbtgroup 4096 Apr 13 09:16 SBT Graphics Info
drwxrwxr-x  3 cindy sbtgroup 4096 Apr 12 23:24 Scan Images
tomr@SBTG-SERVER1:~$
 
2a
tomr@SBTG-SERVER1:~$ ls -l /srv/data/"SBT Graphics Info"
total 424
-rwxrwxr-x 1 cindy sbtgroup    165 Oct  3  2009 ~$2009 SBT  Numbers wrk2.xlsm
-rwxrwxr-x 1 cindy sbtgroup 101111 Dec  1  2010 2010 Planner.xlsx
drwxrwxr-x 2 cindy sbtgroup   4096 Apr 13 00:48 Backup Forms
drwxrwxr-x 3 cindy sbtgroup   4096 Apr 13 00:48 Current Quotes
-rwxrwxr-x 1 cindy sbtgroup     78 Apr  2  2007 Desktop.ini
-rwxrwxr-x 1 cindy sbtgroup  63113 Sep  6  2009 Excel shortcut and function...pdf
drwxrwxr-x 3 cindy sbtgroup   4096 Apr 13 00:48 Forecast
drwxrwxr-x 6 cindy sbtgroup   4096 Apr 13 00:48 Old Spreadsheets
drwxrwxr-x 2 cindy sbtgroup   4096 Apr 13 00:48 Price Caculators
drwxrwxr-x 9 cindy sbtgroup   4096 Apr 13 00:48 Sales Tax
drwxrwxr-x 2 cindy sbtgroup   4096 Apr 13 00:48 SBT Banking Websites
drwxrwxr-x 2 cindy sbtgroup   4096 Apr 13 00:48 SBTG Homework
-rwxrwxr-x 1 cindy sbtgroup 140288 Sep 29  2012 SBTG Sales track 2011.xls
-rwxrwxr-x 1 cindy sbtgroup  59485 Apr 15  2011 SBTG Sales track 2011.xlsx
-rwxrwxr-x 1 cindy sbtgroup    638 Oct 13  2005 Shortcut to Area Code Lookup.lnk
-rwxrwxr-x 1 cindy sbtgroup   3181 Apr 17  2011 sync.ffs_db
drwxrwxr-x 2 cindy sbtgroup   4096 Apr 13 00:48 Tax Forms
-rwxrwxr-x 1 cindy sbtgroup   5632 Apr  2  2007 Thumbs.db
tomr@SBTG-SERVER1:~$
 
3a
tomr@SBTG-SERVER1:~$ ls -l /srv/data/"Scan Images"
total 744
drwxrwxr-x 2 cindy sbtgroup   4096 Apr 12 23:24 archive
-rwxrwxr-x 1 cindy sbtgroup 402893 Mar 25 10:18 Jennifer.pdf
-rwxrwxr-x 1 cindy sbtgroup  81610 Mar 12 11:11 MIchael R..pdf
-rwxrwxr-x 1 cindy sbtgroup  67638 Mar 27 14:13 Nusign Plotter invoice.pdf
-rwxrwxr-x 1 cindy sbtgroup  85924 Mar 20 10:45 Pac lease.pdf
-rwxrwxr-x 1 cindy sbtgroup 113310 Feb 26 12:42 sbtstatefundforms.pdf
tomr@SBTG-SERVER1:~$

```

I want to test this by having "Cindy" create a folder with files and drop it in, but I'll wait to hear from you.

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> ...

I want to test this by having "Cindy" create a folder with files and drop it in, but I'll wait to hear from you.

We need to do one last thing.  We need to set the group inheritance (SGID) on the /srv/data directory.  To do that  we need to do this```
sudo chmod 2775 /srv/data
```

What is the output of this command ```
ls -ld /srv/data
```

If this works we can do some tests.  DO NOT TEST ANYTHING NOW!  I will show you that if this is successful.

---

### Post by thunter1995 on 2013-04-13
Not doing anything tell you say so Bab1.
Here it is

```
tomr@SBTG-SERVER1:~$ sudo chmod 2775 /srv/data
tomr@SBTG-SERVER1:~$ ls -ld /srv/data
drwxrwsr-x 5 tom sbtgroup 4096 Apr 13 19:33 /srv/data
tomr@SBTG-SERVER1:~$


```

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> Not doing anything tell you say so Bab1.
Here it is

```
tomr@SBTG-SERVER1:~$ sudo chmod 2775 /srv/data
tomr@SBTG-SERVER1:~$ ls -ld /srv/data
drwxrw**[COLOR="#FF0000"]s[/COLOR]**r-x 5 tom sbtgroup 4096 Apr 13 19:33 /srv/data
tomr@SBTG-SERVER1:~$


```

We are 1/2 way there.  The red S above is the SGID bit.  The server is configured!  You can test this by creating a 0 byte file like this ```
touch /srv/data/testfile
``` 

Post the output of ```
ls -l /srv/data
```...you should see the file *testfile* and the group should be *sbtgroup*.  The permissions should be rw-rw-r-- (0664).

DO NOT TRY SAMBA JUST YET!

---

### Post by thunter1995 on 2013-04-13
Here are the results

```
tom@SBTG-SERVER1:~$ touch /srv/data/testfile
tom@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxrwxr-x  4 cindy sbtgroup 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxrwxr-x  1 cindy sbtgroup 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxrwxr-x 11 cindy sbtgroup 4096 Apr 13 09:16 SBT Graphics Info
drwxrwxr-x  3 cindy sbtgroup 4096 Apr 12 23:24 Scan Images
-rw-rw-r--  1 tom   sbtgroup    0 Apr 13 20:33 testfile


```

---

### Post by bab1 on 2013-04-13
> **thunter1995 said:**
> Here are the results

```
tom@SBTG-SERVER1:~$ touch /srv/data/testfile
tom@SBTG-SERVER1:~$ ls -l /srv/data
total 24
drwxrwxr-x  4 cindy sbtgroup 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxrwxr-x  1 cindy sbtgroup 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxrwxr-x 11 cindy sbtgroup 4096 Apr 13 09:16 SBT Graphics Info
drwxrwxr-x  3 cindy sbtgroup 4096 Apr 12 23:24 Scan Images
**[COLOR="#FF0000"]-rw-rw-r--  1 tom   sbtgroup    0 Apr 13 20:33 testfile[/COLOR]**


```

So it worked!  See the line highlighted in red.

The reason we do all of this is so that if you add a file or directory from the Ubuntu host, all the Samba users will be able to use it.  The configuration in Samba will be for users adding, modifying or deleting files remotely from a Samba client. 

Now we need to modify the smb.conf file.  We can edit the file with a graphical editor (gedit) with this command```
gksudo gedit /etc/samba/smb.conf
```

Go to the shares section and replace this```
[SBT Files]
comment = Where we keep everything
path = /srv/
read only = no
writable = yes
browsable = yes
user = sbtgroup
```... with this
```

[SBT Files]
comment = Where we keep everything
        path = /srv/data                       # the shared directory
        browseable = yes
       valid users = @sbtgroup
        force group = sbtgroup
        writeable = yes
        create mask = 0664                  #file permissions (the umask)
        force directory mode = 2775     # directory permissions


``` 

The directory we are sharing is controlled by the group.  The /srv directory is owned by root.  The only thing a user can do is read the contents or descend into /srv/data.  That's why you don't share /srv but you do share /srv/data.

We set these parameters in smb.conf for Samba users.  This should make any file created either by an Ubuntu user or a Samba user have the same permissions.

After you have edited the smb.conf file you need to restart the Samba server (smbd).  Yo do that with this command```
sudo service smbd restart
```

Now see if the share is working.  Can you add data to the directories?  Who is the group owner?  What are the permissions?

---

### Post by thunter1995 on 2013-04-14
It almost worked. I created folders on two Windows computers and inside those folders I dropped a test text file. I then saved those Folders to the server /srv/data. When I tried to edit the text files, it won't let me as the permission for those files in the group is r-- (See output below for tomtest doc.txt

```
root@SBTG-SERVER1:/home/tom# ls -l /srv/data
total 32
drwxrwsr-x  2 cindy sbtgroup 4096 Apr 13 21:12 CINDY MADE THIS
drwxrwxr-x  4 cindy sbtgroup 4096 Apr 13 09:45 Cindy's Old Computer Stuff
-rwxrwxr-x  1 cindy sbtgroup 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf
drwxrwxr-x 11 cindy sbtgroup 4096 Apr 13 09:16 SBT Graphics Info
drwxrwxr-x  3 cindy sbtgroup 4096 Apr 12 23:24 Scan Images
-rw-rw-r--  1 tom   sbtgroup    0 Apr 13 20:33 testfile
drwxrwsr-x  2 tom   sbtgroup 4096 Apr 13 21:09 TOM MADE THIS
root@SBTG-SERVER1:/home/tom# cd /srv/data/"TOM MADE THIS"
root@SBTG-SERVER1:/srv/data/TOM MADE THIS# ll
total 8
drwxrwsr-x 2 tom sbtgroup 4096 Apr 13 21:09 ./
drwxrwsr-x 7 tom sbtgroup 4096 Apr 13 21:10 ../
-rwxr--r-- 1 tom sbtgroup    0 Apr 13 21:08 Tomtest doc.txt*
root@SBTG-SERVER1:/srv/data/TOM MADE THIS#


```

---

### Post by bab1 on 2013-04-14
Did you restart Samba (smbd)?

---

### Post by thunter1995 on 2013-04-14
Wait saw an error in my smb.conf let me try it again

---

### Post by bab1 on 2013-04-14
> **thunter1995 said:**
> ... When I tried to edit the text files, it won't let me as the permission for those files in the group is r-- (See output below for tomtest doc.txt

```

-rwxr--r-- 1 tom sbtgroup    0 Apr 13 21:08 Tomtest doc.txt*
root@SBTG-SERVER1:/srv/data/TOM MADE THIS#


```
You should have been able to edit it anyway as it is owned by the user tom ( I assume that is who you are logged in as).

---

### Post by bab1 on 2013-04-14
> **thunter1995 said:**
> Wait saw an error in my smb.conf let me try it again

Ah ha...

Computers can't think.  You supply the brains.  :)

Post what you put in the share definition.

---

### Post by thunter1995 on 2013-04-14
HOORAY!!!!!! You're the greatest bab1 it WORKS!!!!!

```
rroot@SBTG-SERVER1:/srv/data# ll
total 40
drwxrwsr-x  7 tom   sbtgroup 4096 Apr 13 21:32 ./
drwxr-xr-x  9 root  root     4096 Apr 10 06:43 ../
drwxrwxr-x  4 cindy sbtgroup 4096 Apr 13 09:45 Cindy's Old Computer Stuff/
drwxrwsr-x  2 cindy sbtgroup 4096 Apr 13 21:32 Cindy_test2/
-rwxrwxr-x  1 cindy sbtgroup 9950 Apr 12 11:21 Invoices 9316427, 9316428.pdf*
drwxrwxr-x 11 cindy sbtgroup 4096 Apr 13 09:16 SBT Graphics Info/
drwxrwxr-x  3 cindy sbtgroup 4096 Apr 12 23:24 Scan Images/
-rw-rw-r--  1 tom   sbtgroup    0 Apr 13 20:33 testfile
drwxrwsr-x  2 tom   sbtgroup 4096 Apr 13 21:30 Tom_made_this_II/
root@SBTG-SERVER1:/srv/data# ^C
root@SBTG-SERVER1:/srv/data# cd /srv/data/Cindy_test2
root@SBTG-SERVER1:/srv/data/Cindy_test2# ll
total 12
drwxrwsr-x 2 cindy sbtgroup 4096 Apr 13 21:32 ./
drwxrwsr-x 7 tom   sbtgroup 4096 Apr 13 21:32 ../
-rw-rw-r-- 1 cindy sbtgroup   24 Apr 13 21:33 Cindy test.txt
root@SBTG-SERVER1:/srv/data/Cindy_test2#

```

---

### Post by bab1 on 2013-04-14
Great.  We can make you a guide so you can replicate it for other shares.

---

### Post by thunter1995 on 2013-04-14
The guide would be great! The last problem was in my smb.conf file I misspelled "create" was the problem. Thanks again for all your help.

---

### Post by bab1 on 2013-04-15
> **thunter1995 said:**
> The guide would be great! The last problem was in my smb.conf file I misspelled "create" was the problem. Thanks again for all your help.
 I have attached a guide to what we have been talking about.

---

### Post by thunter1995 on 2013-04-15
This looks GREAT Bab1. THANK YOU AGAIN. I read the doc and it makes sense to me. What I need to do is try it out and insure I got it right. I've done a couple since last we talked, but haven't tried where I "Limit" what users in the group can do. It's rare that I would need that as I would control most access rights by who I allow in the group(s) but I can figure that out. Of all the reading I've seen about setting up shares in SAMBA, I never saw the command: "force group." I'm not about to argue with how you make it work, but just curious if this is something unique to how "You" set things up?

---

### Post by thunter1995 on 2013-04-15
This looks GREAT Bab1. THANK YOU AGAIN. I read the doc and it makes sense to me. What I need to do is try it out and insure I got it right. I've been a couple since last we talked, but haven't tried where I "Limit" what users in the group can do. It's rare that I would need that as I would control most access writes by who I allow in the group(s) but I can figure that out. Of all the reading I've seen about setting up shares in SAMBA, I never saw the command: "force group." I'm not about to argue with how you make it work, but just curious if this is something unique to how "You" set things up?

---

### Post by bab1 on 2013-04-15
> **thunter1995 said:**
> This looks GREAT Bab1. THANK YOU AGAIN. I read the doc and it makes sense to me. What I need to do is try it out and insure I got it right. I've done a couple since last we talked, but haven't tried where I "Limit" what users in the group can do. It's rare that I would need that as I would control most access rights by who I allow in the group(s) but I can figure that out. Of all the reading I've seen about setting up shares in SAMBA, I never saw the command: "force group." I'm not about to argue with how you make it work, but just curious if this is something unique to how "You" set things up?

If you read the man page for smb.conf you will see this```
 force group (S)

           This specifies a UNIX group name that will be assigned as the default primary group
           for all users connecting to this service. This is useful for sharing files by ensuring
           that all access to files on service will use the named group for their permissions
           checking. Thus, by assigning permissions for this group to the files and directories
           within this service the Samba administrator can restrict or allow sharing of these
           files.

```

Most people stumble through howto's and never read the actual documentation.  ;-)

---

### Post by thunter1995 on 2013-04-15
Ya know I did buy a book, The "Official Ubuntu Server Guide" 2nd edition and no mention of "Force Group" was found. LOL

---

### Post by bab1 on 2013-04-15
> **thunter1995 said:**
> Ya know I did buy a book, The "Official Ubuntu Server Guide" 2nd edition and no mention of "Force Group" was found. LOL

The best documentation for Samba comes from Samba.org.  :-)

---

