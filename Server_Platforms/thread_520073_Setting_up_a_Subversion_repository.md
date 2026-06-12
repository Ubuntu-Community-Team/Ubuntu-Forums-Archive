---
title: "Setting up a Subversion repository"
date: 2007-08-07
forum: Server Platforms
---

### Post by barnjo on 2007-08-07
I have added a directory /home/svn

I added that path as the SVNParentPath in my dav_svn.conf file

I then CHOWNed that folder to www-data:www-data

On pointing my browser at localhost:8008/svn I get a 403 Forbidden error but not if I goto URL/svn/project

Anyone know whats wrong?

---

### Post by petersk on 2007-08-08
try adding a "/" to the end.  I noticed that it's reasonably fickle with choosing the "exact" url.
Kurt

---

### Post by barnjo on 2007-08-09
Nope, [http://localhost/svn/](http://localhost/svn/) is still forbidden as well

---

### Post by JHuizingh on 2007-08-10
You haven't created any repositories yet.  You need to run something like this:

```
svnadmin create /home/svn/test_repo
```

Set the permissions on that directory, and once that is all set up, you should be able to go to localhost:8008/svn/test_repo and see what is in that repository.

---

