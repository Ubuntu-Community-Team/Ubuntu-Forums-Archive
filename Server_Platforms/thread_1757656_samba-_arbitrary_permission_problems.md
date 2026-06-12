---
title: "samba- arbitrary permission problems"
date: 2011-05-13
forum: Server Platforms
---

### Post by Maythe on 2011-05-13
Hey everyone, I'm back with another Samba question.  This one should be short and sweet though!

Basically, I have 2 share folders set up. Literally, the only difference between the 2 is their names, and yet I can only write to one of them.  (I have read access for both)  Here is my config:

 
#Global parameters
[global]
    server role = domain controller
    workgroup = SUPERGROUP
    realm = super.domain.com
    netbios name = SUPERSERVER
    setup directory = /usr/share/samba/setup
 
[netlogon]
    path = /var/lib/samba/sysvol/super.domain.com/scripts
    read only = No
 
[sysvol]
    path = /var/lib/samba/sysvol
    read only = No
 
[backupEx]
    path = /media/samba
    read only = no
 
[backupHd]
    path =  /media/samba
    read only = no
 
 
 
Some things you should know:

1) I'm running samba 4 Alpha. I'm aware it is unstable, but apparently Ubuntu made that the default in Natty?

2) At first, [backupEx] was [backup], but I changed the name when I added [backupHd]. 

3) [BackupHd] is the share with no write permission for some reason.  It originally had a different path, but when the write wouldn't work, I changed it to the same path as backupEx to troubleshoot.  Still no write permissions.
 
4) I'm running this over the internet through an SSH tunnel.
 
5) I switched out my domain name and workgroup name for security paranoia reasons. Hope no one minds :)
 
 
Thanks for any advice you may have!
 
-Maythe

---

