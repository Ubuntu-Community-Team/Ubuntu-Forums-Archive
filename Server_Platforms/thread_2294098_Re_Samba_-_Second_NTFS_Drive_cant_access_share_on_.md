---
title: "Re: Samba - Second NTFS Drive cant access share on windows."
date: 2015-09-09
forum: Server Platforms
---

### Post by mike359 on 2015-09-09
I have a "server" running lubuntu under my stairs.The aim is to have all the family files central.The children also stream movies and music from it.I have two young children and didn't want them having access to all the files, just their own folders.This storage is on a 2TB NTFS HDD that is NOT the drive lubuntu is installed on.I setup samba with users and shares.All the shares do show in windows and i get the user prompt also.However i always get access denied on windows.I thought this may be a windows authentication issue and have spent ages troubleshooting. Last night as a last ditch attempt I shared the "downloads" folder on the drive that IS part of the lubuntu install on the lubuntu drive and tried connecting on windows... it worked.I have come to the conclusion that either lubuntu or samba does not like the fact it is not the root drive for the other shares or that the 2TB drive is NTFS.Has anyone else had this issue or have any advice on solving it?

I also had this problem with Ubuntu.
Ubuntu was slow because of unity on my low end system. It was because of this and the sharing issue that I went with Lubuntu.

---

### Post by mike359 on 2015-09-10
No ideas? :-?

---

### Post by bab1 on 2015-09-12
> **mike359 said:**
> I have a "server" running lubuntu under my stairs.The aim is to have all the family files central.The children also stream movies and music from it.I have two young children and didn't want them having access to all the files, just their own folders.This storage is on a 2TB NTFS HDD that is NOT the drive lubuntu is installed on.I setup samba with users and shares.All the shares do show in windows and i get the user prompt also.However i always get access denied on windows.I thought this may be a windows authentication issue and have spent ages troubleshooting. Last night as a last ditch attempt I shared the "downloads" folder on the drive that IS part of the lubuntu install on the lubuntu drive and tried connecting on windows... it worked.I have come to the conclusion that either lubuntu or samba does not like the fact it is not the root drive for the other shares or that the 2TB drive is NTFS.Has anyone else had this issue or have any advice on solving it?
The problem is not that the shared folders are on a separate disk per se.  It sounds like a ownership and permissions problem.  Did you configure the 2TB NTFS HDD partition to mount via fstab?  NTFS file systems require setting the file and directory ownership and permissions at mount time.  [COLOR="#0000FF"]Edit:  You can't change these permissions once they are set.[/COLOR]

The reason you had success with the Downloads folder is because it is using the native ext4 file system.  The permissions are correctly configured when you installed the Ubuntu.

If you are going to use the 2TB NTFS HDD partition as is, you will need to configure the permissions and mounting via fstab.  If you are going to go to that trouble you might as well just format the partition with the ext4 as well.  You will have more control over the ownership and permissions.

Which method do you want to use?

---

### Post by mike359 on 2015-09-12
The problem i have is that there is already A LOT of data already on the drive and I don't have another drive to transfer the files to while I do the format.
I originally had it setup with windows but windows sharing is pretty much all or nothing. No user password protected directories.

I take it from your comment "[COLOR=#000000]If you are going to go to that trouble you might as well just format the partition with the ext4[/COLOR]" That setting up permissions and ownership using fstab is not a simple task for a linux n00b?

---

### Post by bab1 on 2015-09-12
> **mike359 said:**
> The problem i have is that there is already A LOT of data already on the drive and I don't have another drive to transfer the files to while I do the format.

Not having backups of your data means that someday you will have a failure that you can't easily recover from.  You need some method of backup. 
> 
I originally had it setup with windows but windows sharing is pretty much all or nothing. No user password protected directories.

I take it from your comment "[COLOR=#000000]If you are going to go to that trouble you might as well just format the partition with the ext4[/COLOR]" That setting up permissions and ownership using fstab is not a simple task for a linux n00b?  None of this is trivial.  It can be done either way.  One way is simple and solid.  The other way is harder to think out and IMO not as stable.  There will no way to modify the ownership or permissions of the files once they are created.  The problem is a matter of flexibility and security.  

Samba is higher level application and you can set ownership and permission when creating files using share parameters.  You will need a separate share for each user or group of users you want to manage.

From my point of view it is easier to create the users and groups, then set up the directories security and permissions using ext formatted partitions.  Then l make remotely available the directories with Samba shares.  If we use Samba it to handle all the authorization (you can do that) along with the athentication (who are you) it is not as flexible or secure.  Everything is managed at the share level.

How many users and what separation do we need for these users.  Do we have something like this for users: mom, dad, kid1, kid2 ?  How about the user-groups such as this: parents, kids, work, home?

IMO it is well worth the money spent on a backup storage solution.  Then you can start over with a freshly formatted 2TB data disk.  The amount of data is not going to get any smaller than it is now.

---

### Post by mike359 on 2015-09-22
OK, so today i got hold of an empty 500GB HDD, Installed it, formatted it with ext4.

again, shared root drive "downloads" folder and a folder i created on secondary drive (the 500GB one) called "Storage"

Moving to windows, the samba share worked with "downloads" once again and did NOT work with "Storage".

So i have ruled out the issue being NTFS since i formatted it with ext4.

Where do I go from here???

---

### Post by bab1 on 2015-09-22
> **mike359 said:**
> OK, so today i got hold of an empty 500GB HDD, Installed it, formatted it with ext4.

again, shared root drive "downloads" folder and a folder i created on secondary drive (the 500GB one) called "Storage"

Moving to windows, the samba share worked with "downloads" once again and did NOT work with "Storage".

So i have ruled out the issue being NTFS since i formatted it with ext4.

Where do I go from here???
The issue is one of permissions not NTFS per se.  It's just easier to set the permissions and control users using ext4.

It would be helpful for you so show where and how you installed the 500GB HDD.  [LIST]
[*]Should I assume that this disk is installed internally in the host machine?  
[*]How is it connected?  
[*] Where in the file system is it mounted?  
[/LIST]
Post the output for this terminal command```
df -h
```

I'd like to see the share configuration. Post the output of this terminal command```
cat /etc/samba/smb.conf
```

Please post the text output between [noparse]```
  
```[/noparse] code blocks.  The easiest way to do this is to click on the [SIZE=5]**# **[/SIZE]icon at the top of the Advanced Editor that you use to reply to this post.

---

### Post by mike359 on 2015-09-30
Thanks for your reply. 
I had already begun a reinstall of lubuntu before I read this. Anyway, I reinstalled Lubuntu and reformatted the new 500GB drive again only this time I chose to zero the drive as ext4 instead of quick formatting... thought it was worth a shot.

Anyway, it worked... at least partially.

I tested it on my wife's office PC (Win 7) and i got straight in to the 500GB drive shares.
I excitedly went down to my Win10 laptop and it failed. I believed I had found the cause, not samba, windows 10!!

I have since messed with windows 10 settings and got it working BUT only the root username and pass work.

I have a root user called woodieserver (this is the root lubuntu user and added to samba)
I have added other users called "parents" and "kids", Also added to samba shares.

These do not work on either win7 or win10. I can only connect using woodieserver.
Another issue possibly related is that I have shared a folder on the drive called "kids" with permissions of read/write for everyone. This is not accessible unless I access a user/password protected share (e.g. "Parents") first. 

Drive structure is as follows:)
//drive (share users: "Woodieserver", "Parents")
//drive/parents/ (share users: "Woodieserver", "Parents")
//drive/kids/ (share users: "Everyone")

Is the problem with the "Kids" folder caused by the root only having samba permission for "Woodieserver" and "Parents" and thus overides the permission of "everyone" for that folder.

Damn this gets complicated.

---

### Post by bab1 on 2015-10-01
> **mike359]Where do I go from here??? [/QUOTE]
I'm surprised.  You asked for help (see above) and I responded with some helpful advice and instructions.  I don't see any meaningful reply.  

Do you want help or just some sympathetic conversation?  If you want help, post the output to the commands I asked for in the previous posts.

[QUOTE=mike359 said:**
> Thanks for your reply. 
I had already begun a reinstall of lubuntu before I read this. Anyway, I reinstalled Lubuntu and reformatted the new 500GB drive again only this time I chose to zero the drive as ext4 instead of quick formatting... thought it was worth a shot.

Anyway, it worked... at least partially.

I tested it on my wife's office PC (Win 7) and i got straight in to the 500GB drive shares.
I excitedly went down to my Win10 laptop and it failed. I believed I had found the cause, not samba, windows 10!!

I have since messed with windows 10 settings and got it working BUT only the root username and pass work.
I have a root user called woodieserver (this is the root lubuntu user and added to samba)

There is only one root user (root: uid=0).  Do you mean you have a user named *woodieserver* the can use sudo commands and administrate?  Is this the user that was first created when you installed Ubuntu?
> 
I have added other users called "parents" and "kids", Also added to samba shares.
Just my personal belief, but I think users should use their names as usernames (i.e. john, will, robbie, liz, maggie or joan).  I name the usergroups by the use (i.e. parents, kids, accounting, admin).  This simplifies the administration and allows you to audit the users actions. > 
These do not work on either win7 or win10. I can only connect using woodieserver.
Another issue possibly related is that I have shared a folder on the drive called "kids" with permissions of read/write for everyone. This is not accessible unless I access a user/password protected share (e.g. "Parents") first. 

There is no way to tell what you have configured with you posting the specific configuration parameters.  Post the configuration output that I ask for and we can move forward. 
> 

Drive structure is as follows:)
//drive (share users: "Woodieserver", "Parents")
//drive/parents/ (share users: "Woodieserver", "Parents")
//drive/kids/ (share users: "Everyone")

This doesn't really tell us anything.
> 
Is the problem with the "Kids" folder caused by the root only having samba permission for "Woodieserver" and "Parents" and thus overides the permission of "everyone" for that folder.[?]

Who knows at this point?  We need to diagnose the problem in a logical manner.
> 
Damn this gets complicated.
Actually the Samba part is really simple.  There are lots of options, but the idea is not complex at all.

A larger part of the "problem" is the file system infrastructure.  This is where you are at right now.

The steps to configuring group sharing are:
[LIST]
[*]Configuring the file system structure, ownership and permissions
[*]Creating the users and groups that will use the file share
[*]Sharing the portion of the file system as a SMB resource (e.g the "share")
[*]
[/LIST]
The first step is the file system.  So let's start there.  Post the output of these commands```
df -h
ls -l <path/to/shared/directory>
```...where <path/to/shared/directory> is the actual path to the directory you are sharing.

Post the output of these commands so I can see the file shares you have made```
net usershare info --long

cat /etc/samba/smb.conf
```

---

### Post by mike359 on 2015-10-01
Thanks

```
root@woodieserver:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            486M     0  486M   0% /dev
tmpfs           100M  5.7M   94M   6% /run
/dev/sda1       293G  5.6G  272G   2% /
tmpfs           496M     0  496M   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           496M     0  496M   0% /sys/fs/cgroup
tmpfs           100M  8.0K  100M   1% /run/user/1000
/dev/sdb1       1.9T  490G  1.4T  27% /media/woodieserver/902E216C2E214D12

```
```
ls -l /media/woodieserver/902E216C2E214D12/WoodieServer-Storage
total 4
drwxrwxrwx 1 woodieserver woodieserver    0 Sep  2 20:17 Kids
drwxrwxrwx 1 woodieserver woodieserver 4096 Sep 27 21:37 Parents

```

```
root@woodieserver:~# net usershare info --long
root@woodieserver:~# 
root@woodieserver:~# 
root@woodieserver:~# 
root@woodieserver:~# cat /etc/samba/smb.conf
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


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
	server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam


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


#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
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


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
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
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
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
;	guest ok = no
;	read only = yes
	create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers


[Kids]
	path = /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Kids
	writeable = yes
;	browseable = yes
	guest ok = yes


[Parents]
	path = /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Parents
	writeable = yes
;	browseable = yes
	valid users = parents, woodieserver
root@woodieserver:~# 



```



Hope this helps.

---

### Post by bab1 on 2015-10-02
> **mike359 said:**
> Thanks

```
root@woodieserver:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
...
/dev/sdb1       1.9T  490G  1.4T  27% /media/woodieserver/902E216C2E214D12

```

Is the partition above allowed to auto mount via udisks?  Or maybe you have a line in the /etc/fstab file for that?  Post the output of ```
cat /etc/fstab
```
> 

```
ls -l /media/woodieserver/902E216C2E214D12/WoodieServer-Storage
total 4
drwxrwxrwx 1 woodieserver woodieserver    0 Sep  2 20:17 Kids
drwxrwxrwx 1 woodieserver woodieserver 4096 Sep 27 21:37 Parents

```
Both of these directories are available for read and write for all users as far as the OS is concerned.  Bear in mind this is not really the correct way of achieving those permissions.> 
```
root@woodieserver:~# net usershare info --long
root@woodieserver:~# 
root@woodieserver:~# 
root@woodieserver:~# 

```

Good.  No usershares created via the GUI.
> 
```

root@woodieserver:~# cat /etc/samba/smb.conf
...

#======================= Share Definitions =======================
...

[Kids]
	path = /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Kids
	writeable = yes
;	browseable = yes
	guest ok = yes

```

Since you are sharing ***Kids*** (/media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Kids) we need to see the permissions of contents of that folder.  Post the output of this
```
ls -l /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Kids
```
> 

```


[Parents]
	path = /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Parents
	writeable = yes
;	browseable = yes
	valid users = parents, woodieserver

```

You also need all of the users added to the Samba user database (smbpasswd -a).  Post the output of this to show what users are also Samba users```
sudo pdbedit -L
```...it is helpful if you have all users with a consistent username on all of the computers.  I am always bab (uid=1000) on all of my Linux and Windows computers.  That way I do not need to map one name to another. 

We should also see the permissions of contents of this folder too.  Post the output of
```

ls -l /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Parents

```
I notice that you are logged in as the root user (e.g. root@woodieserver:~#).  This is not a good idea.  If you need to have the root user perform commands you are better off using sudo each time.  If nothing else, it reminds you that root is performing the task.

I would like you to consider using user-groups (e.g. parents and kids) rather than users for share authorization.  As an example.  I would have setup the parents and kids directories like this
```
ls -l /media/woodieserver/902E216C2E214D12/WoodieServer-Storage
total 4
drwx[COLOR="#0000FF"]**rwx**[/COLOR][COLOR="#008000"]r-x[/COLOR] 1 woodieserver [COLOR="#0000FF"]**kids**[/COLOR]    0 Sep  2 20:17 Kids
drwx[COLOR="#0000FF"]**rwx**[/COLOR][COLOR="#008000"]r-x[/COLOR] 1 woodieserver [COLOR="#0000FF"]**parents**[/COLOR] 4096 Sep 27 21:37 Parents

```
The part in blue is the user-group and the groups permissions.  The part in green is the "others" group which every user that is not the owner or in the user-group.  This allows you to have a directory that is owned by a user-group while the owner (creator) of the content is not important.  The share might look like this for the kids```

[Kids]
        comment = Kids Files
        path = /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Kids
        browseable = yes
        guest ok = no
        valid users = @kids
        force group = kids
        writeable = yes

```
You can be part of the user-group kids along with your kids user accounts so you have access remotely.

The parents share might be this```

[Kids]
        comment = Kids Files
        path = /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Parents
        browseable = yes
        guest ok = no
        valid users = @parents
        force group = parents
        writeable = yes

```
Only the users that are in the parents user-group will be authentication (who are you) and have authorization (you have permission to do that).

From my own experience I have found this is the most flexible method.  You only need to maintain the user-groups and not the individual users.

But...You are the admin of your network so you get to make the final decisions.

---

### Post by mike359 on 2015-10-02
fstab
```

woodieserver@woodieserver:~$ cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3249bddd-90da-4382-bff0-9d16cebbdd60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=36f8fefb-f838-4622-b9d9-7fc211070171 none            swap    sw              0       0
woodieserver@woodieserver:~$ 

```


```

woodieserver@woodieserver:~$ ls -l /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Kids
total 28
drwxrwxrwx 1 woodieserver woodieserver  4096 Oct  2 09:24 Isabella Storage
drwxrwxrwx 1 woodieserver woodieserver 24576 Sep 25 22:45 Movies
drwxrwxrwx 1 woodieserver woodieserver     0 Jun 17 21:12 Noah Storage
woodieserver@woodieserver:~$ 

```

```

woodieserver@woodieserver:~$ sudo pdbedit -L
woodieserver:1000:WoodieServer
parents:1002:parents,,,,
woodieserver@woodieserver:~$ 

```

```

woodieserver@woodieserver:~$ ls -l /media/woodieserver/902E216C2E214D12/WoodieServer-Storage/Parents
total 44
drwxrwxrwx 1 woodieserver woodieserver 12288 Sep 27 21:23 Amy Storage
drwxrwxrwx 1 woodieserver woodieserver  4096 Sep 26 00:17 Mike Storage
drwxrwxrwx 1 woodieserver woodieserver  4096 Sep 27 21:27 Movies
drwxrwxrwx 1 woodieserver woodieserver  4096 Sep 29 00:17 Music
drwxrwxrwx 1 woodieserver woodieserver  4096 Aug  8 14:02 Phone Backup
drwxrwxrwx 1 woodieserver woodieserver  4096 Sep 26 01:08 Pictures
drwxrwxrwx 1 woodieserver woodieserver  4096 Sep 28 19:43 Software & Installation Files
drwxrwxrwx 1 woodieserver woodieserver  8192 Sep  2 20:19 Temp Storage
woodieserver@woodieserver:~$ 

```


I agree with all of your advice. I'm just quite new to Linux and have limited skills in the Terminal. I'm flighting my way though it as i would like to learn it.

As per your advice, I have created to user groups. I hope I have done it correctly.
[TABLE="width: 500"]
[TR]
[TD]**Parents (group)**[/TD]
[TD]**Kids (group)**[/TD]
[/TR]
[TR]
[TD]Mum[/TD]
[TD]Mum[/TD]
[/TR]
[TR]
[TD]Dad[/TD]
[TD]dad[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]Izzi[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]Noah[/TD]
[/TR]
[/TABLE]

So i have two groups, but mum and dad are also added to "Kids" (as we should obviously have access to the children's files and folders.)

---

### Post by darkod on 2015-10-02
Lets be short and more specific, step by step. In your post #11 /dev/sdb1 is the 2TB disk, not the 500GB you mention you formatted with ext4. So, is that again the ntfs 2TB disk?

I am asking because the instrcutions to automount it will differ if it's ntfs. In fact, I wouldn't use it as ntfs at all, as already recommended.

Lets assume /dev/sdb1 is the single partition on the second disk, formatted as ext4. You can create any empty folder that you like and use it as mount point. That's how it works in linux. So you can call it /data, or /storage, or even /storage1 if think in the future you will install another disk and call it /storage2.

So, just make the folder /storage for example, and in the /etc/fstab add this line to automount sdb1:
```
/dev/sdb1   /storage   ext4   defaults   0   0
```

That will mount it at each boot. After that you use the /storage path as you need and also this path is much shorter and easier to use and manage compared to the whole path you use now for the disk. You will use it for example in the smb.conf to create the share definition.

The permissions of the folders/files in /storage are separate thing, and as already discussed.

So I guess the next immediate questions is: Are you continuing with ntfs disk or with ext4 disk? It would make a difference.

---

### Post by bab1 on 2015-10-02
> **mike359 said:**
> As per your advice, I have created to user groups. I hope I have done it correctly.

I can't see the commands you used so I can't say that you have or have not done it correctly.  Interesting choice of logins for your wife and yourself.  I am a father, but my login is always my name.  ;-)

The partition sdb1 is not mounted via fstab.  The partition should be mounted via fstab and should be an ext4 partition if not used in a dual boot situation.  Do you still have your data backed up onto the 500GB drive?  If so you can follow @darkod's instructions and permanently mount the partition sdb1.  If you are going to use the entire HDD as a data storage location.  I would only create one partition on the HDD as sdb1 (the entire 2TB).  The standard mount point for server data (i.e. Samba server data) is /srv.  I would go farther and say that you should create a mount point at /srv such as /srv/share to mount the sdb1 2TB partition.

See the [**Linux File System Hierarchy Standard**]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for reference.

---

### Post by bab1 on 2015-10-02
> **darkod said:**
> Lets be short and more specific, step by step. In your post #11 /dev/sdb1 is the 2TB disk, not the 500GB you mention you formatted with ext4. So, is that again the ntfs 2TB disk?

Read the thread again.  The OP was referring to a 500GB backup disk.
> 

I am asking because the instrcutions to automount it will differ if it's ntfs. In fact, I wouldn't use it as ntfs at all, as already recommended.

Lets assume /dev/sdb1 is the single partition on the second disk, formatted as ext4. You can create any empty folder that you like and use it as mount point. That's how it works in linux. So you can call it /data, or /storage, or even /storage1 if think in the future you will install another disk and call it /storage2.

So, just make the folder /storage for example, and in the /etc/fstab add this line to automount sdb1:
```
/dev/sdb1   /storage   ext4   defaults   0   0
```

That will mount it at each boot. After that you use the /storage path as you need and also this path is much shorter and easier to use and manage compared to the whole path you use now for the disk. You will use it for example in the smb.conf to create the share definition.

The permissions of the folders/files in /storage are separate thing, and as already discussed.

So I guess the next immediate questions is: Are you continuing with ntfs disk or with ext4 disk? It would make a difference.
I suggest that the OP doesn't know which file system formatting to use.  I'm sure you will ageee that ext4 is a better choice in this situation.

---

### Post by darkod on 2015-10-03
Yes, I agree ext4 is better choice definitely. As I said in my post too, I wouldn't use ntfs at all in this situation.

But I didn't manage to understand if all data from the 2TB disk could fit onto the 500GB. If it doesn't, you can't really reformat the 2TB one as all of us have pointed out. Only that he tried a 500GB disk with ext4 and got same behavior. But that doesn't mean all the data fits...

---

### Post by bab1 on 2015-10-03
> **darkod said:**
> ...
But I didn't manage to understand if all data from the 2TB disk could fit onto the 500GB.
That's why I said "read the entire thread".  The OP provided the information.  See Below```
root@woodieserver:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
...
/dev/sdb1       1.9T  [COLOR="#FF0000"]**490G**[/COLOR]  1.4T  27% /media/woodieserver/902E216C2E214D12
```

See the part in red.  That is the data that should also be on the OP's 500GB backup disk.

To @mike359 -- Is this correct?  You have all the data from the 2TB drive backed up to a separate 500GB HDD?

---

### Post by mike359 on 2015-10-03
Correct, I do have all files backed up on the new ext4 500GB drive.
So my plan of action (i think) from all your advice is... 

* Format the 2TB to ext4 now that its backed up.
* fstab the 2TB drive so it auto mounts.
* Setup user group share permissions and folder permissions instead of per user.

There will be plenty of googling ahead haha.

I will try to achieve what you have kindly advised.
Keep you updated.
Thanks.

---

### Post by mike359 on 2015-10-03
> **bab1 said:**
> The standard mount point for server data (i.e. Samba server data) is /srv.  I would go farther and say that you should create a mount point at /srv such as /srv/share to mount the sdb1 2TB partition.

See the [**Linux File System Hierarchy Standard**]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for reference.

This is interesting, will have to look at this properly when I chance, thanks.

---

### Post by bab1 on 2015-10-03
> **mike359 said:**
> Correct, I do have all files backed up on the new ext4 500GB drive.
So my plan of action (i think) from all your advice is... 

* Format the 2TB to ext4 now that its backed up.
* fstab the 2TB drive so it auto mounts.
* Setup user group share permissions and folder permissions instead of per user.

There will be plenty of googling ahead haha.

I will try to achieve what you have kindly advised.
Keep you updated.
Thanks.
If you have problems or can't find what you need by googling, just ask here.  We can supply the commands you need to accomplish your goal,

---

### Post by mike359 on 2015-10-04
Ok, So i think i have done everything correctly.
Could you please review these outputs.

```

woodieserver@woodieserver:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            486M     0  486M   0% /dev
tmpfs           100M  5.6M   94M   6% /run
/dev/sda1       293G  5.7G  272G   3% /
tmpfs           496M     0  496M   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           496M     0  496M   0% /sys/fs/cgroup
**[COLOR=#ff0000]/dev/sdb1       1.8T  144G  1.6T   9% /srv/2TBstorage (this is the newly formatted ext4 drive auto mounting in fstab)[/COLOR]**
tmpfs           100M  8.0K  100M   1% /run/user/1000
/dev/sdc1       459G  252G  184G  58% /media/woodieserver/Storage
woodieserver@woodieserver:~$ 

```

```

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/
total 8
drwxrwxr-x 5 woodieserver kids    4096 Oct  4 12:15 Kids
drwxrwxr-x 9 woodieserver parents 4096 Oct  4 12:31 Parents
woodieserver@woodieserver:~$ 

```

```
# Windows clients look for this share name as a source of downloadable# printer drivers


[Kids]
        comment = Kids Files
        path = /srv/2TBstorage/WoodieServer-Storage/Kids
        browseable = yes
        guest ok = no
        valid users = @kids
        force group = kids
        writeable = yes


[Parents]
	comment = Kids Files
        path = /srv/2TBstorage/WoodieServer-Storage/Parents
        browseable = yes
        guest ok = no
        valid users = @parents
        force group = parents
        writeable = yes


[Downloads]
	path = /home/woodieserver/Downloads
	writeable = yes
;	browseable = yes
	guest ok = yes
woodieserver@woodieserver:~$ 

```

I have created two groups, Parent & Kids.
Parents (Mike, Amy)
Kids (Mike, Amy, Izzi, Noah)

I have to be missing something as the only user that works is "woodiesever" which is the user that was created during install of lubuntu.
I'm finding my way around terminal much better I think HAHA!!
Thanks guys.

---

### Post by darkod on 2015-10-04
Go inside Parents and do the ls -l in there to check permissions of the subfolders. Don't forget that Parents can have one permissions but the subfolders different ones.

Also, login to the server as Mike and try to go into any of your parents subfolders and create any file there. That will show you if the local user is working or not. That way you can see if you are forbidden write only over network/samba or as local user too.

I think it was mentioned earlier, did you confirm all local users are also samba users? Samba keeps different users.

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> Ok, So i think i have done everything correctly.
Could you please review these outputs.

```

woodieserver@woodieserver:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            486M     0  486M   0% /dev
tmpfs           100M  5.6M   94M   6% /run
/dev/sda1       293G  5.7G  272G   3% /
tmpfs           496M     0  496M   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           496M     0  496M   0% /sys/fs/cgroup
**[COLOR=#ff0000]/dev/sdb1       1.8T  144G  1.6T   9% /srv/2TBstorage (this is the newly formatted ext4 drive auto mounting in fstab)[/COLOR]**
tmpfs           100M  8.0K  100M   1% /run/user/1000
/dev/sdc1       459G  252G  184G  58% /media/woodieserver/Storage
woodieserver@woodieserver:~$ 

```

It is more important to see the actual /etc/fstab file.  Post the output of this```
cat /etc/fstab
```
> 
```

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/
total 8
drwxrwxr-x 5 woodieserver kids    4096 Oct  4 12:15 Kids
drwxrwxr-x 9 woodieserver parents 4096 Oct  4 12:31 Parents
woodieserver@woodieserver:~$ 

```

Make sure that the path to these folders has read and eXecute rights so that any user can read and traverse the /*srv* and */srv/2TBstorage* folders.  Post the output of these commands```
ls -l /srv

ls -l /srv/2TBstorage
```
> 
```
# Windows clients look for this share name as a source of downloadable# printer drivers

[Kids]
        comment = Kids Files
        path = /srv/2TBstorage/WoodieServer-Storage/Kids
        browseable = yes
        guest ok = no
        valid users = @kids
        force group = kids
        writeable = yes


[Parents]
	comment = Kids Files
        path = /srv/2TBstorage/WoodieServer-Storage/Parents
        browseable = yes
        guest ok = no
        valid users = @parents
        force group = parents
        writeable = yes


[Downloads]
	path = /home/woodieserver/Downloads
	writeable = yes
;	browseable = yes
	guest ok = yes
woodieserver@woodieserver:~$ 

```

I have created two groups, Parent & Kids.
Parents (Mike, Amy)
Kids (Mike, Amy, Izzi, Noah)

The above looks okay.  Lets see if the users are really there.  Post the output of these commands```

getent passwd | grep 100|grep -v 101

getent group parents kids
```
We also need to check for the corresponding Samba users existence.  Post he output of this command```
sudo pdbedit -L
``` 
> 
I have to be missing something as the only user that works is "woodiesever" which is the user that was created during install of lubuntu.
I'm finding my way around terminal much better I think HAHA!!
Thanks guys.
It's better to see what you have really got first.  I think you are real close now.  The one thing I have left for last is user-group inheritance.  We will do that last.

For right now you can log in as any of the users to see if that user can create a file in /srv/2TBstorage/WoodieServer-Storage/Kids```

touch /srv/2TBstorage/WoodieServer-Storage/Kids/<some-file-name>
```...where <some-file-name> is your choice and is unique to that user.

---

### Post by bab1 on 2015-10-05
> **darkod said:**
> Go inside Parents and do the ls -l in there to check permissions of the subfolders. Don't forget that Parents can have one permissions but the subfolders different ones.
The permissions are really not the problem upon file creation.  Permissions are handled by umask.  If there is a problem it will be with ownership (e.g. owner:group) changing.
> 
Also, login to the server as Mike and try to go into any of your parents subfolders and create any file there. That will show you if the local user is working or not. That way you can see if you are forbidden write only over network/samba or as local user too.

When we are done here the ownership will be provided by **user-group** inheritance.  The OP only needs to check access to the root folder of the share (i.e. *_/srv/2TBstorage/WoodieServer-Storage/Kids_* or *_/srv/2TBstorage/WoodieServer-Storage/Parents_* using the command **touch.**

---

### Post by mike359 on 2015-10-05
```

woodieserver@woodieserver:~$ cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3249bddd-90da-4382-bff0-9d16cebbdd60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=36f8fefb-f838-4622-b9d9-7fc211070171 none            swap    sw              0       0
/dev/sdb1              /srv/2TBstorage              ext4              defaults              0              0

```

```
woodieserver@woodieserver:~$ ls -l /srvtotal 4
drwx------ 5 woodieserver woodieserver 4096 Oct  4 12:05 2TBstorage
```

```
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage
total 24
drwx------ 2 root         root         16384 Oct  4 11:55 lost+found
drwxrwxr-x 3 woodieserver woodieserver  4096 Oct  4 12:05 Company-files
drwxrwxr-x 4 woodieserver woodieserver  4096 Oct  4 12:15 WoodieServer-Storage

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage
total 8
drwxrwxr-x 5 woodieserver kids    4096 Oct  4 12:15 Kids
drwxrwxr-x 9 woodieserver parents 4096 Oct  4 12:31 Parents

```

```
woodieserver@woodieserver:~$ getent passwd | grep 100|grep -v 101systemd-timesync:x:100:104:systemd Time Synchronization,,,:/run/systemd:/bin/false
woodieserver:x:1000:1000:WoodieServer,,,:/home/woodieserver:/bin/bash
izzi:x:1001:1002:Izzi,,,,:/home/izzi:/bin/bash
noah:x:1002:1005:noah,,,,:/home/noah:/bin/bash
amy:x:1003:1006:amy,,,,:/home/amy:/bin/bash
mike:x:1004:1007:mike,,,,:/home/mike:/bin/bash
```

```
woodieserver@woodieserver:~$ getent group parents kids
parents:x:1004:woodieserver,mike,amy
kids:x:1001:woodieserver,amy,noah,mike,izzi

```

```
woodieserver@woodieserver:~$ sudo pdbedit -L
[sudo] password for woodieserver: 
WARNING: Ignoring invalid value 'share' for parameter 'security'
woodieserver:1000:WoodieServer
amy:1003:amy,,,,
noah:1002:noah,,,,
mike:1004:mike,,,,
izzi:1001:Izzi,,,,

```
Hmmmm, A warning?! :)

You may be onto the problem with the touch command, I su'd into that user rather than logging in via the GUI, is that ok?
```

woodieserver@woodieserver:~$ su - mike
Password: 
mike@woodieserver:~$ touch /srv/2TBstorage/WoodieServer-Storage/Kids/delete-me-later.txt
touch: cannot touch ‘/srv/2TBstorage/WoodieServer-Storage/Kids/delete-me-later.txt’: Permission denied
mike@woodieserver:~$ 

```

Cheers gentlemen.

fixed the [COLOR=#000000][FONT=Ubuntu Mono]sudo pdbedit -L[/FONT][/COLOR] 
I was messing a little last night and set security to "shares" rather than "users" :)

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> ```

woodieserver@woodieserver:~$ cat /etc/fstab# /etc/fstab: static file system information.
#
[COLOR="#0000FF"][B]# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#[/B][/COLOR]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3249bddd-90da-4382-bff0-9d16cebbdd60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=36f8fefb-f838-4622-b9d9-7fc211070171 none            swap    sw              0       0
[COLOR="#FF0000"]**/dev/sdb1              /srv/2TBstorage              ext4              defaults              0              0**[/COLOR]

```

The line in red above should use the UUID instead of /dev/sdb1.  See the note in blue.

[COLOR="#008000"][SIZE=3]**Edit:  **[/SIZE][/COLOR]The format should be something like this: *UUID=<some-looooooong-number>      /srv/2TBstorage              ext4              defaults              0              0*

To see what the blkid is use this command```
sudo blkid -c /dev/null -o list
```
You will see that every partition has a UUID.  the sda or sdb or sdc is not always assigned to the same partition, but the UUID always ID's the partition in question. 
> 

```
woodieserver@woodieserver:~$ ls -l /srv
total 4
drwx------ 5 woodieserver woodieserver 4096 Oct  4 12:05 2TBstorage
```

Wrong!  Only the user woodieserver can descend into the folder 2TBstorage.  This needs to be set to 0775 ( it is now at 0700).  You can do that with this command```
sudo chmod 0775 /srv/2TBStoreage
```
> 
```
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage
total 24
drwx------ 2 root         root         16384 Oct  4 11:55 lost+found
drwxrwxr-x 3 woodieserver woodieserver  4096 Oct  4 12:05 Company-files
drwxrwxr-x 4 woodieserver woodieserver  4096 Oct  4 12:15 WoodieServer-Storage

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage
total 8
drwxrwxr-x 5 woodieserver kids    4096 Oct  4 12:15 Kids
drwxrwxr-x 9 woodieserver parents 4096 Oct  4 12:31 Parents

```
With /srv fixed,  you should be able to use touch to create a file in Kids with any user (from the command line).  Any user in the parents group (you or your wife or woodieserver should be able to create a file in the Parents folder.

Try it and post the output back here. We you should be able to create the files, but there is still one step before we are finished with the file system.  Can you see the problem?  It has to do with group inheretance
> 
```
woodieserver@woodieserver:~$ getent passwd | grep 100|grep -v 101systemd-timesync:x:100:104:systemd Time Synchronization,,,:/run/systemd:/bin/false
woodieserver:x:1000:1000:WoodieServer,,,:/home/woodieserver:/bin/bash
izzi:x:1001:1002:Izzi,,,,:/home/izzi:/bin/bash
noah:x:1002:1005:noah,,,,:/home/noah:/bin/bash
amy:x:1003:1006:amy,,,,:/home/amy:/bin/bash
mike:x:1004:1007:mike,,,,:/home/mike:/bin/bash
```

```
woodieserver@woodieserver:~$ getent group parents kids
parents:x:1004:woodieserver,mike,amy
kids:x:1001:woodieserver,amy,noah,mike,izzi

```

```
woodieserver@woodieserver:~$ sudo pdbedit -L
[sudo] password for woodieserver: 
WARNING: Ignoring invalid value 'share' for parameter 'security'
woodieserver:1000:WoodieServer
amy:1003:amy,,,,
noah:1002:noah,,,,
mike:1004:mike,,,,
izzi:1001:Izzi,,,,

```
Hmmmm, A warning?! :)


You may be onto the problem with the touch command, I su'd into that user rather than logging in via the GUI, is that ok? 

Don't use the GUI just yet.> 
```

woodieserver@woodieserver:~$ su - mike
Password: 
mike@woodieserver:~$ touch /srv/2TBstorage/WoodieServer-Storage/Kids/delete-me-later.txt
touch: cannot touch &#8216;/srv/2TBstorage/WoodieServer-Storage/Kids/delete-me-later.txt&#8217;: Permission denied
mike@woodieserver:~$ 

```

Cheers gentlemen.
I see you fixed the problem of the pdbedit warning.  The other steps will take care of the touch issue.

---

### Post by mike359 on 2015-10-05
Changed to UUID, just waiting for the server to reboot.
Do i need to force user to woodieserver once authenticated so any new folders / files created have woodieserver as the owner and not the user that created them?

Google is my friend. haha!

[http://ubuntuforums.org/showthread.php?t=2192973&p=12870668#post12870668](http://ubuntuforums.org/showthread.php?t=2192973&p=12870668#post12870668) Thank you! :)

---

### Post by mike359 on 2015-10-05
The thing that is taxing my brain now is do i set sgid on the root directory or on each share...

example...
```

sudo chmod g+s /srv/2TBstorage/WoodieServer-Storage/parents

```

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> Changed to UUID, just waiting for the server to reboot.
Do i need to force user to woodieserver once authenticated so any new folders / files created have woodieserver as the owner and not the user that created them?

Google is my friend. haha!

[http://ubuntuforums.org/showthread.php?t=2192973&p=12870668#post12870668](http://ubuntuforums.org/showthread.php?t=2192973&p=12870668#post12870668) Thank you! :)

When you have set up the file system as I show you, The *user* (owner/creator) is no longer the important entity.  The **user-group** will be what controls access.  Would you like an example or does my previous thought explain enough?

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> The thing that is taxing my brain now is do i set sgid on the root directory or on each share...

example...
```

sudo chmod g+s /srv/2TBstorage/WoodieServer-Storage/parents

```Don't front run me here.  ;-)  Just follow along and it will all be revealed.  :D

[COLOR="#008000"]Edit:  You are trying to get to the end of the task.  I want you to see what happens so you can do this later without needing help.  [/COLOR]

---

### Post by bab1 on 2015-10-05
Did the touch command work?  Were you able to create files in the two directories (Kids and Parents) with both types of users (kids (group) and parents (group))?

Post the output of these comands```
ls -l  /srv/2TBstorage/WoodieServer-Storage/parents

ls -l /srv/2TBstorage/WoodieServer-Storage/kids
```

---

### Post by mike359 on 2015-10-05
Well I did jump ahead didn't I!
Using UUID broke it, so it booted into emergency mode. I removed the mount point for that device so I could let it boot.

```

woodieserver@woodieserver:~$ sudo blkid -c /dev/null -o list
[sudo] password for woodieserver: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              3249bddd-90da-4382-bff0-9d16cebbdd60
/dev/sda5  swap             <swap>         36f8fefb-f838-4622-b9d9-7fc211070171
/dev/sdb1  ext4    storage2TB (not mounted) e5a5ccd7-7d6f-482e-9b0d-28c275262c89
/dev/sdc1  ext4    Storage  (not mounted)  34848141-ae04-4de0-9543-dca642f10c5c

```

I added:
```

UUID=e5a5ccd7-7d6f-482e-9b0d-28c275262c89    /srv/2TBstorage    ext4    default   0   0

```

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> Well I did jump ahead didn't I!
Using UUID broke it, so it booted into emergency mode. I removed the mount point for that device so I could let it boot.

```

woodieserver@woodieserver:~$ sudo blkid -c /dev/null -o list
[sudo] password for woodieserver: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              3249bddd-90da-4382-bff0-9d16cebbdd60
/dev/sda5  swap             <swap>         36f8fefb-f838-4622-b9d9-7fc211070171
/dev/sdb1  ext4    storage2TB (not mounted) e5a5ccd7-7d6f-482e-9b0d-28c275262c89
/dev/sdc1  ext4    Storage  (not mounted)  34848141-ae04-4de0-9543-dca642f10c5c

```

I added:
```

UUID=e5a5ccd7-7d6f-482e-9b0d-28c275262c89    /srv/2TBstorage    ext4    [COLOR="#FF0000"]**default**[/COLOR]   0   0

```

It's defaults not default (see red).  From the man page re: mount```
 defaults
              Use default options: rw, suid, dev, exec, auto, nouser, and async.

```

---

### Post by mike359 on 2015-10-05
What a numpty! All sorted and mounting with UUID.
I was able to 'touch' a file in the Kids folder btw. :)

Enlighten me please bab1, How do I sgid?

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> What a numpty! All sorted and mounting with UUID.
I was able to 'touch' a file in the Kids folder btw. :)

Enlighten me please bab1, How do I sgid?
Maybe you missed this.  Please post the output of these comands

```
ls -l  /srv/2TBstorage/WoodieServer-Storage/parents

ls -l /srv/2TBstorage/WoodieServer-Storage/kids
```

---

### Post by mike359 on 2015-10-05
Apologies, I did!
```

woodieserver@woodieserver:~$ ls -l  /srv/2TBstorage/WoodieServer-Storage/Parents 
total 38688
drwxrwxr-x  5 woodieserver woodieserver     4096 Oct  4 12:19 Amy Storage
drwxrwxr-x  7 woodieserver woodieserver     4096 Oct  4 12:19 Mike Storage
drwxrwxr-x  6 woodieserver woodieserver     4096 Oct  4 12:16 Movies
drwxrwxr-x  3 woodieserver woodieserver     4096 Oct  4 12:31 Music
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:31 Phone Backup
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:18 Pictures
-rwxrwxrwx  1 woodieserver woodieserver 39585738 Mar  3  2015 pro valet sheet.psd
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:30 Software & Installation Files

```

```

woodieserver@woodieserver:~$ ls -l  /srv/2TBstorage/WoodieServer-Storage/Kids
total 12
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Isabella Storage
drwxrwxr-x 6 woodieserver woodieserver 4096 Oct  4 12:15 Movies
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Noah Storage

```

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> Apologies, I did!
```

woodieserver@woodieserver:~$ ls -l  /srv/2TBstorage/WoodieServer-Storage/Parents 
total 38688
drwxrwxr-x  5 woodieserver woodieserver     4096 Oct  4 12:19 Amy Storage
drwxrwxr-x  7 woodieserver woodieserver     4096 Oct  4 12:19 Mike Storage
drwxrwxr-x  6 woodieserver woodieserver     4096 Oct  4 12:16 Movies
drwxrwxr-x  3 woodieserver woodieserver     4096 Oct  4 12:31 Music
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:31 Phone Backup
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:18 Pictures
-rwxrwxrwx  1 woodieserver woodieserver 39585738 Mar  3  2015 pro valet sheet.psd
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:30 Software & Installation Files

```

```

woodieserver@woodieserver:~$ ls -l  /srv/2TBstorage/WoodieServer-Storage/Kids
total 12
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Isabella Storage
drwxrwxr-x 6 woodieserver woodieserver 4096 Oct  4 12:15 Movies
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Noah Storage

```

This shows that the user ***woodieserver*** copied or made some directories.  I assume there are files inside the directories too..  I want to see that a user such as  **noah** or **Izzi** can make files in Kids and can't make files in Parents.  The same with the users **mike** and **amy**.  They should be able to make files in both directroies.

Try using the touch command again as one of the above users ```
touch /srv/2TBstorage/WoodieServer-Storage/Kids/kid-file.txt 

sudo touch /srv/2TBstorage/WoodieServer-Storage/parents/parents-file.txt 
```..and sent that set of results```
ls -l  /srv/2TBstorage/WoodieServer-Storage/parents

ls -l /srv/2TBstorage/WoodieServer-Storage/kids
```

FYI:  Having existing data is a different problem we will deal with in a bit.  I need to see that the users function correctly first.

---

### Post by mike359 on 2015-10-05
```

woodieserver@woodieserver:~$ su - noah
Password: 
noah@woodieserver:~$ touch /srv/2TBstorage/WoodieServer-Storage/Kids/kid-file.txt 
noah@woodieserver:~$ sudo touch /srv/2TBstorage/WoodieServer-Storage/parents/parents-file.txt
[sudo] password for noah: 
noah is not in the sudoers file.  This incident will be reported.
noah@woodieserver:~$ 

```

I also successfully created a file in Kids and Parents as user 'mike'

```
woodieserver@woodieserver:~$ ls -l  /srv/2TBstorage/WoodieServer-Storage/Parentstotal 38688
drwxrwxr-x  5 woodieserver woodieserver     4096 Oct  4 12:19 Amy Storage
drwxrwxr-x  7 woodieserver woodieserver     4096 Oct  4 12:19 Mike Storage
drwxrwxr-x  6 woodieserver woodieserver     4096 Oct  4 12:16 Movies
drwxrwxr-x  3 woodieserver woodieserver     4096 Oct  4 12:31 Music
-rw-rw-r--  1 mike         mike                0 Oct  5 23:08 parent-file.txt
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:31 Phone Backup
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:18 Pictures
-rwxrwxrwx  1 woodieserver woodieserver 39585738 Mar  3  2015 pro valet sheet.psd
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:30 Software & Installation Files
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Kids
total 12
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Isabella Storage
-rw-rw-r-- 1 noah         noah            0 Oct  5 23:05 kid-file.txt
drwxrwxr-x 6 woodieserver woodieserver 4096 Oct  4 12:15 Movies
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Noah Storage
-rw-rw-r-- 1 mike         mike            0 Oct  5 23:08 parent-file.txt
woodieserver@woodieserver:~$ 

```

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> ```

woodieserver@woodieserver:~$ su - noah
Password: 
noah@woodieserver:~$ touch /srv/2TBstorage/WoodieServer-Storage/Kids/kid-file.txt 
noah@woodieserver:~$ sudo touch /srv/2TBstorage/WoodieServer-Storage/parents/parents-file.txt
[sudo] password for noah: 
noah is not in the sudoers file.  This incident will be reported.
noah@woodieserver:~$ 

```

I also successfully created a file in Kids and Parents as user 'mike'

```
woodieserver@woodieserver:~$ ls -l  /srv/2TBstorage/WoodieServer-Storage/Parents
total 38688
...
-rw-rw-r--  1 mike         mike                0 Oct  5 23:08 parent-file.txt

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Kids
total 12

-rw-rw-r-- 1 noah         noah            0 Oct  5 23:05 kid-file.txt
...
-rw-rw-r-- 1 mike         mike            0 Oct  5 23:08 parent-file.txt
woodieserver@woodieserver:~$ 

```
So each group of users now has permissions to create files and directories in their respective folders.  To set the **parents** group inheritance on the */srv/2TBstorage/WoodieServer-Storage/parents/* folder we need to do this```
sudo chmod g+s /srv/2TBstorage/WoodieServer-Storage/Parents 
``` 

To set the **kids** group inheritance on the */srv/2TBstorage/WoodieServer-Storage/kids/* folder we need to do this ```
sudo chmod g+s /srv/2TBstorage/WoodieServer-Storage/Kids
``` 

Post the output of these commands```
ls -l  /srv/2TBstorage/WoodieServer-Storage/parents

ls -l /srv/2TBstorage/WoodieServer-Storage/kids
```...you should see permissions like this```
drwxrw***[COLOR="#FF0000"]s[/COLOR]***r-x
```...note the red s.  This is the sgid bit.  It sets that group inheritance on all files and sub-directories under that directory.  Since each directory has a different group that directory is the root of each separate file system.

Try the touch commands again and see if they work for each group of users.

Post that info back (again :-(   ) ```
ls -l  /srv/2TBstorage/WoodieServer-Storage/parents

ls -l /srv/2TBstorage/WoodieServer-Storage/kids
```

---

### Post by mike359 on 2015-10-05
```

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Kids
total 12
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Isabella Storage
-rw-rw-r-- 1 noah         noah            0 Oct  5 23:05 kid-file.txt
drwxrwxr-x 6 woodieserver woodieserver 4096 Oct  4 12:15 Movies
-rw-rw-r-- 1 noah         kids            0 Oct  5 23:39 noah-delete-me-later.txt
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Noah Storage
-rw-rw-r-- 1 mike         mike            0 Oct  5 23:08 parent-file.txt
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents
total 38688
drwxrwxr-x  5 woodieserver woodieserver     4096 Oct  4 12:19 Amy Storage
-rw-rw-r--  1 mike         parents             0 Oct  5 23:38 delete-me-later.txt
drwxrwxr-x  7 woodieserver woodieserver     4096 Oct  4 12:19 Mike Storage
drwxrwxr-x  6 woodieserver woodieserver     4096 Oct  4 12:16 Movies
drwxrwxr-x  3 woodieserver woodieserver     4096 Oct  4 12:31 Music
-rw-rw-r--  1 mike         mike                0 Oct  5 23:08 parent-file.txt
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:31 Phone Backup
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:18 Pictures
-rwxrwxrwx  1 woodieserver woodieserver 39585738 Mar  3  2015 pro valet sheet.psd
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:30 Software & Installation Files
woodieserver@woodieserver:~$ 


```

Mike can create in both, Noah can only create in Kids.

---

### Post by bab1 on 2015-10-05
> Mike can create in both, Noah can only create in Kids. 

I can see that.  Have you set the sgid bits on each folder and tested like I asked?  Post that output please.

[COLOR="#0000FF"]**Edit: ** This is the minutia of Ubuntu so you have to really read what I'm posting.  You  can't skim over the post. [/COLOR]

---

### Post by mike359 on 2015-10-05
Yes i did, I have just ran it again though.

```

woodieserver@woodieserver:~$ sudo chmod g+s /srv/2TBstorage/WoodieServer-Storage/Parents
woodieserver@woodieserver:~$ sudo chmod g+s /srv/2TBstorage/WoodieServer-Storage/Kids
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents
total 38688
drwxrwxr-x  5 woodieserver woodieserver     4096 Oct  4 12:19 Amy Storage
-rw-rw-r--  1 mike         parents             0 Oct  5 23:38 delete-me-later.txt
drwxrwxr-x  7 woodieserver woodieserver     4096 Oct  4 12:19 Mike Storage
drwxrwxr-x  6 woodieserver woodieserver     4096 Oct  4 12:16 Movies
drwxrwxr-x  3 woodieserver woodieserver     4096 Oct  4 12:31 Music
-rw-rw-r--  1 mike         mike                0 Oct  5 23:08 parent-file.txt
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:31 Phone Backup
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:18 Pictures
-rwxrwxrwx  1 woodieserver woodieserver 39585738 Mar  3  2015 pro valet sheet.psd
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:30 Software & Installation Files
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Kids
total 12
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Isabella Storage
-rw-rw-r-- 1 noah         noah            0 Oct  5 23:05 kid-file.txt
drwxrwxr-x 6 woodieserver woodieserver 4096 Oct  4 12:15 Movies
-rw-rw-r-- 1 noah         kids            0 Oct  5 23:39 noah-delete-me-later.txt
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Noah Storage
-rw-rw-r-- 1 mike         mike            0 Oct  5 23:08 parent-file.txt
woodieserver@woodieserver:~$ 

```

EDIT: Will delete the text files i created and redo the touch.

---

### Post by mike359 on 2015-10-05
deleted other text files used in previous tests and touched new files as Mike & Noah.

```

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Kids
total 12
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Isabella Storage
-rw-rw-r-- 1 noah         kids            0 Oct  6 00:07 kids-file.txt
drwxrwxr-x 6 woodieserver woodieserver 4096 Oct  4 12:15 Movies
drwxrwxr-x 2 woodieserver woodieserver 4096 Oct  4 12:15 Noah Storage
-rw-rw-r-- 1 mike         kids            0 Oct  6 00:05 Parent-File.txt
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents
total 38688
drwxrwxr-x  5 woodieserver woodieserver     4096 Oct  4 12:19 Amy Storage
drwxrwxr-x  7 woodieserver woodieserver     4096 Oct  4 12:19 Mike Storage
drwxrwxr-x  6 woodieserver woodieserver     4096 Oct  4 12:16 Movies
drwxrwxr-x  3 woodieserver woodieserver     4096 Oct  4 12:31 Music
-rw-rw-r--  1 mike         parents             0 Oct  6 00:05 Parent-File.txt
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:31 Phone Backup
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:18 Pictures
-rwxrwxrwx  1 woodieserver woodieserver 39585738 Mar  3  2015 pro valet sheet.psd
drwxrwxr-x 10 woodieserver woodieserver     4096 Oct  4 12:30 Software & Installation Files
woodieserver@woodieserver:~$ 



```

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> Yes i did, I have just ran it again though.

```

woodieserver@woodieserver:~$ sudo chmod g+s /srv/2TBstorage/WoodieServer-Storage/Parents
woodieserver@woodieserver:~$ sudo chmod g+s /srv/2TBstorage/WoodieServer-Storage/Kids

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents
total 38688

-rw-rw-r--  1 mike         parents             0 Oct  5 23:38 delete-me-later.txt
...
-rw-rw-r--  1 mike         mike                0 Oct  5 23:08 parent-file.txt

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Kids
total 12
-rw-rw-r-- 1 noah         noah            0 Oct  5 23:05 kid-file.txt
...
-rw-rw-r-- 1 noah         kids            0 Oct  5 23:39 noah-delete-me-later.txt

-rw-rw-r-- 1 mike         mike            0 Oct  5 23:08 parent-file.txt
woodieserver@woodieserver:~$ 



```

So now we have the ability for any user to create a file or directory that has group inheritance and the proper permissions.

Now we need to take care of the files and directories that already existed in both the Parents and Kids directories.

To properly set the group on all the subdirectories and files of /srv/2TBstorage/WoodieServer-Storage/Parents directory we do this```
sudo chgrp -R parents   /srv/2TBstorage/WoodieServer-Storage/Parents
```

Post the output of this```
ls -l /srv/2TBstorage/WoodieServer-Storage/Parents

ls -l /srv/2TBstorage/WoodieServer-Storage/Parents/Pictures
```

---

### Post by mike359 on 2015-10-05
```

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents
total 38688
drwxrwxr-x  5 woodieserver parents     4096 Oct  4 12:19 Amy Storage
drwxrwxr-x  7 woodieserver parents     4096 Oct  4 12:19 Mike Storage
drwxrwxr-x  6 woodieserver parents     4096 Oct  4 12:16 Movies
drwxrwxr-x  3 woodieserver parents     4096 Oct  4 12:31 Music
-rw-rw-r--  1 mike         parents        0 Oct  6 00:05 Parent-File.txt
drwxrwxr-x 10 woodieserver parents     4096 Oct  4 12:31 Phone Backup
drwxrwxr-x 10 woodieserver parents     4096 Oct  4 12:18 Pictures
-rwxrwxrwx  1 woodieserver parents 39585738 Mar  3  2015 pro valet sheet.psd
drwxrwxr-x 10 woodieserver parents     4096 Oct  4 12:30 Software & Installation Files
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents/Pictures
total 40
drwxrwxr-x 3 woodieserver parents  4096 Oct  4 12:16 Amy's Phone
drwxrwxr-x 2 woodieserver parents  4096 Oct  4 12:17 Amys Phone
drwxrwxr-x 2 woodieserver parents  4096 Oct  4 12:18 Amy's Phone Pictures
drwxrwxr-x 3 woodieserver parents  4096 Oct  4 12:18 Camera Roll
drwxrwxr-x 2 woodieserver parents  4096 Oct  4 12:18 found Family Pics
drwxrwxr-x 2 woodieserver parents 12288 Oct  4 12:18 Mikes Phone Backup 02.10.2015
drwxrwxr-x 2 woodieserver parents  4096 Oct  4 12:18 My Phone PIctures
drwxrwxr-x 4 woodieserver parents  4096 Oct  4 12:17 Wedding Pictures
woodieserver@woodieserver:~$ 

```

Amazing. I worked out that the -R switch would make it recursive. So do i assume my next set would be..
```

sudo chgrp -R kids /srv/2TBstorage/WoodieServer-Storage/Kids

```

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> ```

woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents
total 38688
drwxrwxr-x  5 woodieserver parents     4096 Oct  4 12:19 Amy Storage
drwxrwxr-x  7 woodieserver parents     4096 Oct  4 12:19 Mike Storage
drwxrwxr-x  6 woodieserver parents     4096 Oct  4 12:16 Movies
drwxrwxr-x  3 woodieserver parents     4096 Oct  4 12:31 Music
-rw-rw-r--  1 mike         parents        0 Oct  6 00:05 Parent-File.txt
drwxrwxr-x 10 woodieserver parents     4096 Oct  4 12:31 Phone Backup
drwxrwxr-x 10 woodieserver parents     4096 Oct  4 12:18 Pictures
-rwxrwxrwx  1 woodieserver parents 39585738 Mar  3  2015 pro valet sheet.psd
drwxrwxr-x 10 woodieserver parents     4096 Oct  4 12:30 Software & Installation Files
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents/Pictures
total 40
drwxrwxr-x 3 woodieserver parents  4096 Oct  4 12:16 Amy's Phone
drwxrwxr-x 2 woodieserver parents  4096 Oct  4 12:17 Amys Phone
drwxrwxr-x 2 woodieserver parents  4096 Oct  4 12:18 Amy's Phone Pictures
drwxrwxr-x 3 woodieserver parents  4096 Oct  4 12:18 Camera Roll
drwxrwxr-x 2 woodieserver parents  4096 Oct  4 12:18 found Family Pics
drwxrwxr-x 2 woodieserver parents 12288 Oct  4 12:18 Mikes Phone Backup 02.10.2015
drwxrwxr-x 2 woodieserver parents  4096 Oct  4 12:18 My Phone PIctures
drwxrwxr-x 4 woodieserver parents  4096 Oct  4 12:17 Wedding Pictures
woodieserver@woodieserver:~$ 

```

Amazing. I worked out that the -R switch would make it recursive. So do i assume my next set would be..
```

sudo chgrp -R kids /srv/2TBstorage/WoodieServer-Storage/Kids

```
Yes, that should work.  Post back the output of ```
ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids

ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids/Movies
```

Edit:  We're not done yet.  We need to set the sgid bit too.  When I see this last output we can go on to that.  Don't get ahead of me.  :D

---

### Post by mike359 on 2015-10-05
```
woodieserver@woodieserver:~$ ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kidstotal 12
drwxrwxr-x 2 woodieserver kids 4096 Oct  4 12:15 Isabella Storage
-rw-rw-r-- 1 noah         kids    0 Oct  6 00:07 kids-file.txt
drwxrwxr-x 6 woodieserver kids 4096 Oct  4 12:15 Movies
drwxrwxr-x 2 woodieserver kids 4096 Oct  4 12:15 Noah Storage
-rw-rw-r-- 1 mike         kids    0 Oct  6 00:05 Parent-File.txt
woodieserver@woodieserver:~$ ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids/Movies
total 43535096
-rwxrwxrwx 1 woodieserver kids 1228680715 Jun 17 23:24 A.Bug's.Life.mp4
-rwxrwxrwx 1 woodieserver kids  366430110 Feb 21  2013 Alvin and the Chipmunks 3 Chipwrecked.mkv
-rwxrwxrwx 1 woodieserver kids 1631276014 Apr 19  2013 Alvin and the Chipmunks.mkv
-rwxrwxrwx 1 woodieserver kids 1584738663 Apr 19  2013 Alvin and the Chipmunks The Squeakquel.mkv
-rwxrwxrwx 1 woodieserver kids  371606966 Jun 18 00:01 Bear in the Big Blue House.mp4
-rwxrwxrwx 1 woodieserver kids  849415760 May 24 18:23 Big Hero 6.mp4
-rwxrwxrwx 1 woodieserver kids 1191521951 Jun 18 01:46 Cinderella.mp4



```

ARHH! missed the two -l switches (i've edited it in... no one will ever know ) :)

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> ```
woodieserver@woodieserver:~$ ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kidstotal 12
drwxrwxr-x 2 woodieserver kids 4096 Oct  4 12:15 Isabella Storage
-rw-rw-r-- 1 noah         kids    0 Oct  6 00:07 kids-file.txt
drwxrwxr-x 6 woodieserver kids 4096 Oct  4 12:15 Movies
drwxrwxr-x 2 woodieserver kids 4096 Oct  4 12:15 Noah Storage
-rw-rw-r-- 1 mike         kids    0 Oct  6 00:05 Parent-File.txt
woodieserver@woodieserver:~$ ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids/Movies
total 43535096
-rwxrwxrwx 1 woodieserver kids 1228680715 Jun 17 23:24 A.Bug's.Life.mp4
-rwxrwxrwx 1 woodieserver kids  366430110 Feb 21  2013 Alvin and the Chipmunks 3 Chipwrecked.mkv
-rwxrwxrwx 1 woodieserver kids 1631276014 Apr 19  2013 Alvin and the Chipmunks.mkv
-rwxrwxrwx 1 woodieserver kids 1584738663 Apr 19  2013 Alvin and the Chipmunks The Squeakquel.mkv
-rwxrwxrwx 1 woodieserver kids  371606966 Jun 18 00:01 Bear in the Big Blue House.mp4
-rwxrwxrwx 1 woodieserver kids  849415760 May 24 18:23 Big Hero 6.mp4
-rwxrwxrwx 1 woodieserver kids 1191521951 Jun 18 01:46 Cinderella.mp4



```

ARHH! missed the two -l switches (i've edited it in... no one will ever know ) :)

So now we need to set the sgid bits.   Lets do the Kids directories first.  The command is```

sudo chmod -R g+s  /srv/2TBstorage/WoodieServer-Storage/Kids

``` 

All of the existing directories will have the sgid bit set now.  Post the output of 
```
ls -l  ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids

 ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids/Movies 
```

---

### Post by mike359 on 2015-10-05
```

woodieserver@woodieserver:~$ ls -l  ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids
ls: cannot access ls: No such file or directory
/srv/2TBstorage/WoodieServer-Storage/Kids:
total 12
drwxrwsr-x 2 woodieserver kids 4096 Oct  4 12:15 Isabella Storage
-rw-rwSr-- 1 noah         kids    0 Oct  6 00:07 kids-file.txt
drwxrwsr-x 6 woodieserver kids 4096 Oct  4 12:15 Movies
drwxrwsr-x 2 woodieserver kids 4096 Oct  4 12:15 Noah Storage
-rw-rwSr-- 1 mike         kids    0 Oct  6 00:05 Parent-File.txt
woodieserver@woodieserver:~$ ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids/Movies
total 43535096
-rwxrwsrwx 1 woodieserver kids 1228680715 Jun 17 23:24 A.Bug's.Life.mp4
-rwxrwsrwx 1 woodieserver kids  366430110 Feb 21  2013 Alvin and the Chipmunks 3 Chipwrecked.mkv
-rwxrwsrwx 1 woodieserver kids 1631276014 Apr 19  2013 Alvin and the Chipmunks.mkv
-rwxrwsrwx 1 woodieserver kids 1584738663 Apr 19  2013 Alvin and the Chipmunks The Squeakquel.mkv
-rwxrwsrwx 1 woodieserver kids  371606966 Jun 18 00:01 Bear in the Big Blue House.mp4
-rwxrwsrwx 1 woodieserver kids  849415760 May 24 18:23 Big Hero 6.mp4
-rwxrwsrwx 1 woodieserver kids 1191521951 Jun 18 01:46 Cinderella.mp4



```

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> ```

woodieserver@woodieserver:~$ ls -l  ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids
ls: cannot access ls: No such file or directory
/srv/2TBstorage/WoodieServer-Storage/Kids:
total 12
drwxrwsr-x 2 woodieserver kids 4096 Oct  4 12:15 Isabella Storage
-rw-rwSr-- 1 noah         kids    0 Oct  6 00:07 kids-file.txt
drwxrwsr-x 6 woodieserver kids 4096 Oct  4 12:15 Movies
drwxrwsr-x 2 woodieserver kids 4096 Oct  4 12:15 Noah Storage
-rw-rwSr-- 1 mike         kids    0 Oct  6 00:05 Parent-File.txt
woodieserver@woodieserver:~$ ls -l -l /srv/2TBstorage/WoodieServer-Storage/Kids/Movies
total 43535096
-rwxrwsrwx 1 woodieserver kids 1228680715 Jun 17 23:24 A.Bug's.Life.mp4
-rwxrwsrwx 1 woodieserver kids  366430110 Feb 21  2013 Alvin and the Chipmunks 3 Chipwrecked.mkv
-rwxrwsrwx 1 woodieserver kids 1631276014 Apr 19  2013 Alvin and the Chipmunks.mkv
-rwxrwsrwx 1 woodieserver kids 1584738663 Apr 19  2013 Alvin and the Chipmunks The Squeakquel.mkv
-rwxrwsrwx 1 woodieserver kids  371606966 Jun 18 00:01 Bear in the Big Blue House.mp4
-rwxrwsrwx 1 woodieserver kids  849415760 May 24 18:23 Big Hero 6.mp4
-rwxrwsrwx 1 woodieserver kids 1191521951 Jun 18 01:46 Cinderella.mp4



```
Now we do the same for the  ls -l /srv/2TBstorage/WoodieServer-Storage/Parents folder.

The command```
sudo chmod g+s  /srv/2TBstorage/WoodieServer-Storage/Parents
```

The data to post back```
ls -l /srv/2TBstorage/WoodieServer-Storage/Parents/Pictures
```

Edit: Lots of typos on my part.  Sorry.

---

### Post by mike359 on 2015-10-05
```
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents/Pictures
total 40
drwxrwsr-x 3 woodieserver parents  4096 Oct  4 12:16 Amy's Phone
drwxrwsr-x 2 woodieserver parents  4096 Oct  4 12:17 Amys Phone
drwxrwsr-x 2 woodieserver parents  4096 Oct  4 12:18 Amy's Phone Pictures
drwxrwsr-x 3 woodieserver parents  4096 Oct  4 12:18 Camera Roll
drwxrwsr-x 2 woodieserver parents  4096 Oct  4 12:18 found Family Pics
drwxrwsr-x 2 woodieserver parents 12288 Oct  4 12:18 Mikes Phone Backup 02.10.2015
drwxrwsr-x 2 woodieserver parents  4096 Oct  4 12:18 My Phone PIctures
drwxrwsr-x 4 woodieserver parents  4096 Oct  4 12:17 Wedding Pictures
woodieserver@woodieserver:~$ 



```

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> ```
woodieserver@woodieserver:~$ ls -l /srv/2TBstorage/WoodieServer-Storage/Parents/Pictures
total 40
drwxrwsr-x 3 woodieserver parents  4096 Oct  4 12:16 Amy's Phone
drwxrwsr-x 2 woodieserver parents  4096 Oct  4 12:17 Amys Phone
drwxrwsr-x 2 woodieserver parents  4096 Oct  4 12:18 Amy's Phone Pictures
drwxrwsr-x 3 woodieserver parents  4096 Oct  4 12:18 Camera Roll
drwxrwsr-x 2 woodieserver parents  4096 Oct  4 12:18 found Family Pics
drwxrwsr-x 2 woodieserver parents 12288 Oct  4 12:18 Mikes Phone Backup 02.10.2015
drwxrwsr-x 2 woodieserver parents  4096 Oct  4 12:18 My Phone PIctures
drwxrwsr-x 4 woodieserver parents  4096 Oct  4 12:17 Wedding Pictures
woodieserver@woodieserver:~$ 



```

Okay.  This all looks good.  All we need to do is create a simple Samba share for each group.  Wait a minute here; we already did that.  Do they work now?

---

### Post by mike359 on 2015-10-05
Seems great so far on windows 7 & 10 :)
Legend!

---

### Post by mike359 on 2015-10-05
Strangely, seems much faster too?? :/

---

### Post by bab1 on 2015-10-05
> **mike359 said:**
> Strangely, seems much faster too?? :/
Try it for a while.  You can use the file manager GUI to see the ownership and permissions if that is easier for you.

I sent a PM about tomorrow's availability.

---

### Post by mike359 on 2015-10-06
Seemed to be working amazing but i have found 2 issues I would like to iron out.

1) I would like to share a temp folder that require no windows authentication, just in case i have any authentication errors in future but really need to move a file.
2) more importantly, i think i need something like a timeout for inactive samba connections, I don't know if this is a windows issue or a samba one.

I asked my daughter (izzi) to authenticate with her account on the "Kids" share, it worked flawlessly and didn't allow her to the "Parents" share.
I have come to the computer 2 hours later and tried to access the Parents folder and it wont have it, however the Kids Folder goes straight in.

I can only assume that the connection to the Parents folder is not working because windows is already authenticated using the "Izzi" who only has access to the kids folder.

---

### Post by bab1 on 2015-10-07
> **mike359 said:**
> Seemed to be working amazing but i have found 2 issues I would like to iron out.

1) I would like to share a temp folder that require no windows authentication, just in case i have any authentication errors in future but really need to move a file.

This is fairly easy to do now. At the */srv/2TBstorage/WoodieServer-Storage* location I would make a directory named *public *```
sudo mkdir -p /srv/2TBstorage/WoodieServer-Storage/public 
```...Then I would add all the users you want to the user group named ***users***. This group is already configured (gid=100) so you don't have to create it. Then you need to change the group ownership of */srv/2TBstorage/WoodieServer-Storage/public* ```
sudo chgrp -R users /srv/2TBstorage/WoodieServer-Storage/pubic 
```...and then set the group inheritance on public ```
sudo chmod -R g+s /srv/2TBstorage/WoodieServer-Storage/public 
```

Now all you need to do is share that directory in the smb.conf file like this```

[Public]
	comment = Public Share (no login)
        path = /srv/2TBstorage/WoodieServer-Storage/public
        browseable = yes
        guest ok = [COLOR="#FF0000"]yes[/COLOR]
       
        [COLOR="#FF0000"]force group = users[/COLOR]
        writeable = yes

```...and then you need to add this line to the [global] section of the smb.conf file
```
 map to guest = Bad User 
```...This line means that any user that has no Samba login is treated as a "Bad User" and is mapped to the guest account (nobody:nogroup).  You can read about this in the man page section below```

       map to guest (G)

           This parameter can take four different values, which tell smbd(8) what to do with
           user login requests that don't match a valid UNIX user in some way.

           The four settings are :

           ·   Never - Means user login requests with an invalid password are rejected. This
               is the default.

           ·   [B]Bad User - Means user logins with an invalid password are rejected, unless
               the username does not exist, in which case it is treated as a guest login and
               mapped into the guest account.[/B]

           ·   Bad Password - Means user logins with an invalid password are treated as a
               guest login and mapped into the guest account. Note that this can cause
               problems as it means that any user incorrectly typing their password will be
               silently logged on as "guest" - and will not know the reason they cannot
               access files they think they should - there will have been no message given
               to them that they got their password wrong. Helpdesk services will hate you
               if you set the map to guest parameter this way :-).
           ·   Bad Uid - Is only applicable when Samba is configured in some type of domain
               mode security (security = {domain|ads}) and means that user logins which are
               successfully authenticated but which have no valid Unix user account (and
               smbd is unable to create one) should be mapped to the defined guest account.
               This was the default behavior of Samba 2.x releases. Note that if a member
               server is running winbindd, this option should never be required because the
               nss_winbind library will export the Windows domain users and groups to the
               underlying OS via the Name Service Switch interface.

       Note that this parameter is needed to set up "Guest" share services. This is because
       in these modes the name of the resource being requested is not sent to the server
       until after the server has successfully authenticated the client so the server cannot
       make authentication decisions at the correct time (connection to the share) for
       "Guest" shares.

       Default: map to guest = Never

```

So Samba allows anyone access to the share when you use *_guest ok = yes_*, but the files are created and modified by the user ***nobody*** and the group is ***nogroup***.  Then the *force group* directive overrides the *nogroup* setting and all work is owned by the user-group named **users**, which all your users are a member of.  This means only the people in the users group will  have read write guest access to the Public share.  All others should have read only permissions.
>  
2) more importantly, i think i need something like a timeout for inactive samba connections, I don't know if this is a windows issue or a samba one.

I asked my daughter (izzi) to authenticate with her account on the "Kids" share, it worked flawlessly and didn't allow her to the "Parents" share.
I have come to the computer 2 hours later and tried to access the Parents folder and it wont have it, however the Kids Folder goes straight in.

I can only assume that the connection to the Parents folder is not working because windows is already authenticated using the "Izzi" who only has access to the kids folder.
There is no connection as you would think it to be.  Samba authenticates the user (who are you) to have access to the SMB resources.  The parameters in the share definition (the resource) then add restrictions (valid users).  If your daughter has logged in to a host (the Samba client) and not logged out, Samba has no way to know that some other user is now using that client.  Furthermore if this is a Windows computer the the logged in user is sent to Samba before you even attempt to access Samba via a login.

You would need to log your daughter out and log in using your own account.  In fact it is good practice to have any user, when done, to log un mount the share and log out out of the machine. I know that sometimes security is a bummer.  I’ve spent 25+ years rapping folks on the knuckles for using easy passwords or sharing passwords to get around security.  There have been countless numbers of machines that I have found where the user has just gotten up and walked away while still logged in.  I can preach but I know I'm not heard.  :-(

That being said, there is a deadtime [global] parameter that can be set in the smb.conf file.  It is in increments of minutes.  This is really a timeout so that the server isn't overwhelmed with connections that are not being used.  I've not used this so I do not know what happens.  Does the user authentication go away or only the connection between the client and the server.  FYI:  The server forks for each user session.  That's what the deadtime parameter is really trying to control.  The line would look like this in the [global] section```
deadtime = 15
```...for 15 minutes.

This is the man page section on deadtime```

       deadtime (G)

           The value of the parameter (a decimal integer) represents the number of minutes
           of inactivity before a connection is considered dead, and it is disconnected. The
           deadtime only takes effect if the number of open files is zero.

           This is useful to stop a server's resources being exhausted by a large number of
           inactive connections.

           Most clients have an auto-reconnect feature when a connection is broken so in
           most cases this parameter should be transparent to users.

           Using this parameter with a timeout of a few minutes is recommended for most
           systems.

           A deadtime of zero indicates that no auto-disconnection should be performed.

           Default: deadtime = 0

           Example: deadtime = 15

```
You can see all the parameters for the smb.conf file using this command```
man smb,conf
```

---

