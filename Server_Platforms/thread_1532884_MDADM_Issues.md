---
title: "MDADM Issues"
date: 2010-07-17
forum: Server Platforms
---

### Post by jmg999 on 2010-07-17
Hi,

I'm not certain that I'm posting this in the correct forum, so please feel free to move it, if necessary.

So, I've been having this on-going problem w/ a fileserver that I'd built, and I thought that it was about time that I sought advice on how to remedy my problems.

I have this home setup consisting of a one Windows XP Pro box and one Ubuntu Server rig that houses my fileserver.  I'm running RAID 5 using MD Raid.  I also use samba to connect to the fileserver from the Windows box.  Ever since I'd built this fileserver, I've had the same recurring issue...

When transferring files TO the array, utilizing Samba, FROM my XP box, the transfers take FOREVER.  Transferring files FROM the array, utilizing Samba, TO my XP box seem to move at a normal rate of speed.  For instance, I could transfer a 1GB file from the XP to the array, and it might take 10-20 minutes.  Transferring the same file from the array to the XP box might only take a minute or two.

At this point, the array is almost full, and I'm adding another array to this server, but I'd really like to resolve this issue first.  I've tried both searching the forums and Googling for answers, but I can't come up w/ anything.  Any help would be greatly appreciated.  Thank you.

```
cat /etc/issue
Ubuntu 8.04.4 LTS \n \l
``````
 cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdf1[0] sde1[7] sdd1[6] sdc1[5] sdb1[4] sdi1[3] sdh1[2] sdg1[1]
      6837319552 blocks level 5, 64k chunk, algorithm 2 [8/8] [UUUUUUUU]
      
unused devices: <none>
``````
sudo mdadm --detail /dev/md0        
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Jun 16 20:03:13 2009
     Raid Level : raid5
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 17 00:55:56 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : c6aed8c5:00493db7:72560c0a:77e3a89a (local to host USC)
         Events : 0.168

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8       97        1      active sync   /dev/sdg1
       2       8      113        2      active sync   /dev/sdh1
       3       8      129        3      active sync   /dev/sdi1
       4       8       17        4      active sync   /dev/sdb1
       5       8       33        5      active sync   /dev/sdc1
       6       8       49        6      active sync   /dev/sdd1
       7       8       65        7      active sync   /dev/sde1
```

---

### Post by YesWeCan on 2010-07-17
My first thought is what does RAID have to do with this? Do you have the same problem if you create a new samba share directory on the ubuntu server that is not located on the RAID array?

---

### Post by jmg999 on 2010-07-17
So, you think this is a samba issue *only*?  I will create an accessible directory off the array and post the results.  Thanks for your assistance.

---

### Post by YesWeCan on 2010-07-17
I am not expert enough to imagine how the RAID would cause this samba share dysfunction. It could be related to RAID, samba, your windows network or something else entirely. Testing whether the RAID is actually a cause is relatively easy so I would start there. :)

---

### Post by YesWeCan on 2010-07-17
Misc ideas:
You could test the RAID upload performance independently of samba: do client sftp (psftp on Windows: google Putty) transfers to and from a RAID directory and measure the performance both ways. repeat from a non-RAID directory.

Disable/unmount the RAID completely and redo the samba and sftp tests.

You can see whether it is Windows specific. Boot one of your clients from a live Ubuntu CD and connect to the server's samba share. Then do upload and download tests.

But you probably don't need to go this far. Anyway, you get the idea.

---

### Post by jmg999 on 2010-07-17
I'm having trouble w/ the new samba share.  My setup is pretty basic in this fileserver.  I have the OS HDDs in a RAID 1 mirror off the array.  I created a directory in my home directory, and I can connect to it, as well as copy/read from it, but I'm unable to write to it.

drwxr-xr-x 2 jeffe jeffe     4096 2010-07-17 12:18 test

I'm signed in as jeffe, so it's not a user perms issue.    

This is the portion of smb.conf that I'd added to allow access to this directory.

```
[/dev/sdi2]
        comment = Root
        browseable = yes
        writable = yes
        path = /home/jeffe/test
        valid users = jeffe
```

I also uncommented these two lines parameters...

```

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes
```

Any thoughts on why I'm not able to write to this directory?

---

### Post by YesWeCan on 2010-07-17
I am not a samba expert. It may be because your user name is not being recognized. You may need to insert 'guest = ok' and remove the valid users requirement to get it working, at least for testing purposes.

I'd recommend reading the Samba file server instructions here: [https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html)
and setting up your share directories accordingly.

---

### Post by jmg999 on 2010-07-18
The strange thing is, I can read, write, and execute any and all files from the array using the exact same setup in smb.conf.  I simply copied what was I had previously used to share this directory, although that didn't work, b/c it was my home directory, so I had to uncomment those other two parameters to be able to map the path.

I'll try adding 'guest = ok' in smb.conf, and I'll also read the setup instructions.  I had read through that when I'd initially set this server up, but I'll see if I can find the answer in there, and once I have it working, I'll test the transfer speeds.  

Thanks for your help!

---

### Post by YesWeCan on 2010-07-18
[QUOTE=jmg999]When transferring files TO the array, utilizing Samba, FROM my XP box, the transfers take FOREVER.  Transferring files FROM the array, utilizing Samba, TO my XP box seem to move at a normal rate of speed.  For instance, I could transfer a 1GB file from the XP to the array, and it might take 10-20 minutes.  Transferring the same file from the array to the XP box might only take a minute or two.[/QUOTE]
Uploading from your XP box takes about 10 times as long as downloading. Curious coincidence. Are these boxes on the same wired subnet and are they directly routed to one another?

---

### Post by ian dobson on 2010-07-18
Hi,

So are you sure the problem is your RAID array. Please try the following:-

1) dd if=/dev/zero of=your_array/somefilename bs=4K count=100000

This will create a file called somefilename on your array and display how quick your array is.

2) Copy a file to the array using ftp rather than samba, and wite down the speed that the file is written.

Once you have this information, post it here. It could be that the raid array is slow at writing, samba could be slow or a network problem.

Regards
Ian Dobson

---

### Post by jmg999 on 2010-07-18
Well, I was finally able to create a share on the OS HDD that I was able to write to.  I tested YesWeCan's method, and the file transfer still took forever.  So, it's obviously not the array.  A 1GB file took about 20-25 minutes.  One thing that I forgot mention in my initial post was that if I'm transferring two files at once, it goes at normal speed (a 1GB file would take 2 minutes or so).  Just to be clear, I'm not transferring them together.  I'm performing two separate operations.  I cut/paste one file and then the other.  

In addition to this issue, I've run into another problem w/ Samba.  I can no longer connect to my array.  After fiddling around trying to get the test share to work, I must've screwed something up.  When I try to map the drive, I get the authentication pop-up, but when I enter my credentials, and hit 'OK', the dialogue box remains, and no connection is made.  I even tried adding 'guest ok = yes', but that didn't work, either.  It still asked for my credentials.  Any suggestions on what to check?  If you need to see any part of my smb.conf, please let me know.  Thank you.

---

### Post by YesWeCan on 2010-07-18
[QUOTE=jmg999]One thing that I forgot mention in my initial post was that if I'm transferring two files at once, it goes at normal speed (a 1GB file would take 2 minutes or so).  Just to be clear, I'm not transferring them together.  I'm performing two separate operations.  I cut/paste one file and then the other.[/QUOTE]
That sounds like a huge clue to somebody with more experience. Let me understand this: in Windows client you cut and paste a big file to the linux network share folder. The transfer rate is pitiful. Then you cut and paste a different, big file into the share folder and BOTH transfers then happen at correct speed?
I have no idea. I would probably uninstall samba and reinstall it. What about samba's log files - do they report any problems?
It is possible the problem is with XP, of course. Can you eliminate XP as a suspect?

---

### Post by jmg999 on 2010-07-18
Yes, you seem to have it correct.  The thing is, if one transfer finishes before the other (which always happens), the other transfer then slows down to that pitiful rate of speed again.  It's really odd.  I'll check the samba log, and see if there's any indication in there.  I can hook a laptop up to the network, and test from there.  I'd really like to figure out what mistake I made in the smb.conf file, b/c it's prohibiting me from connecting to the array.

If it makes any difference, I login to the XP box as administrator, but I've always done and been able to connect to the array.  Here's my smb.conf...

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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = BAMA

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
;   bind interfaces only = true



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
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

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
;   printer admin = @lpadmin


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

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

[Test Share]
        comment = /home/jeffe/test
        browseable = yes
        path = /home/jeffe/test
        valid users = jeffe
        writeable = yes
        create mask = 0755
[Disk]
        comment = Media
        browseable = yes
        writeable = yes
        path = /disk
        valid users = jeffe
[Disk2]
        comment = Media
        browseable = yes
        writeable = yes
        path = /disk2
        valid users = jeffe


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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

```

---

### Post by jmg999 on 2010-07-18
Well, I resolved the issue of not being able to connect to the array.  I had to remove this portion of smb.conf:

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
   valid users = %S

---

### Post by YesWeCan on 2010-07-18
Good. Permissions are complicated. Moreso when Windows is involved. You are on a private home network, right? So you can safely simplify the whole thing by having minimal security and get it working and then add more. Simplify.
Using your laptop to confirm the speed dichotomy with another PC is good. What OS is your laptop running?
I'd reinstall samba for good measure. Won't hurt.

---

### Post by jmg999 on 2010-07-18
I'd like to try what Ian mentioned, but I don't know how to set up an FTP server on Ubuntu.  I'll have to find a tutorial somewhere.  In the meantime, I'll hook up the laptop.

---

### Post by YesWeCan on 2010-07-18
sudo apt-get install openssh-server

SSH stands for secure shell. It provides a suite of useful encrypted, remote connection services. You can log in to your linux box from a client and the connection is encrypted automatically. Essential for logging in over the public internet, for example.

It has a configuration file at /etc/ssh/sshd_conf
This may need a tweak (I can't remember) to add your linux user name to "Allowed users". See 'man sshd_conf'.

[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

On your Windows PC just download one of the suite of Putty tools called pscp.exe (Putty secure copy): [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
scp is like sftp but simpler.

ftp stands for "file transfer protocol" and has been used for donkeys years. Nowadays it has been superceeded by sftp "secure ftp" that encrypts the connection by default.

More useful than scp is ssh login. On a linux client you would install ssh_client and connect and get a server terminal locally  with the command 'ssh fred@linuxServer'. You are now logged in to your remote server from your client. Very, very useful. You can do more sophisticated things with SSH like port-forwarding so that your client application can listen on a port on the remote server, and you can use the -X option to see a GUI on the client and -C to compress the data stream for better speed. However, using ssh for GUI is quite slow and it is better to use VNC or similar. However, you can do tricks like making an encrypted port-forward "tunnel" over which you pipe the VNC desktop for security on the public internet.

ssh defaults to using port 22. So if you are roaming and want to log in to your server your home router/firewall has to be told to forward port 22 packets to your server (an opening in the firewall). In the sshd_conf file you can specify a different port for the server to listen on, or a selection of ports.
Worth learning about SSH.

---

### Post by jmg999 on 2010-07-19
Thanks for the in-depth explanation. :)

I have the ssh setup already.  That's how I connect now.  What I need is to setup an ftp server on the fileserver to run the test that Ian had recommended.

---

### Post by YesWeCan on 2010-07-19
:rolleyes: ftp, scp, ssh - hey give me a break, they are all three letters long. :p
I must learn to read.

If you are running 10.04 you are probably running an ftp server already. From a Windows browser 'ftp://serverIP'

But I don't see that it matters much what method you use, ftp or scp. I had in mind just checking that you can transfer to and from the RAID at high speed by some method. Ian may have something specific in mind to do with ftp, though.

---

### Post by jmg999 on 2010-07-19
Oh, I see what you're saying.  I'm wondering if that file he's having me  create on the array will capture the transfer speeds of an scp  transfer?  I'll give it a try.
 
 I tried [ftp://serverIP](ftp://serverIP), but I got nothin'.  I'm running 8.04.4 LTS.  
 
 I should probably tell you the whole story on this server to see if it  makes any difference.
 
 I built this thing originally w/ a Promise EX8350 RAID controller w/  8x500GB HDDs in RAID 5.  Less than two years later, the card went bad,  and I lost all the data on the array.  I had Promise replace the card,  and in the meantime, I purchased this stand-alone  direct-attached-storage device.  This is it...
 
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16816132016&cm_re=esata_4_drives-_-16-132-016-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132016&cm_re=esata_4_drives-_-16-132-016-_-Product)
 
 I'm using 8x1TB HDDs in a RAID 5 array.  It's a dual eSATA connection,  and I've had another issue w/ it in the past.  If I transfer too much  data to it directly, the array goes offline, and the entire thing has to  resync, which takes 18-20 hours.  Eventually, I started limiting how  data I would transfer to the array at one time, but I'm beginning to  think that the problems are all inter-related.

---

### Post by jmg999 on 2010-07-20
I found these instructions for installing an FTP server:

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

But, it didn't work.  I can't even get the process running.  It says that it starts, but it's not to be found in ps.

```
sudo /etc/init.d/vsftpd start
 * Starting FTP server: vsftpd                                                           [ OK ] 
```

```
ps auxwww |grep vs
jeffe     7357  0.0  0.0   3004   768 pts/0    S+   08:25   0:00 grep vs 
```

```
sudo /etc/init.d/vsftpd stop
 * Stopping FTP server: vsftpd                                                                  No /usr/sbin/vsftpd found running; none killed.
                                                                                         [ OK ] 
```

---

### Post by jmg999 on 2010-07-20
Ok, I finally got the FTP server working.

Here are the results of dd:

```
sudo dd if=/dev/zero of=/disk2/arraytest bs=4k count=100000
100000+0 records in
100000+0 records out
409600000 bytes (410 MB) copied, 3.98397 s, 103 MB/s 
```

This is the result of the FTP transfer.  I ran it a few times to make sure I had a reasonable average...

```
Tue Jul 20 10:14:51 2010 [pid 7709] CONNECT: Client "192.168.2.10"
Tue Jul 20 10:14:51 2010 [pid 7708] [jeffe] OK LOGIN: Client "192.168.2.10"
Tue Jul 20 12:10:54 2010 [pid 6819] CONNECT: Client "192.168.2.10"
Tue Jul 20 12:10:54 2010 [pid 6818] [jeffe] OK LOGIN: Client "192.168.2.10"
Tue Jul 20 12:16:29 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 28171.85Kbyte/sec
Tue Jul 20 12:17:14 2010 [pid 6820] [jeffe] OK DELETE: Client "192.168.2.10", "/disk2/temp/test_file.avi"
Tue Jul 20 12:17:56 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 28461.97Kbyte/sec
Tue Jul 20 12:18:00 2010 [pid 6820] [jeffe] OK DELETE: Client "192.168.2.10", "/disk2/temp/test_file.avi"
Tue Jul 20 12:19:18 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 28487.57Kbyte/sec
Tue Jul 20 12:20:15 2010 [pid 6820] [jeffe] OK DELETE: Client "192.168.2.10", "/disk2/temp/test_file.avi"
Tue Jul 20 12:20:59 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 27907.82Kbyte/sec
Tue Jul 20 12:21:14 2010 [pid 6820] [jeffe] OK DELETE: Client "192.168.2.10", "/disk2/temp/test_file.avi"
Tue Jul 20 12:22:06 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 21500.00Kbyte/sec 
```

---

### Post by YesWeCan on 2010-07-20
Not too shabby. Would you explain a little. This is copying in which direction and is it the RAID5 or the test directory? What about copying the other way.

---

### Post by jmg999 on 2010-07-20
The directory was to test Samba transfers.  That directory was not on the array, and it still had issues, so we figured that it was most likely a Samba issue.  The FTP experiment was conducted by transferring a 1GB file from the Windows box to the array (/disk2/temp/).  As you can see, those speeds were quite fast but still not as fast as DD wrote.  The speeds from the array to the Windows box have never been a problem, but I did test from the OS HDD on the server to the array, and those speeds were quite fast, as well.

---

### Post by YesWeCan on 2010-07-20
You've lost me a little. dd is the kernel writing directly to the array at 100MB/s or so. The ftp uploads from Windows box to the array are over an ethernet connection and are at about 30MB/s. What speed did you expect?
You haven't said what speed ftp uploads from the array to Windows come in at. How much difference does the direction make with ftp and is this difference similar to the samba method difference? Just curious. :)

---

### Post by jmg999 on 2010-07-21
Going from the array to Windows isn't the problem.  Those speeds, utilizing Samba, have always been fine.  The problem has always been going from Windows to the array.  The FTP transfer of a 1GB file took about 30 seconds from Windows to the array.  The same file being transferred from Windows to the array via Samba took over 20 minutes.

---

### Post by ian dobson on 2010-07-22
Hi jmg99,

Sorry I didn't get back to you earlier, I've been working in germany this week.

Yor results look interesting, dd can transfer at 100mb/sec but FTP only reaches 25mb/sec. What network card are you using? It almost looks as if the tcp/ip receive buffers are too small/your network card can't handle receiving large data packages.

When I get the chance I'll play abit with my RAID5/samba system it see if I can find anything interesting.

Regards
Ian Dobson

---

### Post by jmg999 on 2010-07-22
Thanks for the reply, Ian.  No worries on not getting back...priorities. :)

This is my NIC:

>  *-network
             description: Ethernet interface
             product: RTL-8169 Gigabit Ethernet
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@0000:06:09.0
             logical name: eth1
             version: 10
             serial: 00:22:3f:e0:b0:56
             size: 1GB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-
fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK du
plex=full ip=192.168.2.40 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes
 port=twisted pair speed=1GB/s 

Even though I'm able to transfer at 25Mb/s via FTP, that still doesn't explain why Samba can't make a single transfer in the direction of the fileserver at reasonable speeds.  Any thoughts on that?  Thanks.

---

### Post by YesWeCan on 2010-07-22
I am curious to compare the average xfer rates in all cases.
To server and from server for both ftp and samba type transfers.

To server from XP:
   ftp is about 28MB/s.
   Samba is about 1MB/s (from your post #1 1GB in 15 mins)

To XP from server:
   Samba is about 11MB/s
   ftp is ?

---

### Post by ian dobson on 2010-07-23
Hi,

I've just played about with my backend server (RAID5 array,Gbit lan,8Gb ram) and when copying data from my XP box to the server I'm able to copy 2Gb in about 45seconds.

With my first tests I was only getting about 2Gb in 2 minutes and after changing afew options and rebooting the server I'm getting much better results.

The changes I made to the server are:-
in /etc/samba/smb.conf
[Globals]
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536 rlimit_max=16384

and in  /etc/security/limits.conf
* - nofile 16384

So before I optimised samba I was getting 16Mbyte/sec and after the optimisation I getting 45Mbyte/sec.

Regards
Ian Dobson

---

### Post by YesWeCan on 2010-07-23
That's interesting Ian. What rate do you get the other way: server to XP?

---

### Post by ian dobson on 2010-07-23
Hi,

OK I just copied a 2.5Gb file from the array to the local XP harddisk at about 27Mbyte/sec. Note the array is being hammered at the moment (Recording 2 HD programs at the same time as running the test) so the results might be better when the array isn't so active.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-07-24
Hi,

also maybe try running the testparm program on your server. This checks you smbd.conf configuration file for errors/linux file limits configuration.

edit: OK I just tested copying from the server to a XP system and hit about 2.5Gb/min so thats about 40Mbyte/sec.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-07-24
Hi,

Last post for afew days (leaving the country again).
I've played about with the samba smbd.conf file and found that "socket options" makes a really huge difference to the performance.

If I remove the line and restart smbd I only get afew Mbyte/sec (I gave up after 5minutes trying to transfer a 2Gb file). On my network setting the send/receive buffer to 128k made the biggest difference. So for me the configuration that gives the best read/write performance from a XP box is:-

socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072 SO_SNDBUF=131072

On my Windows 7 box I'm only seeing about 6Mbyte/sec writing to the server, but that could be caused by my slow 100Mbit router or a really crappy network driver.

Regards
Ian Dobson

---

### Post by jmg999 on 2010-07-24
Hi Ian,

Thanks for looking into that.  I really appreciate it.  Nonetheless, neither of your solutions alleviated my problem.  First, I tried this...

```
The changes I made to the server are:-
in /etc/samba/smb.conf
[Globals]
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536 rlimit_max=16384

and in  /etc/security/limits.conf
* - nofile 16384 
```

I'd never made changes to /etc/security/limits.conf before, so this option was commented out.  I uncommented it, and added your limit, so it now looks like this...

>          - nofile 16384 - max number of open files 

I restarted Samba, and it had no effect.  I then tried your second value for smb.conf, and it now appears as this...

> # Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072 SO_SNDBUF=131072 

I restarted Samba, again, and again, it didn't resolve the issue.  

I have tried testparm before, but I didn't see anything wrong w/ the output.  Just to be sure, here it is...

> Load smb config files from /etc/samba/smb.conf
Processing section "[Disk]"
Processing section "[Disk2]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = BAMA
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072 SO_SNDBUF=131072
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[Disk]
        comment = Media
        path = /disk
        valid users = jeffe
        read only = No

[Disk2]
        comment = Media
        path = /disk2
        valid users = jeffe
        read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers   

Any additional help you might be able to provide would be great.  Thank you, again!

Jeff

---

### Post by ian dobson on 2010-07-24
Hi,

I'm starting to think your problem is the network card. Do you have a PCIexpress network card that you can install and test.

Realtek cards aren't known to be the best cards, most motherboard manufacturer's use them as they're cheap and don't need an external pxy.

Regards
Ian Dobson

---

### Post by YesWeCan on 2010-07-24
Some similarities
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/114171](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/114171)

---

### Post by ian dobson on 2010-07-25
> **YesWeCan said:**
> Some similarities
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/114171](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/114171)

Thats a really old bug.

I just tested my MythTV frontend system (Mythbuntu 10.04), it has a rtl 8169 network card and I'm seeing really bad (8Mbyte/sec receive/4Mbyte/sec transmit) network performance using CIFS to my samba system. So it looks as if the rtl cards are cheap and nasty.

Regards
Ian Dobson

---

### Post by YesWeCan on 2010-07-25
Yes that old bug report applied to 7.04. Jeff is running a nearly as old 8.04. Just a thought. The bug report describes the same symptom of smb transfers being really slow for a single file but fast again for multiple concurrent file transfers.
So I reckon this more than a coincidence. I guess a new mfr card will fix it or perhaps also an upgrade to 10.04. I'm not sure how one finds out whether a Ubuntu defect was ever fix or not.

---

### Post by jmg999 on 2010-07-25
So, it appears that my problem is resolved.  Today, I was attempting to put my Promise controller array online and was running into various issues w/ compiling the array.  After some searching around, I found a thread that mentioned a few different Promise cards and how they were having similar issues.  They didn't specifically mention my card, but they did say that a kernel upgrade resolved their issues.  Since 10.04 LTS came out recently, I thought I'd give it a go.  

I upgraded just now, and everything went smoothly.  Interestingly enough, I chose the option to keep my smb.conf file, instead of upgrading to the most recent version of Samba.  I'll do that manually later on.  The first thing I tested was the transfer speed to the array, and sure enough, the problem no longer exists.  I was able to transfer a 1GB file in ~30 seconds.  

YesWeCan, I'm wondering if the upgraded RealTek driver solved this issue.  Either way, it's no longer a problem. 

I want to thank you both for sticking through this w/ me.  It's been a headache ever since I can remember.  I appreciate your suggestions and research.  Thank you so much!

---

### Post by ian dobson on 2010-07-25
Hi jmg99,

I guess the kernel driver in 7.04 wasn't the fastest.  Glad to see that the problem is solved.

Regards
Ian Dobson

---

### Post by YesWeCan on 2010-07-25
Great news, Jeff. It is very rewarding for all concerned when a long-standing problem gets sorted out. Glad to have been of some help. :D

Don't forget to mark this thread as "solved".

---

### Post by jmg999 on 2010-07-25
Ooh, thanks for reminding me! :)

---

