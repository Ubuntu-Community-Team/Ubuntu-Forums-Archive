---
title: "samba share with windows access denied Ubuntu 10.04"
date: 2010-09-17
forum: Security
---

### Post by isaacjun16 on 2010-09-17
Hi, so I have 2 problem with my shares in Ubuntu 10.04 with windows XP.

Problem # 1

Every time I restart my Ubuntu system, the printers I have shared are no visible, so what I have to do every time after I log in, I have to run this command in order to be able to see my printers shared from my windows machine.

sudo service smbd restart

Problem # 2

When I tried to share a folder that is on my home directory, (Desktop or Documents) I get the message access denied from my windows machine. The estrange think is that I have two share and the second one I'm using I have access from the same windows machine.

share 1: /home/user/Documents   drwxrwxrwx  2 user user   ext3   No access
share 2: /media/backups/upload  drwxrwxrwx 1 root plugdev   ntfs  Complete access

Please help this is driving me crazy. ](*,)

testparm -s

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Unknown parameter encountered: "wide symlinks"
Ignoring unknown parameter "wide symlinks"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = usuario
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	unix extensions = No
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes

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
	read only = No

---

### Post by CharlesA on 2010-09-17
I haven't worked with sharing printer via samba, so I'm not sure why that isn't working. smbd and nmbd should start automagically on boot.

Can you post What your share definitions look like, and place them in code tags?

---

### Post by isaacjun16 on 2010-09-17
Sorry I'm a bit noob at this. I'm not sure how to place them in code tags.

---

### Post by CharlesA on 2010-09-17
> **isaacjun16 said:**
> Sorry I'm a bit noob at this. I'm not sure how to place them in code tags.

Just add [code ] [/code ] around them. (minus the spaces)

---

### Post by isaacjun16 on 2010-09-17
```
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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
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

```

Sorry this are the only share definitions I have, on the smb.conf, I'm not sure if making the shares with nautilus has anything to do with it.

---

### Post by CharlesA on 2010-09-17
I don't see any definition for the share in yer home directory. That could be the reason you are getting an error.

Try running this:

```
smbclient -L `hostname`
```

Yes those are backticks (the tilde key)

---

### Post by isaacjun16 on 2010-09-17
I get this:

```
smbclient -L `hostname`
Unknown parameter encountered: "wide symlinks"
Ignoring unknown parameter "wide symlinks"
Enter user's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED
```

I [read some where]("http://ubuntuforums.org/showthread.php?t=1502265#8") that if I do the shares with nautilus the share definitions are in:

```
/var/lib/samba/usershares
```

I check in there and I found 2 files:

```
-rw-r--r-- 1 user user 81 2010-09-17 00:58 documents
-rw-r--r-- 1 user user 82 2010-09-16 21:43 upload
```

the share definition on them are:

```
#VERSION 2
path=/media/Backups/Upload
comment=
usershare_acl=S-1-1-0:F
guest_ok=y
```

```
#VERSION 2
path=/home/user/Documents
comment=
usershare_acl=S-1-1-0:F
guest_ok=y
```

---

### Post by CharlesA on 2010-09-17
Yeah, it sounds like those are Nautilus shares, but I don't know if that's the reason why you are getting those errors.

Try adding them to smb.conf. I don't think that they will be able to be copy/pasted.

---

### Post by isaacjun16 on 2010-09-17
that did the trick, with the shares, now I still have the problem with the printer, that I have to restart the service of samba in order to be able to see the printers from another windows computer.

BTW what do you think was the problem with the shares: Permission problem, Owner Problem, Samba Problem, Nautilus Problem. I'm curious about it :guitar:

---

### Post by CharlesA on 2010-09-17
I think it was the way nautilus does sharing vs samba, but I'm not sure.

As for having to restart the smbd service, you could just add a line in /etc/rc.local that says:

```
service smbd restart
```

---

