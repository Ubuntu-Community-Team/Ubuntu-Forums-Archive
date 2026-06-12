---
title: "Samba question concerning shares"
date: 2006-06-22
forum: Server Platforms
---

### Post by vanilla_thunder on 2006-06-22
Whats up guys, this forum has helped me out tons before.  I havent been able to find an answer to this particular question though.  Im running an ubuntu box with Samba installed. Our clients are running XP. Were sharing a folder out to all users, and security is set to share.  However, I want to create another share that allows access to only 3 specific users.  Ive tried using the valid users parameter but for some reason windows forces the clients to log in as guest.  Any suggestions would greatly help.  Heres my smb.conf as of now.  I only have the one share set up right now.

======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no


   syslog = 0


   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

  security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

;   unix password sync = no

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# 'passwd program'. The default is 'no'.
;   pam password change = no

;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups


# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############


;   include = /home/samba/etc/smb.conf.%m


#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY


;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


;   domain master = auto


;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = no


   writable = no


   create mask = 0700


   directory mask = 0700


;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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

;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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

[public]
comment = Public Folder
path = /OLE/SHARE
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

---

### Post by Iowan on 2006-06-23
Not sure I can help - other than to bump...
I'm a bit confused by what you mean:> windows forces the clients to log in as guest
Windows opens a login dialog box with **guest** as the only option? The three specific users will need to have Unix and Samba accounts on the server... AND be logged on as such.  Do the accounts exist?

---

### Post by vanilla_thunder on 2006-06-23
Yes, the users have a unix and samba account.  But when they attempt to access the share with the valid user = parameter.....Windows comes up with a password dialog box with guest as the user and no option to change it

---

### Post by Iowan on 2006-06-26
I don't have an answer - only questions.  I wonder if the **security=share** is affecting the logins?  I wonder if the **security=** statements could be moved into the shares, with **security=user** inside the controlled share.

---

### Post by LordHunter317 on 2006-06-26
Yes, ***don't use security=share*** ever.

---

