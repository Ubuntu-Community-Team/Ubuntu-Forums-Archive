---
title: "Permission between NAS and other Ubuntu Machine"
date: 2016-07-03
forum: Security
---

### Post by ylafont on 2016-07-03
am hoping someone can set me straigh on this issue, which i cannot seem to get right..

I mounting my NAS Root folder via /etc/fstab with the follwoing command. 

```
//192.168.101.99/root /mnt/NasOneRoot cifs uid=33,username=root,password=PASSWORD ,sec=ntlm,_netdev 0 0
```

The UID=33 option, matches  the user www-data wihch exist on the NAS and my client machine. The userID machtes on both systesms in the /etc/passwd file. 


ON the NAS  there is a share  /c/Owncloud with the following permission beloign to user www-data

```
NasOne:/# sudo -u www-data ls -lisa /c/OwnCloud/
total 28
85786625 4 drwxrwx---  6 www-data www-data 4096 2016-06-29 13:21 .
       2 4 drwxrwxrwx 10 root     root     4096 2016-06-10 13:52 ..
85786679 4 drwxrwx---  2 www-data www-data 4096 2016-06-19 17:14 files_external
85786675 4 -rw-rw----  1 www-data www-data  284 2016-05-22 19:02 .htaccess
85786677 0 -rw-rw----  1 www-data www-data    0 2016-05-22 19:02 index.html
85786681 4 drwxrwx---  5 www-data www-data 4096 2016-06-19 17:14 ylafont
85786676 0 -rw-rw----  1 www-data www-data    0 2016-05-22 19:02 .ocdata
85786700 4 drwxrwx---  6 www-data www-data 4096 2016-06-19 17:14 user2
85786626 4 drwxrwx---  6 www-data www-data 4096 2016-06-19 17:14 user1
```
However, on the client  i have no access to that share

```
ylafont@EclipseOne:/$ sudo -u www-data ls -lisa /mnt/NasOneRoot/c/OwnCloud/
ls: reading directory /mnt/NasOneRoot/c/OwnCloud/: Permission denied
```
total 0preventing me properly access owncloud files. 


I have a seperate thread open at Owncloud, thinking this was an owncloud issue. [https://forum.owncloud.org/viewtopic.php?f=38&t=37493](https://forum.owncloud.org/viewtopic.php?f=38&t=37493)

what am i missing, to have remote permission available to the www-data?  any assistance is greatly appreciated.  thank you.

---

