---
title: "Xp Not Joining Samba Domain"
date: 2007-06-09
forum: Server Platforms
---

### Post by sheffrem on 2007-06-09
Hi guys.
i just got a tutorial on [www.howtoforge.com/net](www.howtoforge.com/net)
But the thing isn't working.
i did all they said but yet cant join windows xp to it.
it gives me and error like this " cant find domain or DNS whatever" which i dont understand.
here is my configurations.



[global]
   workgroup = Engineering.net
   netbios name = LinuxPrintServer
   server string = %h server (Domain Controller,Print Server)
   
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
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\LinuxPrintServer\profile\%U


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


[allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes


PLEASE HELP ME. UBUNTU 7.04

---

### Post by obimeister on 2007-06-09
You probably need to configure WINS service in samba and then configure WINS server address to your dhcp server or to your XP machine. These lines in samba config file should make it also act as a WINS server. 

wins support = yes
name resolve order = wins lmhosts host bcast
dns proxy = no

---

### Post by sheffrem on 2007-06-11
I did all that but still giving me the same message.
Pls guys help me,

---

