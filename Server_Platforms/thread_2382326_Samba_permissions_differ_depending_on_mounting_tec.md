---
title: "Samba permissions differ depending on mounting technique"
date: 2018-01-11
forum: Server Platforms
---

### Post by jfaberna on 2018-01-11
I have a Samba file server built with Ubuntu server 16.04.  I tried to configure it so all my PCs could edit any file regardless of Linux, PC, or Mac.  On Ubuntu Desktop, if I mount using the Files GUI -> Connect to Server-> Server Address-> smb://192.168.0.250/ I get access to all my Samba files and can read and write. In Files GUI Owner, Group and Permissions are all listed as unknown. This works, but the mount is not automated and I'm not sure how to use the command line if I want access to the Samba Server's files.

If I edit /etc/fstab and put in the line:

 //192.168.0.250/public /media/media cifs password=passwd123,user=jim 0 0

the system mounts /media/media at boot time, but all the permissions are listed as root:root and 755.

On the Samba file server I use smbpasswd to create the samba user=jim with password= passwd123.  'jim' is also a Linux user and is a member of Group 'users'.  My smb.conf is at the bottom.

I'd like to fix the fstab statement so I can have the same permissions as using the Files GUI.

Thoughts?

[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
security = user
map to guest = bad user
dns proxy = no

#============================ Share Definitions ==============================

[Anonymous]
path = /mnt/md0/samba/anonymous
browsable =yes
writable = yes
guest ok = yes
read only = no
force group = users
force user = jim
create mask = 0664
force directory mode = 2775
[public]
path = /mnt/md1/samba/public
read only = no
force group = users
force user = jim
create mask = 0664
force directory mode = 2775
guest ok = yes
writable = yes
browsable = yes

---

### Post by wildmanne39 on 2018-01-11
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by Morbius1 on 2018-01-12
> //192.168.0.250/public /media/media cifs password=passwd123,user=jim 0 0

the system mounts /media/media at boot time, but all the permissions are listed as root:root and 755.

"user" and "password" represent the credentials that the server requires for authentication. That line as it stands will mount with owner = root because root is the one mounting it and you didn't specify any other owner. If your client user is "jim" make him the owner of the mounted share:

> //192.168.0.250/public /media/media cifs password=passwd123,user=jim[COLOR=#0000cd]**,uid=jim**[/COLOR] 0 0

[COLOR=#0000cd]*It's sorta kinda like mounting an NTFS partition in fstab where unless you specify differently it will mount with root as owner of the mounted partition. *[/COLOR]

---

### Post by jfaberna on 2018-01-12
That did it.

Thanks for the explanation.

Jim A

---

