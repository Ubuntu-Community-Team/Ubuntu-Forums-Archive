---
title: "Error Samba ubuntu 20.04 more files"
date: 2021-10-11
forum: Server Platforms
---

### Post by nicutdk on 2021-10-11
Hello,

I installed Ubuntu 20.04 server and I configure samba simple.

[global]
   unix charset = UTF-8
   workgroup = WORKGROUP
   log file = /var/log/samba/log.%m
   log level = 3
   max log size = 1000
   logging = file
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
   bind interfaces only = yes
   interfaces = 192.168.111.2
   hosts allow = 192.168.111.0/24 127.0.0.1




[privateshare]
   path = /var/www/vhosts/portal
   browseable = Yes
   read only = No
   guest ok = no
   directory mask = 0775
   create mask = 0664
   valid users = @smbinternal
   inherit permissions = yes


I generate from my windows 10 more scripts with phpcomposer and write to ubuntu server via samba.

Works fine but never finis to put all files. 

Same files give me that error:

[2021/10/11 16:27:34.235513,  2] ../../source3/smbd/open.c:4023(open_directory)
  open_directory: unable to create folder1/vendor/composer/ad4a6582/Seldaek-monolog-fd4380d/src/Monolog/Processor. Error was NT_STATUS_OBJECT_NAME_COLLISION
[2021/10/11 16:27:34.235917,  2] ../../source3/smbd/open.c:1452(open_file)
  myuser opened file folder1/vendor/composer/db8830fa/soundasleep-html2text-3243a71/tests/utf8-example.txt read=No write=Yes (numopen=10)
[2021/10/11 16:27:34.236378,  2] ../../source3/smbd/open.c:4023(open_directory)
  open_directory: unable to create folder1/vendor/composer/9bc74a7f/doctrine-dbal-96b0053/src/Platforms. Error was NT_STATUS_OBJECT_NAME_COLLISION


I try to google more than one week but can't find a solution.

Can I solved that ?

I try on my old server with samba 4.10 and centos and works fine.


Best Regards,

---

