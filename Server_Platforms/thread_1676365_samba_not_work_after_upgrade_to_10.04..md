---
title: "samba not work after upgrade to 10.04."
date: 2011-01-27
forum: Server Platforms
---

### Post by whitebate on 2011-01-27
I have upgraded my ubuntu server  to 10.04 from 9.10.Everything seems well except samba.

I know that there are two daemons smbd and nmbd.I have use service ..status to see their status. Smbd is working while nmbd is not start.So I use "sudo start nmbd" to start.It give error"start: Job failed to start".And I can see the /var/log/samba/log.winbindd-idmap have record:

[COLOR="Red"][2011/01/27 16:08:20,  0] winbindd/idmap.c:589(idmap_alloc_init)         
  ERROR: Initialization failed for alloc backend, deferred!   [/COLOR] 

I can access samba use \\ip\share not \\netbios\share from windows clients.

how can I fix bug? 

below is my smb.conf file.

[global]
   workgroup = icreek
   server string = %h server (Samba, Ubuntu)
   wins support = yes 
   netbios name = server1
   dns proxy = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 10 
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = ldapsam:ldap://server1.icreek.cn
   ldap suffix = dc=icreek,dc=cn
   ldap user suffix = ou=people
   ldap group suffix = ou=groups
   ldap machine suffix = ou=computers
   ldap idmap suffix = ou=Idmap
   ldap admin dn = cn=admin,dc=icreek,dc=cn
   ldap ssl = no
   ldap passwd sync = yes
   add machine script = sudo /usr/sbin/smbldap-useradd -t 0 -w "%u"
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = Never
   domain logons = yes
   logon drive = U:
   logon home = \\%N\%U
   logon script = logon.cmd
   load printers = no
   domain master = yes
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0775
   directory mask = 0775
   valid users = %S
[netlogon]
   comment = Network Logon Service
   path = /usr/share/samba/netlogon
   guest ok = no
   read only = yes
   share modes = no

---

