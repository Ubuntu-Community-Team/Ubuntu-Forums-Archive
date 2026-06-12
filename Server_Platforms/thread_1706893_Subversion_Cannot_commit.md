---
title: "Subversion: Cannot commit"
date: 2011-03-14
forum: Server Platforms
---

### Post by augustuen on 2011-03-14
I just set up a subversion server on my Ubuntu 10.10 server (32-bit), and checking out from the server works like a charm. Commiting however, does not. When I try to commit to the repo I created, it comes back telling me it cannot open /home/svn/myproject/db/txn-current-lock because it has no access to it. I followed the tutorial here: [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

---

### Post by rubylaser on 2011-03-14
If you're just getting started with SCM, you might really want to take a second to check out git.  The complexities of svn are what finally made me want to switch (that and git makes merging branches a cinch).

What are the permissions on the lock file?
```
ls -la /home/svn/myproject/db/txn-current-lock
```

And, did you checkout your original repo before making changes and trying to commit them?

---

### Post by kmike82 on 2011-03-16
If you're running the SVN server with apache, make sure the apache user has access to the repository

here are the directions on the site you linked:
```
And use the following commands to correct file permissions:

   $ cd /home/svn
   $ sudo chown -R www-data:subversion myproject
   $ sudo chmod -R g+rws myproject
```

---

