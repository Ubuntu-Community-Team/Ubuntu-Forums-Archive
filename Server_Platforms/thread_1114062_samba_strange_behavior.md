---
title: "samba strange behavior"
date: 2009-04-02
forum: Server Platforms
---

### Post by ulver on 2009-04-02
I have one strange problem with samba and on question.
I have setup to share home dirs, but when I login with and user i see two directories, the "homes" directory and the "username" directory which point to /home/username. Ok now, does anyone know why are the two of those?
And can the Printers and Faxes be removed? 
This is my smb.conf:

```

[global]
   workgroup = softing
   server string = softing shared
   dns proxy = no
   security = user
   encrypt passwords = true
   smb passwd file = /etc/samba/smbpasswd
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes

[homes]
  comment = Home Directories
  browseable = yes
  writable = yes
  create mask = 0700
  directory mask = 0700
  valid users = %S


```

---

### Post by Sam Lars on 2009-04-03
The Homes sharing may share the whole /home directory as well...
And I would guess that you can remove the Printers section.

---

