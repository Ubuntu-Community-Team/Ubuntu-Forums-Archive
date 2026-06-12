---
title: "Apache Default directory"
date: 2011-03-16
forum: Server Platforms
---

### Post by cosine_omerta on 2011-03-16
I have set up multiple accounts on my ubuntu 10.10 webserver, apache2, and everything  is fine, each user has their own www directory, and have their pages  that display at the correct address,  [www.myserver.net/~userjane/index.html](www.myserver.net/~userjane/index.html), and  [www.myserver.net/~userbob/index.html](www.myserver.net/~userbob/index.html).

I am having some problems if you just put in [www.myserver.net](www.myserver.net), you  automatically get userbob's index page.  I was wanting to have my own  personal home folder www director be the default folder, so that if you  put in [www.myserver.net/index.html](www.myserver.net/index.html) then you would get whatever file was  in my user name directory. Same with if you just put in  [www.myserver.net/](www.myserver.net/)

How would I do this?  Thanks!

---

### Post by volkswagner on 2011-03-16
What does your httpd.conf look like?

```
cat /etc/apache2/httpd.conf
```

What do you have in /etc/apache2/sites-enabled?

```
ls -alt /etc/apache2/sites-enabled
```

---

### Post by cosine_omerta on 2011-03-16
My httpd.conf file is completely empty.

My sites-enabled looks like this
```

drwxr-xr-x 2 root root 4096 2011-03-16 14:05 .
lrwxrwxrwx 1 root root   25 2011-03-16 14:05 userbob-> ../sites-available/userbob
lrwxrwxrwx 1 root root   32 2011-03-16 14:02 userjane-> ../sites-available/userjane
drwxr-xr-x 7 root root 4096 2011-03-08 06:50 ..
lrwxrwxrwx 1 root root   29 2011-03-07 10:35 zachswebpages -> ../sites-available/zachswebpages
```

---

### Post by volkswagner on 2011-03-16
I will assume that zach is what you want loaded for xxxx.net requests.

If all your host files (none posted) have the same directive, apache will serve alphabetically ( I believe... unconfirmed).

So if each host has
```
<virtualhost *>
```

or similar, apache2 needs a way to decide what is default, therefore it picks the first match which would be userbob.

I suggest changing the host file name.

```
sudo cp /etc/apache2/sites-available/zachswebpages /etc/apache2/sites-available/azachswebpages
```

then enable the site, restart apache2, and test.  If all is well, you can disable zachswebpages, restart apache, test, then delete the file if all is well (or just keep it disabled).

---

### Post by cosine_omerta on 2011-03-16
That did it.  Now my directory is the first in line. Thanks for the info.

---

