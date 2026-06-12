---
title: "phpmyadmin help"
date: 2006-10-06
forum: Server Platforms
---

### Post by tmez on 2006-10-06
i was wondering how to login to phpmyadmin because i have tried to login using my username and password for my desktop.
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by az on 2006-10-06
> **tmez said:**
> i was wondering how to login to phpmyadmin because i have tried to login using my username and password for my desktop.
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

By default, there is no root password set.  Log is an root and then set a password.  Then, create a user with limited permissions to do real work.

---

### Post by tmez on 2006-10-06
which means my username? or just blank

---

### Post by peanut butter on 2006-10-06
issue the following command at terminal: 
```
mysqladmin password mypasswordhere
```

replacing mypasswordhere with a password.:)

then you can login as root with your password

---

### Post by az on 2006-10-07
> **tmez said:**
> which means my username? or just blank

Log is as root in mysql.  The mysql users (root and otherwise) are completely different from the system users.  After mysql is installed, there are no users set nor is there a root password set.  You do not have to create a user with the same name as your system user name.  It's completely seperate.

---

### Post by tmez on 2006-10-07
can u also tell me how to get a domain on my server instead of it being [http://localhost](http://localhost)

---

### Post by az on 2006-10-07
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

