---
title: "permission changed when copying files over samba"
date: 2015-06-09
forum: Server Platforms
---

### Post by weirdinin on 2015-06-09
Hi. I have headless Ubuntu 14.04.2 LTS and having difficulties with  permissions while using samba. When I create a folder using win 7  machine, permissions are set as rwxrwx---. And that's how I want it.  However, when I remove or copy that folder to another location (again  using win7), permissions are changed to rwxr-x---.

For example: I created a folder "test1" in /media/flexraidpool/public.  Then I created another folder "test2" in  /media/flexraidpool/shared/video. Both have rwxrwx---. Then I cut and  paste "testi1" to "testi2". Now permissions of "testi1" are rwxr-x---.  Why?

If I remove "test1" inside the same parent folder, permissions are not changed. E.g if I remove it to /media/flexraidpool/public/random_folder/. Permission are changed only, if I remove "test1" to another samba share location like in the first example.

umask gives 0002.

This is my smb.conf: 

[public]
comment = public folder
path = /media/flexraidpool/public
browseable = yes
read only = no
public = no
guest ok = no
valid users = @publicgroup
force group = publicgroup
directory mask = 0770
create mask = 0770

[video]
comment = video
path = /media/flexraidpool/shared/video
browsable = yes
read only = no
public = no
guest ok = no
valid users = @videogroup
force group = videogroup
force directory mode = 0770
directory mask = 0770
create mask = 0770

Thank you for your help. Tell me please if I need to provide more details.

---

### Post by TheFu on 2015-06-09
Please post```

ls -ald  /media/flexraidpool/public
ls -ald /media/flexraidpool/shared/video
```

Mine is 
```
thefu@c720:/D$ ls -ald /D
drwxrws--- 10 thefu video 4096 Apr 23 07:46 /D/
```

Are the file systems used the same? Not NTFS? 

Would be good to check the group membership and make the top level directory **chmod g+s** for both directories from inside Linux.
**id** will show the real group membership for each account. Can't hurt to check that video and publicgroup members are really in the group.

 I'm reaching here for all of this. The smb.conf file looks ok, at least what you've shown of it. The global settings would be useful too.

---

### Post by weirdinin on 2015-06-14
Sorry for replying so late, I've been very busy.  and thank you for your help.

```
weirdinin@ubuntu:/media/flexraidpool/shared/video$ ls -ald /media/flexraidpool/public/
drwxrwx--- 5 weirdinin publicgroup 4096 heinä 24  2014 /media/flexraidpool/public/
```

```
weirdinin@ubuntu:/media/flexraidpool/shared/video$ ls -ald /media/flexraidpool/shared/video/
drwxrws--- 6 weirdinin videogroup 4096 marra 17  2014 /media/flexraidpool/shared/video/
```

```
weirdinin@ubuntu:/media/flexraidpool/shared/video$ cat /etc/samba/smb.conf
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
   workgroup = PUISTOKOTI

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

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
#   include = /etc/samba/smb.conf.yavdr.recordings
#   include = /etc/samba/smb.conf.custom



[video]
comment = video
path = /media/flexraidpool/shared/video
browsable = yes
read only = no
public = no
guest ok = no
valid users = @videogroup
force group = videogroup
force directory mode = 0770
directory mask = 0770
create mask = 0770

[game]
comment = game
path = /media/flexraidpool/game
read only = no
public = no
guest ok = no
valid users = @gamegroup
force group = gamegroup
directory mask = 0770
create mask = 0770

[picture]
comment = pictures
path = /media/flexraidpool/shared/pictures
read only = no
public = no
guest ok = no
write list = @picturegroup
read list = @picturegroup
create mask = 0770
directory mask = 0770

[public]
comment = public folder
path = /media/flexraidpool/public
browseable = yes
read only = no
public = no
guest ok = no
valid users = @publicgroup
force group = publicgroup
directory mask = 0770
create mask = 0770

[P2P]
comment = download folder
path = /var/lib/deluge/p2p
browseable = yes
read only = no
public = no
guest ok = no
valid users = @deluge
force group = deluge
directory mask = 0770
create mask = 0770

[audio]
comment = audio
path = /media/flexraidpool/audio
browseable = yes
read only = no
public = no
guest ok = no
valid users = @audiogroup
force group = audiogroup
directory mask = 0770
create mask = 0770

[janne]
comment = Jannen yksityinen kansio
path = /media/flexraidpool/janne
browseable = yes
read only = no
public = no
guest ok = no
valid users = janne
create mask = 0700
directory mask = 0700

[omat_kuvat_jutut]
comment = yksityinen kuvakansio
path = /media/flexraidpool/omat_kuvat_jutut
browseable = yes
read only = no
public = no
guest ok = no
valid users = janne
create mask = 0700
directory mask = 0700


```

```
weirdinin@ubuntu:/media/flexraidpool/shared/video$ df
df: ”/root/FlexRAID-Managed-Pool/class1_0/{6289e715-c89a-4c6d-836f-bfc411208952}”: Lupa evätty
df: ”/root/FlexRAID-Managed-Pool/class1_0/{df9f5420-39ca-4e41-bf8d-21623cb8a4d8}”: Lupa evätty
df: ”/root/FlexRAID-Managed-Pool/class1_0/{9049ede4-c2e5-45cc-9f9e-a7956e8044ce}”: Lupa evätty
df: ”/root/FlexRAID-Managed-Pool/class1_0/{9d205cff-09c4-47d0-8c0a-3d6fb0913b03}”: Lupa evätty
df: ”/root/FlexRAID-Managed-Pool/class1_0/{55036583-348f-45e4-8fcb-c6ad2f71105d}”: Lupa evätty
Tiedostojärjestelmä  1K-blocks       Käyt   Vapaana Käy% Liitospiste
/dev/sda1            115136056   15911856  93375576  15% /
none                         4          0         4   0% /sys/fs/cgroup
udev                   3918544         12   3918532   1% /dev
tmpfs                   785552       1204    784348   1% /run
none                      5120          0      5120   0% /run/lock
none                   3927748          4   3927744   1% /run/shm
none                    102400          0    102400   0% /run/user
FlexRAIDFS          9133571416 8141231528 928850740  90% /media/flexraidpool


```

FlexRaid has overtook the ownership of the "/media/flexraidpool" path and flexraid also has full control over the discs so I think file systems are same:

```
weirdinin@ubuntu:/media/flexraidpool/shared/video$ sudo blkid -o list
device                                                   fs_type         label            mount point                                                  UUID
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                                     ext4                               /                                                                 3c24eb8e-6091-4541-80dd-05010e8b5dbe
/dev/sda5                                                     swap                               <swap>                                                            544dd082-d6c5-42c4-a996-458db928ca3a
/dev/sdb1                                                     ext4                               /root/FlexRAID-Managed-Pool/class1_0/{6289e715-c89a-4c6d-836f-bfc411208952} 6289e715-c89a-4c6d-836f-bfc411208952
/dev/sdc1                                                     ext4                               /root/FlexRAID-Managed-Pool/class1_0/{9d205cff-09c4-47d0-8c0a-3d6fb0913b03} 9d205cff-09c4-47d0-8c0a-3d6fb0913b03
/dev/sdd1                                                     ext4                               /root/FlexRAID-Managed-Pool/class1_0/{df9f5420-39ca-4e41-bf8d-21623cb8a4d8} df9f5420-39ca-4e41-bf8d-21623cb8a4d8
/dev/sde1                                                     ext4                               /root/FlexRAID-Managed-Pool/class1_0/{9049ede4-c2e5-45cc-9f9e-a7956e8044ce} 9049ede4-c2e5-45cc-9f9e-a7956e8044ce
/dev/sdf1                                                     ext4                               /root/FlexRAID-Managed-Pool/class1_0/{55036583-348f-45e4-8fcb-c6ad2f71105d} 55036583-348f-45e4-8fcb-c6ad2f71105d


```




Checked that users are members of video and publicgroup. Do you have any further ideas? I guess flexraid is the reason. Could it be, that flexraid has some kind of umask that overrides system's default umask? If so, I should go to flexraid forum and seek additional help from there.

---

