---
title: "is it possible to..."
date: 2008-07-29
forum: Server Platforms
---

### Post by skunkrecords on 2008-07-29
I have a dedicated SVN server, and I was wondering if there was a way to some how view it through my LAMP server (they're the same box). Is there a way to make my SVN directory my webroot, so any change made through SVN can be seen immediately? 
That seems rather tricky...

---

### Post by skunkrecords on 2008-07-29
I forgot to clarify. The SVN server hosts PHP projects, so I want the scripts to actually execute. :lolflag:

---

### Post by sonofusion82 on 2008-07-29
you can probably try to checkout the files in SVN into the webroot then have a php script or cron job to do execute "svn up" periodically

---

### Post by cariboo on 2008-07-29
Just creat a symlink from /var/www to your svn directory eg:

in /var/www

```
ln -s /path/to/svn svn 
```

then you can access the directory via [http://yourserver/svn](http://yourserver/svn)

Jim

---

