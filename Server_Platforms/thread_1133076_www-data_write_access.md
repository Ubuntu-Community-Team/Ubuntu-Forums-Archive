---
title: "www-data write access"
date: 2009-04-22
forum: Server Platforms
---

### Post by Gatesoft on 2009-04-22
Hi everyone,
I just setup a ubuntu server for some work projects.
I am absolutly new to ubuntu, and just spent the past day and half unsussfully trying to resoluve my current problem. I didnt search becasue this problem has absolutly fried me, so sorry for that.
 
Anyway,
I successfully setup the apache/php/mysql package and tested PHP, all work.
 
I'm trying to install a web-based document management system - opendoc man.
I've succesfully configured it, however, it requires making a "datarepository" and suggest it is outside the web server root, and that folder requires read/write access.
 
I have that folder on /datarepository. I keep getting an error saying that that folder does not have read/write access. I understand apache2 runs as www-data, and like i said, i spent the past day and a half unsussfully trying to grant read/write.
 
Can anyone please help me?
Thanks

---

### Post by cdenley on 2009-04-22
To make www-data the owner the the /datarepository directory and all files and subdirectories within it, use this command
```

sudo chown -R www-data /datarepository

```
The owner should have write permission, unless you changed the permissions.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

