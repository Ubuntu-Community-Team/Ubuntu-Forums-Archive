---
title: "Software or Configuration: Locking files when someone edits them"
date: 2008-03-04
forum: Server Platforms
---

### Post by micdhack on 2008-03-04
I need to ask if there is a configuration or a software that can lock files when edited and free them when work is done by the user. I need this for group development of a project.

---

### Post by rapiscan on 2008-03-05
I recommend a version control system like SVN: 
[http://subversion.tigris.org/](http://subversion.tigris.org/)

This allows multiple people to check out files from a repository and they can all edit the files at the same time.  If two people edited the same file, you can merge the changes.

You can install subversion like so:
```
sudo apt-get install subversion
```

---

### Post by micdhack on 2008-03-06
subversion is good for version control but since the site will have its internal version control in future(created by us) i want something simpler like locking a file when used from an utility(nano, proftpd) and unlock it after a certain amount of time. I don't know if this is possible to be achieved.

---

