---
title: "smbd.  Failed to connect to socket"
date: 2010-11-21
forum: Server Platforms
---

### Post by espenbo on 2010-11-21
Hello

I have a new install of Ubuntu 10.04.1 LTS server.
But I get errormessages trying to start samba.

caesar@klem:/etc/samba$ restart smbd
restart: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory


I have tride to remove an install samba. And deleted smb.conf. And startet with the original.

smb.conf:
workgroup = Easyways
server string = %h server (Samba, Ubuntu)
log file = /var/log/samba/log.%m
 max log size = 1000
 panic action = /usr/share/samba/panic-action %d
 security = user
 encrypt passwords = true
passdb backend = tdbsam
 obey pam restrictions = yes
 unix password sync = yes
 passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
 map to guest = bad user
usershare allow guests = yes
[homes]
   comment = Home Directories
   browseable = no


Can sombody please give me some help on have to correct the problem.

Espen

---

### Post by SeijiSensei on 2010-11-21
> **espenbo said:**
> 
caesar@klem:/etc/samba$ restart smbd

You must use sudo like this, "sudo restart smbd".  Ordinary users can't start or stop services like smbd for security reasons.  Only the root (administrative) user can do so.

---

### Post by espenbo on 2010-11-21
Thanks. Forgot to 'sudo'.... ;)

Espen

---

