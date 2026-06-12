---
title: "Samba write permissions"
date: 2019-10-15
forum: Server Platforms
---

### Post by Andrew_Benjamin on 2019-10-15
I have a file server in my basement which has a share called "PhoneRecordings".  This shared drive is supposed to hold recordings from my asterisk machine (phone system). It's legal in NJ to record calls.

in my smb.conf file, I have the following:

[PhoneRecordings]
path = "/media/RAID/Phone System Calls - Backup"
available = yes
valid users = root server
force user = root
encrypt passwords = true
browseable = yes
security = user
guest ok = no
read only = no
create mask = 0755
writable = yes
write list = server root

The directory, subdirectories and files are all owned by root
drwxr-xr-x  5 root root 4096 Aug 17 17:23 2014

for example.

On the PBX machine, I have an entry in fstab:


//192.168.40.28/PhoneRecordings /mnt/Phone cifs username=server,password=PASSWORD,iocharset=utf8,sec=ntlm  0  0


The drive shares correctly, but when a call comes in, Asterisk/PBX machine indicates a permissions failure:

```
[2019-10-15 19:03:58] WARNING[5259][C-0000000a]: file.c:1229 ast_writefile: Unable to open file /mnt/Phone/2019/10/15/out-9177230665-1000-20191015-190358-1571180638.17.wav: Permission denied
```


Can anyone point out what I'm doing wrong?  I really don't care that the machines are granting write permissions to a super user - the machines are behind 3 firewalls and if they get hacked I have bigger problems.

Thanks.


Andrew

---

### Post by wildmanne39 on 2019-10-15
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

