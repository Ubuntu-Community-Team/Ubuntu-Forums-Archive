---
title: "How to use php-cli with xampp?"
date: 2009-07-27
forum: Server Platforms
---

### Post by absk on 2009-07-27
How do I use php from the command line? I am using xampp.
When I tried to use it, it said unknown commoand. I installed php-cli using apt-get. Now when i use the php command in Terminal, I get:

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysql.so' - /usr/lib/php5/20060613+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysqli.so' - /usr/lib/php5/20060613+lfs/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_mysql.so' - /usr/lib/php5/20060613+lfs/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0


```
I am a total newbie (just 2 days). I did it in Windows, how do I do it here? forgive me if it has been asked earlier, i did not find it.

---

### Post by absk on 2009-07-28
Somebody please reply. Its very important for me.

---

### Post by jacmoe on 2011-01-24
Since this topic insists on being number one in the Google results, here's the answer:

/opt/lampp/bin/php is the command-line php installed by Xampp, so you need to add this line to your .profile:
```
PATH="/opt/lampp/bin:$PATH"
```

---

