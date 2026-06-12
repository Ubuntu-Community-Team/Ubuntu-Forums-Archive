---
title: "samba unauth'd issue"
date: 2010-09-26
forum: Server Platforms
---

### Post by robsablah on 2010-09-26
hey guys. 
i've been trying to do this on my own but now im gonna need a little hand

i can't get into shares without logging in as a user
 - this is the same for windows and linux
this same error im having on 2 different computers across 2 different networks - i can fully modify both

BOTH LOCALTIONS:
the error is - failed to mount windows share (im so sick of this error :))
the log says - 
> robert@WATTSRV:~$ tail /var/log/samba/log.lr-uber 
[2010/09/26 13:52:37,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service software, path /media/Elements/software 

LOCATION 1:

SMB.conf
> 
#======================= Global Settings =======================

[global]
usershare owner only = false
   workgroup = WORKGROUP

   server string = %h server (Samba, Ubuntu)
;   wins server = w.x.y.z

   dns proxy = no
;   name resolve order = lmhosts host wins bcast

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
  unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes


   map to guest = bad user

########## Printing ##########

   load printers = yes

   printing = cups
   printcap name = cups

############ Misc ############


;   include = /home/samba/etc/smb.conf.%m

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes

;   usershare max shares = 100

   usershare allow guests = yes

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon


   usershare allow guests = yes
;   guest ok = yes
;   read only = yes
;   share modes = no


;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0777
   writeable = yes

[movies]
   comment = Movies
   browseable = yes
   path = /media/Movies/Movies/
   guest ok = yes
   read only = yes
   write list = robert

[tv shows]
   comment = tv shows
   browseable = yes
   path = /media/Tv Shows/tvshows
   guest ok = yes
   read only = yes
   write list = robert

[Japanese Anime]
   comment = Anime Tv Shows
   browseable = yes
   path = /media/Tv Shows/anime
   guest ok = yes
   read only = yes
   write list = robert

[software]
   comment = software
   browseable = yes
   path = /media/Elements/software
   guest ok = yes
   read only = yes
   write list = robert

[temp movies]
   comment = not really ready for the collection, view if you can
   browseable = yes
   path = /media/Movies/temp movies
   guest ok = yes
   read only = yes
   write list = robert

[recently downloaded]
   comment = recently downloaded
   browseable = yes
   path = /media/5/recently downloaded
   guest ok = yes
   read only = yes
   write list = robert

[dropbox]
   comment = your change to contribute - put stuff here!
   browseable = yes
   path = /media/5/dropbox
   guest ok = yes
   read only = no
   writable = yes
   create mask = 0777

[New Music]
   comment = Music
   browseable = yes
   path = /media/Elements/music
   guest ok = yes
   read only = yes
   write list = robert

[Music]
   comment = Music
   browseable = yes
   path = /media/5/music
   guest ok = yes
   read only = yes
   write list = robert

[drives]
   comment = 
   browseable = no
   path = /media/
   guest ok = no
   read only = yes
   write list = robert candace

[www]
   comment =
   browseable = yes
   path = /www
   guest ok = yes
   read only = yes
   write list = robert

;   write list = root, @lpadmin


;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom



testparm:
> 
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[movies]"
Processing section "[tv shows]"
Processing section "[Japanese Anime]"
Processing section "[software]"
Processing section "[temp movies]"
Processing section "[recently downloaded]"
Processing section "[dropbox]"
Processing section "[New Music]"
Processing section "[Music]"
Processing section "[itunes]"
Processing section "[drives]"
Processing section "[www]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
[global]
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
	printcap name = cups
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = No
	create mask = 0777
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[movies]
	comment = Movies
	path = /media/Movies/Movies/
	write list = robert
	guest ok = Yes

[tv shows]
	comment = tv shows
	path = /media/Tv Shows/tvshows
	write list = robert
	guest ok = Yes

[Japanese Anime]
	comment = Anime Tv Shows
	path = /media/Tv Shows/anime
	write list = robert
	guest ok = Yes

[software]
	comment = software
	path = /media/Elements/software
	write list = robert
	guest ok = Yes

[temp movies]
	comment = not really ready for the collection, view if you can
	path = /media/Movies/temp movies
	write list = robert
	guest ok = Yes

[recently downloaded]
	comment = recently downloaded
	path = /media/5/recently downloaded
	write list = robert
	guest ok = Yes

[dropbox]
	comment = your change to contribute - put stuff here!
	path = /media/5/dropbox
	read only = No
	create mask = 0777
	guest ok = Yes

[New Music]
	comment = Music
	path = /media/Elements/music
	write list = robert
	guest ok = Yes
[Music]
	comment = Music
	path = /media/5/music
	write list = robert
	guest ok = Yes

[drives]
	path = /media/
	write list = robert, candace
	browseable = No
	browsable = No

[www]
	path = /www
	write list = robert
	guest ok = Yes


SIDE NOTE: share drives is not meant to be visable, nor writeable 

LOCATION 2:

SMB.conf
> 
#======================= Global Settings =======================
[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog only = yes
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user


########## Printing ##########
# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############
;   include = /home/samba/etc/smb.conf.%m
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
   usershare allow guests = yes

#======================= Share Definitions =======================
;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[downloads]
   comment = finished downloads
   path = /media/Elements/complete/
   browseable = yes
   read only = yes
   guest ok = yes

;   write list = root, @lpadmin


testparm:
> 
robert@EEEPC:/media$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[downloads]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	syslog only = Yes
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

[downloads]
	comment = finished downloads
	path = /media/Elements/complete/
	guest ok = Yes




any and all help will be awesome
any particular questions let me know

---

### Post by sikander3786 on 2010-09-26
Do you want guest access to all of your shares?

Also make sure before proceeding that you can ping one box from the other on the network. All your PCs are in the same workgroup.

The network is a mix of Windows and Linux computers?

---

### Post by Morbius1 on 2010-09-26
Output of the following command please:
```
 ls -al /media
```

---

### Post by robsablah on 2010-09-26
location 2:

robert@EEEPC:~$ ls -al /media
total 24
drwxr-xr-x  5 root   root   4096 2010-09-18 21:04 .
drwxr-xr-x 22 root   root   4096 2010-08-09 21:27 ..
drwx------  2 root   root   4096 2010-09-18 19:56 disk
drwx------  1 robert robert 4096 2010-09-18 19:53 Elements
-rw-r--r--  1 root   root    141 2010-09-18 19:57 .hal-mtab
-rw-------  1 root   root      0 2010-09-18 19:56 .hal-mtab-lock
drwx------  2 root   root   4096 2010-09-18 19:57 PE

will get location 1 later

---

### Post by luvshines on 2010-09-27
The path that you have shared are of the type:

[Japanese Anime]
path = /media/Tv Shows/anime

[software]
path = /media/Elements/software

[temp movies]
path = /media/Movies/temp movies

[recently downloaded]
path = /media/5/recently downloaded

But most of /media directories are missing, viz - Tv Show, Movies, 5 etc

Also, the complete shared path should have read and execute permissions ie each of directory(telescopically) starting from /media

---

### Post by robsablah on 2010-09-27
> **luvshines said:**
> The path that you have shared are of the type:

[Japanese Anime]
path = /media/Tv Shows/anime

[software]
path = /media/Elements/software

[temp movies]
path = /media/Movies/temp movies

[recently downloaded]
path = /media/5/recently downloaded

But most of /media directories are missing, viz - Tv Show, Movies, 5 etc

Also, the complete shared path should have read and execute permissions ie each of directory(telescopically) starting from /media
you've quoted  location 1, above ls -al /media is for location 2

---

### Post by Morbius1 on 2010-09-27
Since you're only providing information on Location 2 let's focus on that:

/media/Elements is being mounted with this ownership / permissions:
>  drwx------  1 robert robert 4096 2010-09-18 19:53 ElementsYet your shares are defined this way:
> [downloads]
   comment = finished downloads
   path = /media/Elements/complete/
   browseable = yes
   read only = yes
   [COLOR=Blue]guest ok = yes[/COLOR]You told samba to allow guest access but linux file permissions will only allow robert to access the actual directory. Samba can match or take away permissions but cannot add permissions. Nothing can override linux file permissions. One way to work around this problem is to add the following line to the share definition of [downloads]:
```
force user = robert
```So that the share definition looks like this:
> [downloads]
    comment = finished downloads
    path = /media/Elements/complete/
    browseable = yes
    read only = yes
[COLOR=Blue]force user = robert[/COLOR]
    [COLOR=Black]guest ok = yes[/COLOR]Then restart samba:
```
sudo service smbd restart
```

---

### Post by robsablah on 2010-09-28
so that one works... flawless
what i don't get is this worked on jaunty without the force user
with the location 1 original smb conf file

trying location 1 now

robert@WATTSRV:~$ ls -al /media
total 60
drwxr-xr-x  7 root   root    4096 2010-09-28 17:25 .
drwxr-xr-x 23 root   root    4096 2010-09-24 20:13 ..
drwx------  1 robert robert  4096 2010-07-20 19:17 5
drwx------  1 robert robert 16384 2010-08-19 22:06 backup
drwx------  1 robert robert 20480 2010-09-26 14:03 Elements
drwx------  1 robert robert  8192 2010-06-13 13:43 Movies
drwx------  1 robert robert  4096 2010-07-19 19:48 Tv Shows

updated almost share to reflact force user
 - flawless....
thanks for letting me know how to get it to work

2nd round of business.............
i would only consider this a temp work around as this worked flawless on jaunty
is there any way to make it so i don't have to force user (im more the security nut type and will need it that way in future) :D

---

### Post by Morbius1 on 2010-09-28
> so that one works... flawless
what i don't get is this worked on jaunty without the force userWhen you inserted an external ntfs usb hard drive in Jaunty in would automount with owner = root and permissions set to 777. It was a good starting point to share across the network because by default the linux permissions were set to allow access by everyone.

Now when you insert the drive it mounts with owner = $USER and permissions set to 700. Only $USER can access the drive. 
>  is there any way to make it so i don't have to force user (im more the security nut type and will need it that way in future) :grin:     "force user" is a way to inherit the permissions of someone else for  that particular share. It does not give the remote user access to your  entire box.

Besides, you have control over access in Samba. Remember that access to a remote linux share requires both Linux file permissions and Samba authorization.

Let's say I have a share at /home/$USER/Documents and set it so permissions are set to 700. Only $USER has read / write access. If I set this up to allow guest access then I'm forced to use "force user" to allow the guest to have any kind of access ( Unless I want to change linux permissions on the directory ).

But with Samba I can "take away" permissions. For example:
```
[documents]
path = /home/$USER/Documents
read only = yes
valid users = jim
hosts allow = 192.168.0.100
force user = $USER
```"force user" will convert jim to $USER only after jim provides the required credentials and only if jim is accessing the share from one particular box located at 192.168.0.100 and even then I'm only giving jim read access.

---

### Post by robsablah on 2010-09-28
i guess i don't have much of a choice then

nawwww

thank you so much for your time ......

:popcorn:

---

### Post by quigi on 2012-03-21
> **sikander3786 said:**
> 
Also make sure before proceeding that you can ping one box from the other on the network. All your PCs are in the same workgroup.


Ping checks network connectivity.  What does that have to do with canonicalizing a path?

---

### Post by Iowan on 2012-03-21
Closed.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

