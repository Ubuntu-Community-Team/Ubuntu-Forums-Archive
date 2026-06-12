---
title: "setting up samba pdc"
date: 2009-04-02
forum: Server Platforms
---

### Post by skip.qiu on 2009-04-02
Dear all , 
     I'm sorry  to  trouble you ,  but I have no idea .  I can open the folder (tmp) that samba shares  on linux system  , but I can not open it on windows system .  Then I can not join in the domain yet .it appears "can't find the user-name" .  my smb.conf is like this :
[global]
   workgroup = skip
   server string = skip's samba-servera
   netbios name = skip
#   local master = yes
#   os level = 33
#   prefered master = yes
#   domain master = yes
   dns proxy = no
   name resolve order = lmhosts host wins bcast
   interfaces = eth0
   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog only = no
   syslog = 0
#   panic action = /usr/share/samba/panic-action %d
   security = suer
   username map = /etc/samba/smbusers
   encrypt passwords = true
   smb passwd file = /etc/samba/smbpasswd
# what's the difference between tdbsam and smbpasswd
 #   passdb backend = tdbsam
#   obey pam restrictions = yes   what's mean ? adding this there is a problem
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

   domain logons = yes
   logon path = \\%N\%U\profile
   logon drive = S:
   logon home = \\%N\%U
   logon script = logon.cmd
   load printers = yes
   printing = cups
   printcap name = cups
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
#   template shell = /bin/bash
#   enable privileges = yes
#   nt acl support = yes
#   hide dot files = yes
#   usershare allow guests = yes
   add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u

[homes]
   comment = Home Directories
   browseable = no
#   writable = yes
   read only = no
   create mask = 0700
   directory mask = 0700
#   create mode = 0644
#   directory mode = 0775
#   create mask = 0711
#   directory  = 0711
   valid users = %S
#   map hidden = yes
#   map system = yes
#   map read only = permissions
   hide files = /RECYCLER/
[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   read only = yes
#   browseable = no
   share modes = no
#   write list = skip
#   create mask = 0777
#   directory mask = 0777
#   map hidden = yes
#   map system = yes
#   map read only = permissions
[tmp]
   comment = tmp samba
   path = /var/samba/
#   guest ok = yes
   browseable = yes
   force group = "Domain Users"
   writeable = yes
#   valid users =  skip
#   public = yes
 create mask = 0777
   directory mask = 0777
   force create mode = 0666

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
[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /cdrom
   guest ok = yes
   preexec = /bin/mount /cdrom
   postexec = /bin/umount /cdrom

Anybody can help me ?  Thank you very much !
Best Regards
Skip

---

