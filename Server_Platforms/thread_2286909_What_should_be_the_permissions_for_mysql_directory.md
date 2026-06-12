---
title: "What should be the permissions for mysql directory?"
date: 2015-07-15
forum: Server Platforms
---

### Post by peter1897 on 2015-07-15
My default permissions for mysql directory /var/lib/mysql are 700 and it's owned by user and group mysql. But with this permissions i can go inside the directory only if i am logged as root user.
Can i make the permissions 750 or 755?

---

### Post by nerdtron on 2015-07-15
The default permissions are there for security reasons. Why do you need to change permissions?

Anyway 750 for folders and 640 for files is still good than 755 or 777.

---

### Post by peter1897 on 2015-07-15
> **nerdtron said:**
> The default permissions are there for security reasons. Why do you need to change permissions?


Because i always have to switch to root user if i want to access the mysql folder. If i try: **sudo cd /var/lib/mysql** on account with admin privileges i get: **sudo: cd: command not found**

---

### Post by SeijiSensei on 2015-07-16
None of the files in /var/lib/mysql are editable by humans.  Other than looking at the directory structure, I can't think of any reason why you would want to "access the mysql folder."

---

### Post by limbenjamin on 2015-07-16
If you make it 750, members of the mysql group can access the directory.

If you make it 755, then anyone can access the directory. 

Warning: This might not be a good idea, any process can access your mysql data directory if it is world readable.

---

