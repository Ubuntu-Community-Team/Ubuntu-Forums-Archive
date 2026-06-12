---
title: "Where is the svn log hiding?"
date: 2011-06-27
forum: Server Platforms
---

### Post by SpinningAround on 2011-06-27
I have a svn server that is working and when I'm using Eclipse (with subclipse) can I get a list for all revisions, my question is how I do the same when I'm logged in to the server. I tried svn log /home/svn/repos/project1 but I only got working folder error.

---

### Post by SpinningAround on 2011-07-01
Here is the map structure if for the project, how do I view the log?

```

../svn/repos/
&#9492;&#9472;&#9472; project1
    &#9500;&#9472;&#9472; conf
    &#9474;** &#9500;&#9472;&#9472; authz
    &#9474;** &#9500;&#9472;&#9472; passwd
    &#9474;** &#9492;&#9472;&#9472; svnserve.conf
    &#9500;&#9472;&#9472; db
    &#9474;** &#9500;&#9472;&#9472; current
    &#9474;** &#9500;&#9472;&#9472; format
    &#9474;** &#9500;&#9472;&#9472; fsfs.conf
    &#9474;** &#9500;&#9472;&#9472; fs-type
    &#9474;** &#9500;&#9472;&#9472; min-unpacked-rev
    &#9474;** &#9500;&#9472;&#9472; rep-cache.db
    &#9474;** &#9500;&#9472;&#9472; revprops
    &#9474;** &#9474;** &#9492;&#9472;&#9472; 0
    &#9474;** &#9474;**     &#9500;&#9472;&#9472; 0
    &#9474;** &#9474;**     &#9500;&#9472;&#9472; 1
    &#9474;** &#9474;**     &#9500;&#9472;&#9472; 10
    &#9474;** &#9474;**     &#9500;&#9472;&#9472; 100
				...
    &#9474;** &#9500;&#9472;&#9472; revs
    &#9474;** &#9474;** &#9492;&#9472;&#9472; 0
    &#9474;** &#9474;**     &#9500;&#9472;&#9472; 0
    &#9474;** &#9474;**     &#9500;&#9472;&#9472; 1
    &#9474;** &#9474;**     &#9500;&#9472;&#9472; 10
    &#9474;** &#9474;**     &#9500;&#9472;&#9472; 100
				....
    &#9474;** &#9500;&#9472;&#9472; transactions
    &#9474;** &#9500;&#9472;&#9472; txn-current
    &#9474;** &#9500;&#9472;&#9472; txn-current-lock
    &#9474;** &#9500;&#9472;&#9472; txn-protorevs
    &#9474;** &#9500;&#9472;&#9472; uuid
    &#9474;** &#9492;&#9472;&#9472; write-lock
    &#9500;&#9472;&#9472; format
    &#9500;&#9472;&#9472; hooks
    &#9474;** &#9500;&#9472;&#9472; post-commit.tmpl
    &#9474;** &#9500;&#9472;&#9472; post-lock.tmpl
    &#9474;** &#9500;&#9472;&#9472; post-revprop-change.tmpl
    &#9474;** &#9500;&#9472;&#9472; post-unlock.tmpl
    &#9474;** &#9500;&#9472;&#9472; pre-commit.tmpl
    &#9474;** &#9500;&#9472;&#9472; pre-lock.tmpl
    &#9474;** &#9500;&#9472;&#9472; pre-revprop-change.tmpl
    &#9474;** &#9500;&#9472;&#9472; pre-unlock.tmpl
    &#9474;** &#9492;&#9472;&#9472; start-commit.tmpl
    &#9500;&#9472;&#9472; locks
    &#9474;** &#9500;&#9472;&#9472; db.lock
    &#9474;** &#9492;&#9472;&#9472; db-logs.lock
    &#9492;&#9472;&#9472; README.txt


```

---

### Post by ruffEdgz on 2011-07-01
Just curious if you are using the command 'svn' from the command line?

If you are, try using this to figure out more about svn logs for a repo:
```

svn help log

```
Are those the logs you are talking about?

---

