---
title: "Apache - upload directory for users"
date: 2009-07-23
forum: Server Platforms
---

### Post by lmlypfan on 2009-07-23
I want to create a directory where visitors can upload files. 
I'm sure its an easy process, but i can't figure it out. 

i have permissions on the "Upload" folder set to 777 for the user and group www-data

Also, how do i tell what version of software I'm using? For example, how do i check the specific version of Apache I'm running. I know its Apache2, but not sure what revision. 

Thanks

---

### Post by mlinux on 2009-07-23
If you are new to ubuntu like me, should install webmin and manage the ubuntu server from remote workstation. That save lots of learning.

Apache server is web server, I believe you need to use FTP to upload files. If for internal network, should setup samba for file sharing instead.

---

### Post by lmlypfan on 2009-07-23
I can access the upload folder on my LAN via NFS, and use proftp when outside my LAN. 

I was looking for a way for users outside my LAN to upload files to a specific folder.

My google searches keep returning php info, so i'm assuming is going to be a script of some kind. 

I have webmin installed, but i'd rather learn whats under the hood. 

thanks though.

---

### Post by wojox on 2009-07-23
In terminal:

```
aptitude show apache2
```

Or

Put that in documentroot and open browser to localhost

[PHP]<?php phpinfo();?>[/PHP]

---

### Post by Thirtysixway on 2009-07-24
You're going to need some type of PHP script to allow your visitors to upload files.  

I hope you understand that letting users upload files to a web-accessable (or any..) folder can be a huge security risk.

Understand what you're doing before you allow just anyone to upload.  The last thing you want is some random person being able to upload and execute code on your server.

---

