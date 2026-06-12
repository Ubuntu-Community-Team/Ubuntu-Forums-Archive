---
title: "vsftpd ownership"
date: 2007-08-31
forum: Server Platforms
---

### Post by wanabewired on 2007-08-31
Hi,

This should be a relatively quick question but i'll give some background..

I have a /var/www/ which is owned by root:wwwchange. Each time the users create files or directories, they are owned by the user and thier group

drwxrwxr-x  3 root  wwwchange 4096 Aug 31 09:25 directory1
drwxrwxr-x  3 user1 user1     4096 Aug 31 09:32 directory2
drwxrwxr-x  2 root  wwwchange 4096 Aug 30 20:16 directory3
drwxrwxr-x 11 root  wwwchange 4096 Aug 30 22:04 directory3

I need the group to automatically change to wwwchange on creation of files and directories.

My ftpd is vsftpd

Any help would be much appreciated.

---

### Post by soulresin on 2007-08-31
> **wanabewired said:**
> Hi,

This should be a relatively quick question but i'll give some background..

I have a /var/www/ which is owned by root:wwwchange. Each time the users create files or directories, they are owned by the user and thier group

drwxrwxr-x  3 root  wwwchange 4096 Aug 31 09:25 directory1
drwxrwxr-x  3 user1 user1     4096 Aug 31 09:32 directory2
drwxrwxr-x  2 root  wwwchange 4096 Aug 30 20:16 directory3
drwxrwxr-x 11 root  wwwchange 4096 Aug 30 22:04 directory3

I need the group to automatically change to wwwchange on creation of files and directories.

My ftpd is vsftpd

Any help would be much appreciated.

chmod g+s /var/www

Or look into a default acl using setfacl.

---

