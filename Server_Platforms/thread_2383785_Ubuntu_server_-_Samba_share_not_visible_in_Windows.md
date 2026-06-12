---
title: "Ubuntu server - Samba share not visible in Windows 10 as computer"
date: 2018-01-29
forum: Server Platforms
---

### Post by stanekpa on 2018-01-29
Hello,

I have set up SMB share on ubuntu server. When I run Explorer in Windows 10 and go to \\servername, I see shared folders and can acces to files, this is ok.
When I run Explorer and go to "Network", I cannot see my server as "Computer". Windows 10 client is in group named "WORKGROUP".

My smb config is:
```

[global]
workgroup = WORKGROUP
netbios name = quadrax
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000


name resolve order = bcast host lmhosts wins


security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
map to guest = bad user


[share]
path = /mnt/md1/ServerData/Videa
browsable = yes
guest ok = yes
read only = no
create mask = 0777
directory mask = 0777

```

smbtree output:
```

WORKGROUP
        \\QUADRAX                       quadrax server (Samba, Ubuntu)
                \\QUADRAX\IPC$                  IPC Service (quadrax server (Samba, Ubuntu))
                \\QUADRAX\share
        \\HTPC-OBYVAK                   LibreELEC
        \\BRN001BA9B2406D

```

Did I missed something?

Thank You.

---

