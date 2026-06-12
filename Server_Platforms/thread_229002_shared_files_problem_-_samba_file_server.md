---
title: "shared files problem - samba file server"
date: 2006-08-03
forum: Server Platforms
---

### Post by apollard on 2006-08-03
I have set up a file server for the house using samba. I have directories setup for each user, and one shared directory. The users are in a group, and the directories permissions are set for rws for both the user and group, and no access for other.

The smb.conf:
[global]
workgroup = home
printcap name = CUPS
disable spoolss = Yes
show add printer wizard = No
printing = cups
[shared]
comment = shared files
path = /data/shared
valid users = andy tam
read only = No
write list = tam andy
[tam]
comment = Tams Files
path = /data/tam
read only = No 
valid users = tam andy
write list = tam andy
[andy]
comment = Andys Files
path = /data/andy
read only = No 
valid users = andy
[master]
comment = Master work area files
path = /data
valid users = andy
read only = No
[printers]
comment = Print Temporary Spool Configuration
path = /var/spool/samba
printable = Yes
guest ok = Yes
use client driver = Yes
browseable = No


I can connect to the server from all my computers, and each user can connect fine. All users can connect to the shared directory. The problem occurs when a user creates a file in the share directory. Only the creator can write / execute the file. I tried adding the write list to samba, and that is how I determined the problem was with the file permissions. The permissions are set to rws for the user (what I want) and r-- for the group. How can I change the setup to allow users to create and share work files?

TIA,
Andre

---

### Post by dtfinch on 2006-08-04
On shared folders I usually use the "force user" option to easily get around this problem, like "force user=root", though I guess any username would work.

A more involved solution, if you want to preserve ownership but have the same lax permissions, might be:
create mask=0777
directory mask=0777
force create mode=0777
force directory mode=0777
security mask=0000
directory security mask=0000
But I haven't really tried that yet.

---

### Post by apollard on 2006-08-06
Thanks, the force create seems to have solved the problem-

Andre

---

