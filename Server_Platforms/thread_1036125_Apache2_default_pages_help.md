---
title: "Apache2 default pages help"
date: 2009-01-10
forum: Server Platforms
---

### Post by Jabcor on 2009-01-10
Hi all

I've got apache2 set up, but I'm not sure how to configure default pages.  

For example, if I have index.html in a directory, it displays this, with no problem.  However, if I have index.php and just browse to that directory, it opens a download dialog box.

[http://edub.homeip.net:10001/gallery/](http://edub.homeip.net:10001/gallery/)  for an example of what happens.

Where to I go to configure the server so that it serves up a default page based of a list of default pages.  For example, if I go to [http://edub.homeip.net:10001/gallery/](http://edub.homeip.net:10001/gallery/) I want it to try to open any of the following by default:

index.html
index.htm
default.html
default.htm
index.php
default.php

I'd like this to happen for any directory I go to.

---

### Post by volkswagner on 2009-01-10
I don't know of a global setting in apache that would accomplish your goal.

Depending on how many folders you are talking about, you may just as well create virtual hosts for each folder. That way you can create sub domains and loose the entire trailing folder directory in the address.

---

### Post by mbeach on 2009-01-10
I think you might be looking for the DirectoryIndex directive.

Chances are you can find it in:
/etc/apache2/mods-available/dir.conf

more on DirectoryIndex at:
[http://httpd.apache.org/docs/2.2/mod/mod_dir.html](http://httpd.apache.org/docs/2.2/mod/mod_dir.html)

in your case
```
DirectoryIndex index.html index.htm default.html default.htm index.php default.php
```

---

### Post by mbeach on 2009-01-10
... and you might also want to make sure php is installed.  Search these forums for php download or take a look at:
[http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

to restart apache
```
sudo /etc/init.d/apache2 restart
```

---

### Post by Jabcor on 2009-01-10
Hrmm

My dir.conf was set up pretty much the way I wanted it, without the default.* files.  

Should I be placing DirectoryIndex  inside elements, similar elements as in the dir.conf file, or can I place it anyhwere in the apache2.conf?

---

### Post by mbeach on 2009-01-12
you should be placing it in:
/etc/apache2/mods-available/dir.conf
for serverwide setting

but you can place it in your virtual host files as well, typically in:
/etc/apache2/sites-available/

from the documentation at the link above regarding DirectoryIndex
Context:	server config, virtual host, directory, .htaccess

---

