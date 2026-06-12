---
title: "Simple Samba config"
date: 2005-09-10
forum: Server Platforms
---

### Post by TopDog on 2005-09-10
I used to share my USB Drive from a Ubuntu workstation at home, but now I've installed a low-end computer with Ubuntu server install. I've only installed it, installed samba, smbf, apache and some other services.

I have not configured the NIC espesially. Apache for example works fine.

I'm trying to configure Samba to share files with no security (no authentication) for my two users. I don't need to share print or cdrom or homes, just my mounted USB drive.

Samba is running, I can ping my server, but my girlfriends Windows laptop says it cannot fint my server when I run the command \\ipadress\sharename !?

Anyone got a clue? Here is my smb.conf:

```
#======================= Global Settings =======================

[global]
   workgroup = GAUTEWEB
   netbios name = server
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = share
   encrypt passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
;   pam password change = no


########## Printing ##########

;   load printers = yes

;   printing = bsd
;   printcap name = /etc/printcap

;   printing = cups
;   printcap name = cups

;   printer admin = @ntadmin


######## File sharing ########

;   preserve case = yes
;   short preserve case = yes

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

   socket options = TCP_NODELAY

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

;   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
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

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[veronica]
 comment = Veronicas mappe
 path = /media/storage/Veronica
 public = yes
 browsable = yes
 writable = yes
 create mask = 0777
 directory mask = 0777
 force user = nobody
 force group = nogroup
 guest ok = yes

``` 

Also how much can I remove? I would like it to be as small and simple as possible. I basicly just want to share the [veronica] part with no authentication...

Thanks for any help!

---

### Post by TopDog on 2005-09-11
If anybody is interested, the solution was as follows:

```

[global]
workgroup = GAUTEWEB
netbios name = SMB
server string = SAMBA server
security = share
local master = yes
os level = 35

[veronica]
comment = Veronicas mappe
path = /media/storage/Veronica
public = yes
browsable = yes
writable = yes
guest ok = yes
``` 

Thanks to XOR at [www.linuxcult.com](www.linuxcult.com) for all help  :)

---

