---
title: "Disk space use"
date: 2011-07-19
forum: Server Platforms
---

### Post by schoolpride on 2011-07-19
My ubuntu server is a 1.5T with 448GB available.  When I backup my files each night, my files only amount to 397GB.  Is there an easy way to see where the extra 600 GB on my server is located?  

I think that I might have had a couple of old backups write to the server, but I cannot find them.

---

### Post by Wayne_V on 2011-07-19
# cd /<1.5T mount point>

# du -sk  *   .*   | sort -n

---

### Post by Wim Sturkenboom on 2011-07-19
You might very well have made a backup while the backup device was not mounted.

Unmount any external devices and next run

```

sudo du -k --max-depth=1 /

```

---

