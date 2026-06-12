---
title: "Samba - Mount and Share External Drive"
date: 2007-04-28
forum: Server Platforms
---

### Post by dbqp on 2007-04-28
Hi All,

I am having a heck of a time with this one. I have a web/FTP/Mail server that I installed using the howtoforge Perfect Ubuntu Server (6.10). I then wanted to have a file server so I installed a Samba Server using the following HowTo:

[http://howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10) (primarily page 4 and 5)

I have a properly setup share/path where other users attached to the network are able to access this shared path. (the shared path created was /home/shares/music/audio on the primary hard drive). I now want to add my external drive (USB FAT32) where most of my data was stored when it was connected to a windows machine (it was shared through windows and could always be accessed).

When I plug in the drive, I can mount it (it is not pre-mounted in the fstab) and it shows up as a mounted drive. Problem is two-fold 

1. I want to mount the external drive via fstab on start-up. 

2.  I cannot seem to connect to this drive after creating a shared directory, and chown/chmod ing it. I also included this new path in the smb.conf. See three items below:

Here is the output of fdisk -l

```
root@dbqp:/home/david# fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30356   243834538+  83  Linux
/dev/hda2           30357       30401      361462+   5  Extended
/dev/hda5           30357       30401      361431   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    c  W95 FAT32 (LBA)
```

And here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=33dd3c2e-3242-402f-b84d-6f31abfa05b1 /               ext3    defaults,errors=remount-ro,usrquota,grpquota  0       1
# /dev/hda5
UUID=f6fcd9ba-89d6-4f33-af04-d207acb21475 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

And here is smb.conf:

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
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
   workgroup = dbqp
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
   load printers = yes
   printcap name = CUPS
   printing = CUPS
   printer admin = @lpadmin
   
   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usernod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000
   template shell = /bin/bash


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3

[public]
   browseable = yes
   public = yes


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
   
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   write list = root, @smbadmin


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no
   guest ok = yes
   writable = no
   share modes = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no
   guest ok = no

[allusers]
  comment = All Users
  path = /home/shares/music/audio
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes

[MYBOOK]
  comment = All Users
  path = /media/MYBOOK/shares
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes

```


I know this post is long - sorry if your eyes are now crossed. Any help, direction, or assistance is appreciated in advance.

Thanks.

---

### Post by dbqp on 2007-04-30
^^bump

FYI - I have searched all around for both of these issues, but am unable to find a solution that really pertains to this set-up.

thanks,

---

### Post by MCMcButtah on 2007-04-30
Did you restart samba after your mounted and shared your usb2 drive? I had to do this with my usb2 drive by using this command:

sudo /etc/init.d/samba restart

Here are the entries in fstab and smb.conf to share a folder out on my external

fstab:

/dev/sdd1 /media/ext500 ntfs-3g defaults,force 0 0

smb.conf:

[MUSIC]
path = /media/ext500/Music/
read only = no
valid users = mcmcbuttah
write list = mcmcbuttah
invalid users =
case sensitive = no
hide dot files = no

I have had a bunch of samba problems myself since my upgrade to fiesty. I have resolved the issues on my server by re-installing samba and removing the msdfs proxy entry from smb.conf. I still have not been able to get mounting of samba shares on my workstation working correctly.

---

### Post by dbqp on 2007-04-30
> Did you restart samba after your mounted and shared your usb2 drive? I had to do this with my usb2 drive by using this command:

sudo /etc/init.d/samba restart

Yes, I do this ANY time a change is made to the smb.conf file.

> Here are the entries in fstab and smb.conf to share a folder out on my external

fstab:

/dev/sdd1 /media/ext500 ntfs-3g defaults,force 0 0

Since my external drive is FAT32 should it be vfat32 instead of your type ntfs-3g as a file system?

> smb.conf:

[MUSIC]
path = /media/ext500/Music/
read only = no
valid users = mcmcbuttah
write list = mcmcbuttah
invalid users =
case sensitive = no
hide dot files = no

When I add a new path, do I just type in a new entry into the smb.conf file separately under other paths?

Thank you SO much for posting a response - any response is appreciated and I am going to try your suggestion above upon your response to my reply.

Thanks again!

---

### Post by dbqp on 2007-04-30
Hey! I am now browsing and able to read+write the files on the external drive.

I went ahead and started messing around with the information MCMcButtah provided, but I had to tweak it for the FAT32 file system that I found here:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Down towards the bottom of the page gave me the fs settings.

Sometimes it just takes one reply to a problem to understand and/or see things from another perspective!

Thank you MCMcButtah.

---

### Post by MCMcButtah on 2007-04-30
Yes, I am sorry I forgot to mention that and good catch. My external is ntfs.
I am very a much a noob so I should be careful what I say. I should add that disclaimer 
to any advice I give :)

So what was it exactly that fixed your problem? You just didn't have the entry to your share
in smb.conf? Just want to clarify in case anyone else happens on this thread with samba issues. Thanks.

---

### Post by dbqp on 2007-04-30
> **MCMcButtah said:**
> Yes, I am sorry I forgot to mention that and good catch. My external is ntfs.
I am very a much a noob so I should be careful what I say. I should add that disclaimer 
to any advice I give :)

No worries! It's having a voice and willing to throw ideas out there. Just like I should have done to complete this for anyone else when reading this thread...which leads me to:

> So what was it exactly that fixed your problem? You just didn't have the entry to your share
in smb.conf? Just want to clarify in case anyone else happens on this thread with samba issues. Thanks.

I did have the entry in the smb.conf file, but I failed to have it "mounted" on startup by including it in fstab. By providing the example text from your own smb.conf file I was also able to understand SAMBA a little better (the paths and permissions entries).

That was about it - I had two pieces, but incomplete. I was mouting the drive manually after startup and then the smb.conf code was calling something that really wasn't there (or so I assume).

Here are the updated, working files:

output of fdis -l
```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30356   243834538+  83  Linux
/dev/hda2           30357       30401      361462+   5  Extended
/dev/hda5           30357       30401      361431   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    c  W95 FAT32 (LBA)

```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=33dd3c2e-3242-402f-b84d-6f31abfa05b1 /               ext3    defaults,errors=remount-ro,usrquota,grpquota  0       1
# /dev/hda5
UUID=f6fcd9ba-89d6-4f33-af04-d207acb21475 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/media/MYBOOK	vfat iocharset=utf8,umask=000 0 0

```

smb (I even added another path where only one person has permission)
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
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
   workgroup = dbqp
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
   load printers = yes
   printcap name = CUPS
   printing = CUPS
   printer admin = @lpadmin
   
   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usernod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000
   template shell = /bin/bash


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3

[public]
   browseable = yes
   public = yes


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
   
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   write list = root, @smbadmin


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no
   guest ok = yes
   writable = no
   share modes = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no
   guest ok = no

[allusers]
  comment = All Users
  path = /home/shares/music/audio
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes

[MYBOOK]
  comment = All Users
  path = /media/MYBOOK/Shared
  read only = no
  valid users = @users
  force group = users 
  writable = yes
  case sensitive = no
  hide dot files = no

[MYBOOK-dpyle]
  comment = dbqp
  path = /media/MYBOOK/
  read only = no
  valid users = dbqp
  force group = users 
  writable = yes
  case sensitive = no
  hide dot files = no
```

I hope it clarifies the problem and solution.

:guitar:

---

