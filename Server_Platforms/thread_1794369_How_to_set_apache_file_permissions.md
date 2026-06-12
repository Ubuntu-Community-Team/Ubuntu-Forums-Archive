---
title: "How to set apache file permissions?"
date: 2011-06-30
forum: Server Platforms
---

### Post by rswitzer on 2011-06-30
What is recommended way to set permissions of folders  VAR/WWW for use with apache in 11.04? I would like to let the user "ABC" have access to read/write the website files in this directory. How should permissions on these files be set?

Thanks,
Bob in Tampa

---

### Post by docbop on 2011-06-30
On my systems I create a group for web development and put all the dev team in that group.  Then I can have specific owner with permissions as necessary, and the separate perm's for web team.  Also makes setting perm's for files and directories a lot easier.

---

### Post by kamaji792 on 2011-07-01
Hi @docbop,

I have never had a server actually connected to the web but I do have test server that I can access on my local lan.

I am the only developer so I set the owner to myself and the group to **www-data**.

Files in the /var/www directory look like:
```
-rw-r----- 1 kamaji www-data  214 2009-07-06 14:13 index.php
drwxr-x--- 2 kamaji www-data 4096 2009-10-13 10:43 Lib
```

If you are using some PHP systems that need to write files then you will need to allow the group (www-data) write access.

atb K

---

