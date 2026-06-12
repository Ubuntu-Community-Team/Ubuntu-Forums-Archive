---
title: "permissions not working on 10.04 VPS"
date: 2012-01-21
forum: Server Platforms
---

### Post by gregology on 2012-01-21
Hello everyone,

I'm having some issues with permissions on at 10.04 VPS. I have created multiple users and I want to give each user write access to particular directories in /var/www. Some people will need write access to multiple directories and multiple people need access to each directory so I figure I need to use groups. So this is what I've tried;

In this example I was trying to give users dan and greg read/write access to the directory /var/www/speedy.net while making it read only for other users.

```

greg $ sudo usermod -a -G speedy.net dan
greg $ sudo usermod -a -G speedy.net greg

```

I check in webmin that the users have been added to the groups and everything looks fine. Then I chmod and chown the directories

```

greg $ sudo chmod -R 775 /var/www/speedy.net
greg $ sudo chown -R greg:speedy.net /var/www/speedy.net
greg $ ls -l /var/www
drwxrwxr-x  4 greg speedy.net 4096 2012-01-21 09:00 speedy.net
greg $ 

```

and finally I test

```

greg $ ls /var/www/speedy.net
favicon.ico   index.php
greg $ mkdir /var/www/speedy.net/test1
greg $ ls -l /var/www/speedy.net
drwxrwxr-x 2 greg users         4096 2012-01-21 09:00 test1
greg $

```

but

```

dan $ ls /var/www/speedy.net
favicon.ico   index.php   test1
dan $ mkdir /var/www/speedy.net/test2
mkdir: cannot create directory `/var/www/speedy.net/test2': Permission denied
dan $ 

```

Am I doing something simple wrong? I have googled and done a couple of tutorials but I can't figure out what I am doing wrong :confused:. If anyone could point out the obvious I would greatly appreciate it :)

Thanks,

Greg.

---

