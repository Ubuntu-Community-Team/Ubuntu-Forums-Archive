---
title: "Mysql backup"
date: 2009-09-18
forum: Server Platforms
---

### Post by januzi on 2009-09-18
Hi

I'm looking for an application that would help me with backing-up mysql database. I tried mysqldump, but it took 100% of the cpu. Tar is almost good, but it is complaining about files that are updated by mysql (maybe repeat-until could help here?). Master-slave looks rather hard. 

That application should fetch all the data without killing cpu. I don't mind if it will take an hour.

---

### Post by DaithiF on 2009-09-18
Hi, i think mysqldump is still the right tool for the job.
why not run it with nice -n 15 or something to encourage it not to hog the cpu:

```
nice -n 15 mysqldump -h host -u user etc.....

```

---

### Post by januzi on 2009-09-18
Thanks. Everything is working fine (well, at the moment).

---

