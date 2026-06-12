---
title: "cgit setup problems"
date: 2009-11-08
forum: Server Platforms
---

### Post by Morrad on 2009-11-08
PROBLEM SOLVED.

I've run into a snag setting up a server with cgit.

As you can see, trying to open one of the projects kicks you back to the main page, even though the url updates in the address bar.  Nothing is spit out in the apache error log when this happens.  I'm not sure what is wrong with my configuration.  Does anyone know what my problem might be?  I've included my settings below.

Thanks.

```
$ cat /etc/apache2/conf.d/git
# cgit Apache Configuration


Alias /git /home/git/repositories/
<Directory /home/git/repositories>
   AllowOverride None
   Options ExecCGI
   DirectoryIndex /cgi-bin/cgit.cgi
   Order allow,deny
   Allow from all
</Directory>
```

```
$ cat /etc/cgitrc
virtual-root=/git/
enable-index-links=1
enable-log-filecount=1
enable-log-linecount=1
snapshots=tar.gz zip

#cache-size=100

css=/htdocs/cgit.css
logo=/htdocs/git-logo.png

root-title=jwgraham.blogsite.org git repositories

root-desc=random 1s and 0s

root-readme=/var/www/htdocs/about.html

# List of repositories
# Include them from a separate file:
include=/etc/cgitrepos
#scan-path=/home/git/repositories
```

```
$ cat /etc/cgitrepos 
repo.url=test_project.git
repo.path=/home/git/repositories/test_project.git

repo.url=git-php.git
repo.path=/home/git/repositories/git-php.git
```

EDIT:

Fixed my issue by restructuring stuff.

---

### Post by njmattes on 2010-02-11
I hate to resurrect a dead thread, but could you explain what you restructured to make this work? I'm having the same problem. Thanks.

---

