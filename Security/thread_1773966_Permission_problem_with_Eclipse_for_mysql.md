---
title: "Permission problem with Eclipse for mysql"
date: 2011-06-02
forum: Security
---

### Post by tanveer on 2011-06-02
Hi,
I am designing a web application using php and mysql. currently I have both of them installed in my ubuntu machine. 
Now problem is I am using Eclipse as my IDE and its default workspace is HOME/Workspace/projectfolder. I have added the eclipse path as an alias in apache so that I can browse because it only allows /var/www.
My mysql location is /var/lib/mysql as default. Now the problem arises when my php script tries insert query in the database it fails but the normal select query runs perfect. 
if I create a test php page in /var/www location and it can write to database btw.
How to overcome this issue? whats the recommended way to resolve this?
Thanks in advance.
Below is my Alias part
```

Alias /Author/ "/home/tanveer/Workspace/Author/"
    <Directory "/home/tanveer/Workspace/Author/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

```

I also tried creating a symbolic link in /var/www to my project folder but still it fails to write database. And Eclipse doesn't have permission to create folder in /var/www.:)

---

### Post by tanveer on 2011-06-03
:) I got the problem. Very silly of me. didn't quote the variable in INSERT query.

---

