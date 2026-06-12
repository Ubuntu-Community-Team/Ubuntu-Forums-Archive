---
title: "Ubuntu User Configuration"
date: 2009-02-13
forum: Server Platforms
---

### Post by SimpleData on 2009-02-13
Hi
I am making an application which uploads files to my Ubuntu Server, and I am planning to distrubute this application on my website.

I am planning to use SFTP to transfer the files. But because the application can be downloaded and used by anyone I would like to create a new user in my server and limit its permissions.

I want the user to:

- Only see /var/www/html/uploads/ (user should not be able to get out this directory)
- Only upload a new file to /var/www/html/uploads/ (can't read,list files,execute,remove,download,rewrite -ONLY UPLOAD A NEW FILE)
- If possible no SSH (Command Line part) access. (I know it is probably not possible)

I would like to use FTP but it is not secure enough.

Sorry for bad English.

Thanks in advance.

---

### Post by SimpleData on 2009-02-14
Bump. I really need help.

---

### Post by SimpleData on 2009-02-14
Bump.

---

### Post by jimv on 2009-02-14
[http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html](http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html)

---

### Post by SimpleData on 2009-02-14
> **jimv said:**
> [http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html](http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html)

Thank you. This is just the thing I was looking for.

---

