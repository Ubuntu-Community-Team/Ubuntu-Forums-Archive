---
title: "apache can't see folders?"
date: 2005-11-11
forum: Server Platforms
---

### Post by frank b on 2005-11-11
Hi

I have just installed apache and it works find for the default page. But when I add new folders in the /var/www, sometime's I can not see the new directory from the browser (localhost). Can anybody tell what i going on?

```

frank@joson:/var/www$ ls -lr
total 20
drwxr-xr-x  7 frank root 4096 2005-11-10 22:47 typotest
lrwxrwxrwx  1 root  root   26 2005-11-11 10:45 typo3-quickstart -> /var/lib/typo3-quickstart/
-rw-r--r--  1 root  root   21 2005-11-11 10:29 test.php
drwxr-xr-x  2 frank root 4096 2005-11-10 23:04 pp
lrwxrwxrwx  1 root  root   21 2005-11-11 10:37 phpmyadmin -> /usr/share/phpmyadmin
-rwxrwxrwx  1 root  root    0 2005-11-09 23:50 jep.txt
drwxrwxrwx  7 root  root 4096 2005-11-09 23:28 hans
drwxr-xr-x  2 root  root 4096 2005-11-09 22:51 apache2-default

```

What the browser can se:
```

[DIR] apache2-default/        04-Oct-2005 08:40    -   
[TXT] jep.txt                 09-Nov-2005 23:50    0   
[DIR] phpmyadmin/             06-Oct-2005 12:00    -   
[DIR] pp/                     10-Nov-2005 23:04    -   
[   ] test.php                11-Nov-2005 10:29   21   

```

---

