---
title: "Samba PDC, local profiles are getting copied to the server"
date: 2008-02-21
forum: Server Platforms
---

### Post by gweedo767 on 2008-02-21
I am working on setting up a Samba PDC.  I want server based authentication, but locally stored profiles (for speed reasons).  Right now for some reason the profiles are getting copied back to the users home dir every time they login or out.  Here is my smb.conf:

[global]
   workgroup = DFAZUSA
   netbios name = azusa-fileserv
   server string = %h server (Samba, Ubuntu)

   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = hosts wins bcast
   domain logons = yes
   preferred master = yes
   wins support = yes
   domain master = yes
   local master = yes
   os level = 254
   socket options = TCP_NODELAY

   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS

   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   login path =
   login home =


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
   log level = 2

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
   root preexec = /etc/samba/scripts/autopoweruser.sh %U %m
   admin users = Administrator
   valid users = %U
   read only = Yes
   guest ok = Yes
   browsable = Yes

[allusers]
  comment = All Users
  path = /home/samba/shares/allusers
  valid users = @users
  force user = samba
  force group = samba
  create mask = 0660
  directory mask = 0771
  writable = yes
  hide files = /Thumbs.db/


So, what am I missing?

---

### Post by lnx4me on 2008-02-21
I think that you should turn off roaming profiles on the windows systems.

---

