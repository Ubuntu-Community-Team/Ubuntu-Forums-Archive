---
title: "PHP/Apache2 Restricted in File Manipulation?"
date: 2010-08-18
forum: Server Platforms
---

### Post by kotakotakota on 2010-08-18
Hello,
I have a LAMP server set up (under Ubuntu 10.04 64-bit), and have a PHP application running on the Apache2 server.  I copied the "default" website setup, and created a new one with the root at "/home/kota/WebRoot/".  When running my PHP application though, I come across a major issue: The script doesn't seem to be able to modify any files that are currently on the system, or create new ones.  However, this limitation is restricted to when running through Apache2.  In other words, if i run it by typing "php5 myapplication.php" from the terminal, it works without a flaw.  This leads me to believe that there is a permissions issue, disallowing Apache2 to create and modify files anywhere on my system.  If anyone can give me a pointer as to how I can fix this problem, I would greatly appreciate it!

Although it shouldn't make much of a difference, here is the basic information that I feel I should provide:
```
kota@kota-desktop:~$ uname -a
Linux kota-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
kota@kota-desktop:~$ apache2 -v
Server version: Apache/2.2.14 (Ubuntu)
Server built:   Apr 13 2010 20:21:26
kota@kota-desktop:~$ php5 -v
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP 5.3.2-1ubuntu4.2 with Suhosin-Patch (cli) (built: May 13 2010 20:03:45) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies

```

Thanks!

---

### Post by Ryan Dwyer on 2010-08-18
When you run php5 myapplication.php it runs it as your user account, using your privileges. You have read and write access to your home folder so it works fine. Apache requests are done via the user www-data, which cannot write to home directories using the default permissions.

You should locate the files that need to be modified by Apache, then change the group on those files to www-data and give group the write permission.

Something like:
chgrp www-data filename
chmod g+w filename

---

### Post by Bachstelze on 2010-08-18
Normally, Apache runs as user www-data, and therefore, when a PHP script running in Apache wants to perform some filesystem action, the kernel will check whether the www-data user has permission to do it.  When you run your script on the command-line, on the other hand, the script runs with your permissions, which are probably different since you are in your home directory.

You can either give www-data the necessary permissions to perform the actions in your script, or use suPHP to make the script run with your permissions.

---

