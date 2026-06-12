---
title: "rsync to a file?"
date: 2012-11-12
forum: Server Platforms
---

### Post by floobit on 2012-11-12
I'm trying to create a backup strategy using s3tools and glacier, and am wondering if rsync (or similar) can create a solid file of the "diffs" it generates.  
Because glacier is designed to handle a few large files, I would like to create an initial snapshot of my fs, then create monthly "diffs."  If I ever needed to restore, I'd iteratively apply the diffs to the snapshot.  Presumably, I'd need to keep a local, cached copy of last month's filesystem for rsync to compare with.  Upon generating the update file, rsync would also update the cache fs copy.  

Any thoughts on how this could be done?  I've seen this strategy in enterprise backup software, but unfortunately do not have the budget for using that software at home.  Is there a FOSS variant?  

Thanks

---

### Post by sandyd on 2012-11-12
You can compress the entire folder with gzip and upload that instead

like
```

tar czf backup-$(date +"%m_%d_%Y").tar.gz /path/to/rsync
```

---

### Post by floobit on 2012-11-12
True.  I'm guessing the fs will be 1.5 T or so, and individual updates on the order of 100M, so uploading the whole filesystem each month would not be feasible.  I suppose I could use tar's incremental backup feature ([http://www.gnu.org/software/tar/manual/html_section/after.html](http://www.gnu.org/software/tar/manual/html_section/after.html)).  Applying updates would be easy too.  The question is, is this available with rsync-style file analysis?

---

### Post by Lars Noodén on 2012-11-12
If you go for using tar, the [ISO-8601](http://www.cl.cam.ac.uk/~mgk25/iso-time.html) date format will sort better.

```

tar czf backup-$(date +"%Y-%m-%d").tar.gz /path/to/rsync
# or
tar czf backup-$(date +"%F").tar.gz /path/to/rsync

```

---

### Post by sandyd on 2012-11-13
> **floobit said:**
> True.  I'm guessing the fs will be 1.5 T or so, and individual updates on the order of 100M, so uploading the whole filesystem each month would not be feasible.  I suppose I could use tar's incremental backup feature ([http://www.gnu.org/software/tar/manual/html_section/after.html](http://www.gnu.org/software/tar/manual/html_section/after.html)).  Applying updates would be easy too.  The question is, is this available with rsync-style file analysis?

in this case, I would reccomend rdiff-backup.

---

### Post by rubylaser on 2012-11-14
> **sandyd said:**
> in this case, I would reccomend rdiff-backup.

+1.  This is a great solution for your situation.

---

### Post by floobit on 2012-11-14
Indeed.  That is exactly what I was hoping would exist.  Thanks sandyd.

---

