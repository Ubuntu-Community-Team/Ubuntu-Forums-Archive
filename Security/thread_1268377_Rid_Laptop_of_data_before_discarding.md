---
title: "Rid Laptop of data before discarding"
date: 2009-09-16
forum: Security
---

### Post by cajunlibra on 2009-09-16
I have Xubuntu Intrepid installed on a laptop that I am considering selling. Windows ME was installed on it previously. I have had to installed Xubuntu once or twice before now so the drive has been formatted 2+ times. There isn't any sensitive data on it now but there was under ME.  What can I do to wipe the HD clean? 

I'm no longer a newb but not an expert either.  Something that could be run on a CD would be fine.


Thanks

---

### Post by lindsay7 on 2009-09-16
Take a look at this site,


[http://www.dban.org/about](http://www.dban.org/about)

---

### Post by rookcifer on 2009-09-16
From a live CD, run this command as root:
```

shred -vfz n 1 /dev/sdx
```

Where sdx = name of the drive you want to wipe.  Change it accordingly.

---

