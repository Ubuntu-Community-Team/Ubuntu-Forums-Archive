---
title: "chmod problem"
date: 2008-12-08
forum: Server Platforms
---

### Post by PryGuy on 2008-12-08
Good day everyone! This question relates to CLI in general but since there are many CLI geeks I thought I'd better post it here.

So the question is: dirs should be executable, right? I can't access them otherwise. What if I have to set 644 permissions on some dirs including subdirs? doing 'chmod -R 644 /path/to/dir' makes directories unaccessible... How do I make it right?

---

### Post by sisco311 on 2008-12-08
you can use the find command:
```
find /path/to/dir/ -type f -exec chmod 0644 {} \;
```

*find /path/to/dir/ -type f* = find the files in /path/to/dir
*-exec chmod 0644 {} \;* = set the permissions to 644

---

