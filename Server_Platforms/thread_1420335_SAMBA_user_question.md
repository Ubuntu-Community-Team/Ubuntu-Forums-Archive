---
title: "SAMBA user question"
date: 2010-03-02
forum: Server Platforms
---

### Post by jwkite on 2010-03-02
I am not a frequent poster on these forums because I can usually find someone else who has had my problem and had it resolved, but I've had a hard time finding this problem described elsewhere.  Thanks in advance for your help.

I recently built a new Karmic Server Edition to replace my older home server that was running Hardy Desktop.  I want to share my music directory as a read/write share to both my Karmic desktop and a Vista machine.  I have created shares several times using Samba and never seen this issue.  I am using Webmin to manage the server and create the share.

The admin username (first user created, etc.) on the server is A, and his userID is 1000.  The user who owns the share and all of the files on the server is B, and his userID is 1001.  The share is named music and is intended to be read/writable to all known users.

The username that I have used to log in to the Karmic desktop is C (again, first user created), and his userID is 1000.

I have mounted the share on the desktop at /mount/music with the following entry in fstab:

```
//ipaddress/music/ /mnt/music    smbfs   rw,users,auto,credentials=/home/C/.smbcredentials 0 0
```

The .smbcredentials file looks like this:
```
username=B
password=password
```
When I cd to /mnt/music and ls -l I find that the user is neither B nor C but instead is D.  There is a user D on the desktop with userID 1001; no user with that name exists on the server.

This results in some strange behavior.  For example, from Nautilis I can create a directory and rename it, but I cannot save a file in that newly created directory from gedit.  From the command line entering:
```
touch test
```
I receive the following response:
```
touch: setting times of `test': Permission denied
```
The file test is created.  I can edit the file with vi, but I cannot save the changes.  My presumption is that this is due to the file being created with 755 permissions, despite the fact that the share is defined to allow create mode and directory mode to be 777.

I am aware of the security implications of this configuration, but I will address those once I fix this issue.

Does anyone have any ideas?  Thanks again for any help.

Nearly complete Samba config file from the server with unnecessary comments removed:


```
#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	username map = /etc/samba/user.map
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = BEARMOOSE
	os level = 20
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###
#   wins support = no
;   wins server = w.x.y.z
;   name resolve order = lmhosts host wins bcast

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes

#### Debugging/Accounting ####
#   syslog only = no

####### Authentication #######
#   security = user

########## Domains ###########
;   domain logons = yes
;   logon path = \\%N\profiles\%U
#   logon path = \\%N\%U\profile
;   logon drive = H:
#   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########
## all removed - irrelevant

############ Misc ############
;   include = /home/samba/etc/smb.conf.%m
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
#   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100

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
;   write list = root, @lpadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

[music]
	guest account = B
	writeable = yes
	path = /mnt/drive1/music
	force group = users
	force user = B
	create mode = 777
	directory mode = 777
```

---

### Post by suseendran.rengabashyam on 2010-03-03
Hi,

A similar thread
[http://ubuntuforums.org/showthread.php?t=1409720](http://ubuntuforums.org/showthread.php?t=1409720)

Hope this helps.

---

### Post by jwkite on 2010-03-03
That's exactly what I needed.  Thank you very much for your help!

---

