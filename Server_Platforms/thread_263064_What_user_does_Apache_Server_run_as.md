---
title: "What user does Apache Server run as?"
date: 2006-09-22
forum: Server Platforms
---

### Post by Avian00 on 2006-09-22
I keep running into strang permissions problems with my Apache server on an Ubuntu Server 6.06 box.  I'm installing several web apps, some of which include CGI scripts.

Bottom line is that I have no idea what user Apache Server runs server-side stuff as, and the only thing I know to do is just 'chmod a+rw' on all the stuff I need access to, but I know this is terribly insecure.  Can somebody please explain in a sane way how Apache permsissions should work and what user Apache Server runs stuff as?

Thanks!

---

### Post by paul.maddox on 2006-09-22
User: www-data
Group: www-data

I normally change the ownership of my web files to my username, and the group to www-data.
I then give read-write access to my user, read-only access to apache, and no access to anyone else.

# chown -R myusername /path/to/webroot
# chgrp -R www-data /path/to/webroot
# chmod -R 640 /path/to/webroot/*php

---

### Post by fstab on 2006-09-23
The first httpd process is started by root and runs as root.  It forks off child processes to handle page requests and the owner of those processes is set in the httpd.conf file.

The following lines in httpd.conf determine what user the httpd processes will run as.

```
User www-data
Group www-data
```

---

### Post by colindaven on 2008-01-03
Thanks for that Paul Maddox and fstab

I have one question to this line however -- are you just changing permissions of any php files with this in all directories below the web root ?

# chmod -R 640 /path/to/webroot/*php

I get a no such file or directory error running it.

Thanks,
Colin
--
chmod -R 640 /var/www/*php
chmod: cannot access `/var/www/*php': No such file or directory

---

### Post by devliljohn on 2008-01-11
> **colindaven said:**
> Thanks for that Paul Maddox and fstab

I have one question to this line however -- are you just changing permissions of any php files with this in all directories below the web root ?

# chmod -R 640 /path/to/webroot/*php

I get a no such file or directory error running it.

Thanks,
Colin
--
chmod -R 640 /var/www/*php
chmod: cannot access `/var/www/*php': No such file or directory

almost but you need to do *.php
also i would just do the whole directory

heres what i would do 

cd *insert path to www directoriy*
sudo chmod -R 640 *
sudo chmod -R ug+X *    

the last line will allow you to list the contects of the directories without giving execute permissions to the files

---

