---
title: "Connect to SAMBA server without /etc/nsswitch.conf modify?"
date: 2010-01-26
forum: Server Platforms
---

### Post by frenchn00b on 2010-01-26
Connect to SAMBA server without modification? 

I would like that the workstation can be connected with client modification of smb.conf
cat /etc/samba/smb.conf
> [global]
   guest account = nobody
   invalid users = root
   encrypt passwords = yes
   security = ads
   password server = 192.168.10.10  #samba server
   workgroup = WORKGROUP
   server string = %h server (Samba %v)
   preserve case = yes
   short preserve case = yes
   unix password sync = yes

[homes]
  comment = Home Directories
  read only = No
  create mask = 0700
  directory mask = 0700
  browseable = no





[B]Normally this can be done with adding : 
winbind next to compaq into 

Without modifying the /etc/nsswitch.conf is it possible?[/B]

thanks if any ideas or help

---

