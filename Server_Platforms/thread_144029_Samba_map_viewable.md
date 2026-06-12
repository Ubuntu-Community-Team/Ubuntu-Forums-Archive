---
title: "Samba: map viewable"
date: 2006-03-13
forum: Server Platforms
---

### Post by maxdevis on 2006-03-13
i have 2 users that needs to access some maps
user1 needs acces to map1
user2 needs acces to map1 & map2

i don't want that user 1 sees map2

somebody?

---

### Post by Koybe on 2006-03-13
Use "valid users" directive in the map configuration of your /etc/samba/smb.conf

```
[map1]
valid users = user1 user2
...

[map2]
valid users = user2
...
```

---

### Post by maxdevis on 2006-03-13
thanks!
but that makes only that map inaccessable for user1.
i want that user1 cant see map2.

---

### Post by maxdevis on 2006-03-13
[QUOTE=smb]
[global]
   workgroup = BOEMBAB
   netbios name = MICHIEL
   server string = %h server (Samba, Ubuntu)

   
   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS
   
   # Default logon
   logon drive = M:
   logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = no


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no

[books]
path = /home/michiel/books
available = yes
browseable = yes
hide unreadable = yes
public = no
valid users = michiel
create mask = 0660
directory mask = 0771
writable = yes
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd

[muziek]
path = /media/i/muziek
valid users = michiel johanne
available = yes
browseable = yes
public = yes
writable = no
[/QUOTE]

this is my smb
base on [this](http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4) tutorial

---

### Post by Iowan on 2006-03-13
There's the **browseable = ** option.  I haven't tried whether **map2$** hides the share.

---

### Post by derelict on 2006-03-13
[map1]
valid users = user1 user2
...

[map2]
valid users = user2
invalid users = user1

---

### Post by Iowan on 2006-03-13
Check the sample smb.conf.  There's a section on customizing configuration based on machine.  It may be possible to do something similar based on user.

---

### Post by Koybe on 2006-03-14
Or usr browseable = no for map2 ;-)

---

### Post by maxdevis on 2006-03-14
doesn't work for me

in ubuntu, i also need to fill in a lot of times the username and passwoord and some key? before i can access the network folder

---

