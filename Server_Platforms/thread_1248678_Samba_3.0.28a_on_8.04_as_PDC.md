---
title: "Samba 3.0.28a on 8.04 as PDC"
date: 2009-08-24
forum: Server Platforms
---

### Post by coreykck on 2009-08-24
Hi guys,
I've a big problem on a hardy server with Samba shares.

1 server, 2 winXP clients, 2 users.
remote profiles activated.
After a server distro upgrade from 7.10 to 8.04, on client A both users can open Autocad file in a specific folder, and can save and save as in the same folder.
On client B, only one of the two users can do things reported; with other account I get error in writing over dwl (temporary file created from Autocad) and file is saved in savNNN.tmp.
With the same accont on client B, when I try to 'save as' a word file and choose a file name that doesn't exist, I get 'file *file_name* exists. Overwrite?'.
I think that error is related to file locking, but I've no more ideas.

Any suggestions?

Tnx a lot
Corrado

smb.conf
```

[global]

   workgroup = DOMAIN
   netbios name = FSRV
   server string = %h server (Samba, Ubuntu)

   wins support = yes 

   dns proxy = no
   name resolve order = wins bcast hosts
   log file = /var/log/samba/log.%m
   log level = 1 
   max log size = 1000
;   syslog only = no

   panic action = /usr/share/samba/panic-action %d
   security = user
   username map = /etc/samba/smbusers
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes 
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   passwd chat debug = yes


   domain logons = yes
   preferred master = yes
   logon path = \\%N\profiles\%U

   logon drive = W:
   logon home = \\%N\%U

  logon script = logon.cmd
   profile acls = yes
   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usernod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u

   load printers = yes
   printing = cups
   printcap name = cups
   socket options = TCP_NODELAY

   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash

 hide dot files = yes
 lock directory = /home/samba/locks
[homes]
   comment = Home Directories
   read only = no
   valid users = %S
   writable = yes 
[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   writable = no
   share modes = no
   read only = no
   admin users = Administrator
   valid users = %U

[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   valid users =%U
   writable = yes
   browseable = no
   create mask = 0600
   directory mask = 0700

[printers]
   comment = All Printers
;   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
   use client driver = yes

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

   write list = root, @smbadmin, @ntadmin


[work]
    wide links = no
    delete readonly = yes
    writable = yes
    path = /home/samba/files/work
    force directory mode = 0774
    force group = users
    veto oplock files = /*.tmp/*.dwl/
    force create mode = 0664
    comment = Files lavori  
    follow symlinks = no
    valid users = @users
    create mode = 0664
    directory mode = 0774

[inst]
  comment = Files installazione 
  path = /home/samba/files/inst
  follow symlinks = no
  valid users = @users
  force group = users
  create mask = 0664
  force create mode = 0664
  directory mask = 0774
  force directory mode = 0774
  locking = no
  writable = yes


```

---

### Post by coreykck on 2009-08-26
Ideas? I'm gonna cry :)

---

### Post by coreykck on 2009-09-04
Problem solved with upgrade to Ubuntu 8.10.

---

