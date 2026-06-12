---
title: "run-parts failure"
date: 2010-09-02
forum: Server Platforms
---

### Post by bjh6 on 2010-09-02
Ubuntu 10.04.1 LTS: It appears that run-parts does not run scripts with a period in the name. I had a script upg.sh which run-parts did not recognise; when I changed it to upg it did. This is surely a bug!

---

### Post by surfer on 2010-09-02
```

$ man run-parts

       If neither the --lsbsysinit option nor the --regex option is given then
       the names must consist entirely of upper and lower case  letters,  dig&#8208;
       its, underscores, and hyphens.

```

i had to fight with that before...

---

### Post by bjh6 on 2010-09-02
Many thanks for pointing this out!

But I think that cron.daily, etc, should default to accepting any legal file name - especially one with a period. This has certainly been my experience with other distributions!

---

### Post by jblomb on 2010-09-02
I agree. It took me days to figure out why my cron jobs didn't work in Ubuntu after switching from Fedora. Names like backup.sh and gpstime.cron.

---

