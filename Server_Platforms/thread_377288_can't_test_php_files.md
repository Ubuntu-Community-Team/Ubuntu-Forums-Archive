---
title: "can't test php files"
date: 2007-03-05
forum: Server Platforms
---

### Post by ateet101 on 2007-03-05
i used [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to set everything up
i made a test.php file and put it in /var/www when i put [http://localhost/test.php](http://localhost/test.php)   it will not load the page.  i am sure that apache is running because when i try to start it it says apache is running

---

### Post by majoridiot on 2007-03-06
you didn't say what error, so i'm taking an educated guess... one the server-side try:

```
sudo apt-get install libapache2-mod-php5
```

install it, restart apache and try loading the page again.

---

### Post by Mr. C. on 2007-03-06
What is the output of:

php -r 'echo "PHP Works!\n";'

Php is installed and working if you get the printout PHP Works!

MrC

---

