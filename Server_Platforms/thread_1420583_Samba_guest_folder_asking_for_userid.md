---
title: "Samba guest folder asking for userid ??"
date: 2010-03-03
forum: Server Platforms
---

### Post by ggee on 2010-03-03
I had setup a guest folder in Samba that did not require any authentication, but some time recently, it started asking for credentials.  Fortunately, I can just type in any user with no password and it still lets me in, but why is it asking for password now?

Thanks,
Greg

Ubuntu 9.10

smb.cfg
========
```
[global]
   guest ok = yes
   workgroup = WORK
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
   wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[share]
  path = /share
  available = yes
  browsable = yes
  public = yes
  writable = no
  guest ok = yes
[Downloads]
  path = /home/ggee/Downloads
  writable = yes
  public=no
  valid users = ggee
  available = yes
  browsable = yes
  guest ok = no
```

---

### Post by Letrazzrot on 2010-03-03
Are you trying to connect from a Windows computer, and is the Windows user name the same as the linux (server) user name?  If so, you may want to read towards the bottom of the page here:
[http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/](http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/)

---

