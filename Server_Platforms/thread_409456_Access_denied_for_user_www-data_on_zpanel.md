---
title: "Access denied for user www-data on zpanel"
date: 2007-04-14
forum: Server Platforms
---

### Post by tiger.woods on 2007-04-14
I'm trying to install zpanel and am gettingthe following error:

Access Denied for user 'www-data'@'localhost' (using password: NO)

What eaxactly does this mean and how do I fix it? does it mean the user www-data doesn't have access to read/write to the zpanel directory?

I've installed the zpanel directory under /var/www if it helps.

TW,

---

### Post by NPALeech on 2007-04-14
Enter this in a terminal:

sudo chown -R www-data:www-data /var/www/Zpanel

---

### Post by tiger.woods on 2007-04-14
That seemed to have worked! I had to change the permissions then run the setup  from /admin/install.php

So, it's a file access issue on the zpanel directory.

Thanks.

TW,

---

### Post by metroknight on 2007-04-14
> **NPALeech said:**
> Enter this in a terminal:

sudo chown -R www-data:www-data /var/www/Zpanel

Hi, quick question.

I know what sudo means but what does " chown -r "mean? 
The rest of it is just his files and location of them, right?

---

### Post by NPALeech on 2007-04-14
chown changes the ownership of the directory/files

-R specifies that you want the contents of directory, and all sub-dirctories, to change ownership as well.

www-data:www-data Specifies which user:group you wish to change the ownership to.

---

### Post by metroknight on 2007-04-14
thanks for the info.

---

### Post by az on 2007-04-14
You should really ask on the zpanel project's forum.  Chowning your web application directory can not be secure...

---

