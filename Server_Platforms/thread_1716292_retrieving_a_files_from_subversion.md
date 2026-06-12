---
title: "retrieving a files from subversion"
date: 2011-03-28
forum: Server Platforms
---

### Post by pdc124 on 2011-03-28
ive got a subversion repo (home/svn) that contains  website pages that im working on. The subversion bit works well (!).
I now want to move the final version of the web page from the svn repo to the document root , on the same machine 
ie /home/svn/website/branch/file.php to /var/www/weebsite/

can i do it from the server  ? AFAICS /home/svn/website/branch/file.php exists just in the database and not as somthing i can cp from svn to document root . 
is this correct ?

---

### Post by t3r0 on 2011-03-28
> **pdc124 said:**
> ive got a subversion repo (home/svn) that contains  website pages that im working on. The subversion bit works well (!).
I now want to move the final version of the web page from the svn repo to the document root , on the same machine 
ie /home/svn/website/branch/file.php to /var/www/weebsite/

can i do it from the server  ? AFAICS /home/svn/website/branch/file.php exists just in the database and not as somthing i can cp from svn to document root . 
is this correct ?

yep, the files commited to svn do not exists as "regular" files in filesystem so you need to use normal svn commands to get them.. SVN does support file:// protocol to access local svn repos... 

eg. 
```
svn export file:///home/svn/my_repo /path/to/some/location
```


You can also checkout a repository as well, but when deploying to production (or anything public) you always want to use export...


- Tero

---

