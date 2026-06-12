---
title: "Moving file between two remote servers with a cron job"
date: 2008-12-02
forum: Server Platforms
---

### Post by OOzypal on 2008-12-02
Hello,

I need to move big files from one remote server to other remote
server. I think I can do this by cron jobs. The urls for the backup
data is for example

[www.xyz.com/file1.tar](www.xyz.com/file1.tar).
[www.xyz.com/file2.tar](www.xyz.com/file2.tar)

I do

wget  -c -t 999 [www.xyz.com/file1.tar](www.xyz.com/file1.tar)
wget  -c -t 999 [www.xyz.com/file2.tar](www.xyz.com/file2.tar)

How can I make a cron job to automatically move these files between
the two servers.

---

### Post by hictio on 2008-12-02
Add this to the crontab, for instance:
```

## Will be executed everyday @ 03:38 AM
38 3 * * * wget -c -t 999 www.xyz.com/file1.tar 1>/tmp/_backup.file1.log 2>/tmp/_backup.file1.log

## Will be executed everyday @ 05:38 AM
38 5 * * * wget -c -t 999 www.xyz.com/file2.tar 1>/tmp/_backup.file2.log 2>/tmp/_backup.file2.log

```

Perhaps, you'll need to add the full path to the wget app.

---

### Post by hyper_ch on 2008-12-02
or if you have ssh access to both sevrvers you could setup key-based login and use SCP instead.

---

### Post by hictio on 2008-12-02
> **hyper_ch said:**
> or if you have ssh access to both sevrvers you could setup key-based login and use SCP instead.

If you decide to do this, be sure to check [Rsync](http://en.wikipedia.org/wiki/Rsync), specially since the files are tar'ed.

---

### Post by HermanAB on 2008-12-02
Yes, rsync over SSH would be the best way to do it.

Cheers,

Herman

---

