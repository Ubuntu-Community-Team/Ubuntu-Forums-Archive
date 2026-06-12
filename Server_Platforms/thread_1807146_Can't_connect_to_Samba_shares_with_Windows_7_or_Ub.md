---
title: "Can't connect to Samba shares with Windows 7 or Ubuntu"
date: 2011-07-18
forum: Server Platforms
---

### Post by freshtealeaf on 2011-07-18
Hi

I'm trying to use Windows 7 to connect to a Samba server (running Ubuntu 11.04). 

Server is named Mars. Below is my Samba configuration file. I can ping the server, and connect to it via RDP and ssh, so i know its not a network connectivity issue. What else could it be? 

```
#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	server string = %h server (Samba, Ubuntu)
	winbind enum users = no
	force group = nobody
	force user = nobody
	winbind enum groups = no
	os level = 20
	username map = /etc/samba/user.map
	interfaces = lo eth0
	encrypt passwords = yes
	winbind trusted domains only = yes
	bind interfaces only = yes
	


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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
	writeable = yes
	guest ok = yes
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
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

;[Share name]
;writable = yes
;path = /path/to/directory
;public = yes
;guest ok = yes
;guest only = yes
;guest account = nobody
;browsable = yes

[Aeonaeon3]
	path = /media/Aeonaeon3
	writeable = No
	browseable = yes
	valid users = aries
   create mask = 0755
   directory mask = 0755

[MEDIA]
	path = /media/Aeonaeon3/MEDIA
	writeable = No
	browseable = yes
	guest ok = yes
  create mask = 0755
   directory mask = 0755

[IsaacP1]
	path = /media/C60C80570C804481
	writeable = yes
	force user = nobody
	force group = nobody
	browseable = yes
	guest ok = yes
  create mask = 0755
   directory mask = 0755

[Aeonaeon2 233GB]
	path = /media/Aeonaeon2 233GB
	writeable = yes
	browseable = yes
	guest ok = yes
	force user = nobody
	force group = nobody
  create mask = 0755
   directory mask = 0755

[Vault1]
	path = /media/6d170594-4493-4394-a27f-cbd622678906/Vault1
	writeable = yes
	browseable = yes
  create mask = 0755
   directory mask = 0755
	guest ok = yes

[Vault2]
	path = /media/2b2dbfe6-8a64-41d0-81b9-e1e3ebf51220/Vault2
	writeable = yes
	browseable = yes
  create mask = 0755
   directory mask = 0755
	guest ok = yes

[IsaacP2]
	comment = p2
	path = /media/E4100FD2100FAB1E
	writeable = yes
	browseable = yes
	guest ok = yes
  create mask = 0755
   directory mask = 0755

```

---

### Post by donniezazen on 2011-07-18
Check your firewall.

---

### Post by freshtealeaf on 2011-07-19
Okay, I can connect now but it keeps asking me for a user name and password. When I enter in any of the user names/passwords configured for Samba they don't work. 

Any ideas?

---

### Post by akand074 on 2011-07-19
> **freshtealeaf said:**
> Okay, I can connect now but it keeps asking me for a user name and password. When I enter in any of the user names/passwords configured for Samba they don't work. 

Any ideas?
 
Samba is for Windows only. (i.e you can see Ubuntu share folders in Windows). The username/password is that of your Ubuntu account that you used to make the share folders. If you only have one account it's your name and your root password.

---

### Post by freshtealeaf on 2011-07-19
I enter it in and still no avail. I've tried all the users accounts on the system. Could it be a configuration issue?

---

### Post by Entilza on 2011-07-20
Did you add the unix user to samba user database?

Also make sure the password matches the windows username password.

---

### Post by Morbius1 on 2011-07-20
Well, here's how I see things.

It appears that all of your shares are guest shares that do not require usernames and passwords to access. But you do have at least two complications:

[1] You have no way to convert the remote anonymous user to the guest account because you have a line missing from your smb.conf:
```
map to guest = Bad User
```You might want to add that to the global section and restart samba.
[COLOR=Blue]*EDIT: In fact without that line samba defaults to "map to guest = Never" which is self explanatory.*[/COLOR]

[2] All of your shares are /media/this and /media/that.

Do you have permissions set up on the target directories to allow guest write access? As in:
```
sudo chmod 777 /media/6d170594-4493-4394-a27f-cbd622678906/Vault1
```This one is an NTFS partition so you can't do a chmod on that one:
 > [IsaacP1]
    path = /media/C60C80570C804481You will have to modify your fstab entry for this partition and include a umask=0000 to achieve the same result.

---

### Post by freshtealeaf on 2011-07-20
Ah okay, thank you. Any ideas on how I can edit/update fstab for that share?

---

### Post by Morbius1 on 2011-07-20
[1] Verify that that is the correct uuid number ( C60C80570C804481 ) for the partition by running the following command:
```
sudo blkid -c /dev/null
```[2] Unmount the partition if it's mounted:
```
sudo umount /media/C60C80570C804481
```[3] Create a mount point for the partition. Since I don't know what's on that partition I will call it "Data" for this example:
```
sudo mkdir /media/Data
```[4] Then add the following line to the end of fstab:
```
UUID=C60C80570C804481 /media/Data ntfs defaults,nls=utf8,umask=0000 0 0
```[5] Then run the following command to test for errors and mount the new partition:
```
sudo mount -a
```

---

