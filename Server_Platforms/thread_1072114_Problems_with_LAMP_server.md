---
title: "Problems with LAMP server"
date: 2009-02-17
forum: Server Platforms
---

### Post by skym on 2009-02-17
I am new on Ubuntu. I just installed LAMP but i'm having a lot of problem creating databases in mysql. Currently, when I test mysql and localhost test.php as advised by Hardy Herron during the installation, nothing shows.
I am using version 8.04. What can I do

---

### Post by skym on 2009-02-17
I am new on Ubuntu. I just installed LAMP but i'm having a lot of problem creating databases in mysql. Currently, when I test mysql and localhost test.php as advised by Hardy Herron during the installation, nothing shows.
I am using version 8.04. What can I do

---

### Post by overdrank on 2009-02-17
Please do not make multiple threads on the same subject.
Threads merged
I have moved your post from Forum Feedback & Help.

---

### Post by cariboo on 2009-02-17
What is the content of your test.php? it should look something like this:

```
   <?php 
  phpinfo();
?> 
```

To check if mysql is worrking at the prompt type:

```
mysql -u root -p
```

use the password you created when you installed mysql. The above command should get you to the mysql console.

If you need a gui to create databases, I would suggest install phpmyadmin, it is in the repositories and to access it, open firefox and in the address bar type:

```
http://localhost/phpmyadmin
```

Jim

---

