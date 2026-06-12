---
title: "Samba Permissions Changing! Why?"
date: 2009-01-28
forum: Server Platforms
---

### Post by OfMacandMen on 2009-01-28
I'm having my permissions change on the Samba share automatically?

Created a share folder call Company_Share
ran chown -R root:users Company_Share

Confirmed permissions on file: drwxrwx---  root user  Company_Share

Samba smb.conf
[Company_Share]
      comment = Company Share File
      path = /share/Company_Share
      valid users = @users
      write list = @users
      force user = root
      force group = users
      read only = No
      create mask = 0770
      directory mask = 0770

The next day the permissions changed to: drwxrwxrwx root admin
and all the files in the directory are drwxrwxrwx root admin 

Check cron jobs and nothing out of the ordinary?

Server: Ubuntu Linux 8.04.1
Samba version 3.028

---

