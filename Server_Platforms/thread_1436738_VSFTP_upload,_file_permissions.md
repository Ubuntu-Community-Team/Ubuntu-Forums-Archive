---
title: "VSFTP upload, file permissions"
date: 2010-03-23
forum: Server Platforms
---

### Post by ade234uk on 2010-03-23
I have vsftp and can login to the folder for user. I can upload and download files via ftp without any issues.

The only problem I have is that when I upload the files It is not being uploaded with the correct permissions, so when I am viewing the file through Apache, I get the permission denied. 

If I manually change the permission of the file to say 755 the file is then executable.

So my question is,
How do I change permission for my user so that all files uploaded are executable when viewing through Apache?

---

### Post by Bachstelze on 2010-03-23
In vsftpd.conf

```
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=077

```

Change to 022.

---

### Post by ade234uk on 2010-03-23
Thank you I will give this a go.

---

### Post by ade234uk on 2010-03-24
Thank you, it worked. I can now upload files with correct permissions.

---

### Post by vanwykn on 2013-02-09
helped me as well. tks

---

