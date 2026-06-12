---
title: "SAMBA Share Read Write permissions"
date: 2010-03-23
forum: Server Platforms
---

### Post by rockercya on 2010-03-23
hi
 
i have setup a samba server and created samba shares on it, i have configured the samba server to authenticates users from a windows server 2003 DC, 
 
i have 2 shares call IT and MYSHARE, I want to give read and write permissions to sevaral users to those two shares and read only permisson to all the other users.
 
i tried editing the smb.conf file with the following settings , but no one can write or modify the files in the shares including the users specified in the 
**write list = cweerasinghe,njayarathna.**
 
 
[IT]
 
writeable = Yes
browseable = yes
public = no 
comment = IT share
path = /etc/samba/SHARE
write list = cweerasinghe,njayarathna
 
 
[MYSHARE]
guest ok = no 
writeable = Yes
public = no 
path = /GOV
writeable = yes
browseable = yes
write list = cweerasinghe,njayarathna
 
how can i give access to the **write list = cweerasinghe,njayarathna** users to
read, write and modify the files in the shares ?? 
 
 
regards
 
chamara

---

### Post by jrssystemsnet on 2010-03-23
What are the **filesystem** permissions on /etc/samba/SHARE and /GOV, please.  Post output of **ls -l /etc/samba | grep SHARE** and **ls -l / | grep GOV**.

---

### Post by rockercya on 2010-03-23
Hi
 
thanx fro the reply,
 
when i run **ls -l /etc/samba | grep SHARE** i got  **drwxr-xr-x 2 root root  4096 2010-03-22 17:58 SHARE** as the result 
 
and when run** ls -l / | grep GOV** igot **5 root root  4096 2010-03-22 11:33 GOV **
 
what does this mean?? 
 
please help
 
regards
 
chamara

---

### Post by jrssystemsnet on 2010-03-23
This means that only the root user has write permissions to either of those folders.  Samba cannot override existing filesystem permissions.

You can either **chmod -R 777 /etc/samba/SHARE** and **chmod 777 /GOV** - which makes them world-writeable - or you can **chgrp -R somegroup** both of them, where "somegroup" is the group all your write users belong to, and then **chmod -R 775** both of them (make them group-writeable but not world-writeable).

---

### Post by rockercya on 2010-03-24
Hi
 
this works , i changed as you mentioned ,
 
**chmod -R 777 /etc/samba/SHARE** and **chmod 777 /GOV** and after that im able to assign different permissions to different users
 
thanks a lot
 
regards
 
chamara

---

