---
title: "Help me setup file server"
date: 2008-07-25
forum: Server Platforms
---

### Post by jmedina on 2008-07-25
I just started working on getting my file server up and running today and it has been a diaster. I installed Xubuntu,Samba. I am trying to access the server via a mac. When I connect it simply times out. When I setup samba I put: and have no luck. When I installed Xubuntu I specified my full name and my username, so I think the problem may be with the workgroup and netbios name. Or, I think it maybe because I am using a mac. Should I try a PC? Thanks in advance for your help.

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "Name"
netbios name = "Server name"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700

---

### Post by shouston on 2008-07-25
If you did not setup netatalk you will need to tell your mac to connect via samaba.  Do this by putting smb:// before your ip or uname.

i.e.  smb://192.168.1.1

---

### Post by jmedina on 2008-07-25
Thank you for your quick reply! I am getting closer, but the mac brings up the SMB/CIFS Filesystem Authentication and says:

Workgroup/Domain
MSHOME

Username
"My Name"

Password

I typed in my password and it says it could not connect to the server because the name or password is not correct. I tried changing my password via the terminal and had no luck.

---

### Post by jmedina on 2008-07-25
I give up with the project for now. I will probably try and fix it within the next few weeks. I am closer than I was which feels good.

---

### Post by Uluen on 2008-07-25
Did you remember restarting Samba after you made config changes?

Does you Samba user exist?

Change password:
```
# smbpasswd username
```

Add user:
```
# smbpasswd -a username
```

---

### Post by jmedina on 2008-07-25
> **Uluen said:**
> Did you remember restarting Samba after you made config changes?

Does you Samba user exist?

Change password:
```
# smbpasswd username
```

Add user:
```
# smbpasswd -a username
```

I don't think I did the first part of that code. Maybe that is the problem. Should I have file sharing on my mac on? I tried a machine running Windows XP and that didn't even give me the login screen. Also the mac gave me a different error when I thought I had the information correct. I think it was error #-50 I will try to do that next week.

---

### Post by Stele on 2008-07-25
Remember to add your users to Samba... Tka e alook at this: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add.2Fedit.2Fdelete_network_users)

---

### Post by jmedina on 2008-07-25
Thanks for the link! I will try it within the next few weeks.

---

