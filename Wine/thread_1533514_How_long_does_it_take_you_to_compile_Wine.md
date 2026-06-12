---
title: "How long does it take you to compile Wine?"
date: 2010-07-18
forum: Wine
---

### Post by Carpentr on 2010-07-18
Just curious. I'm compiling version 1.1.15 of wine
```

./configure
make depend
make
```
and it has been taking me a little over 15 minutes to compile on a quad core processor.

What's the average time for all of you guys?

---

### Post by asdfoo on 2010-07-18
> **Carpentr said:**
> Just curious. I'm compiling version 1.1.15 of wine
```

./configure
make depend
make
```
and it has been taking me a little over 15 minutes to compile on a quad core processor.

What's the average time for all of you guys?


maybe 6 minutes or so, less if I've compiled it before and am using ccache.

I suggest you try this instead:
```

./configure
make depend
make -j10

```

This tells make to do 10 tasks in parallel, yes you have only 4 cores, but not all time is spent processing on each core at 100% - the jobs that run (gcc, as, ld) spend time waiting for disk reads and writes to complete.  You can watch the activity with top, press 1 to show cpu stats.

---

### Post by Carpentr on 2010-07-18
> **asdfoo said:**
> maybe 6 minutes or so, less if I've compiled it before and am using ccache.

I suggest you try this instead:
```

./configure
make depend
make -j10

```

This tells make to do 10 tasks in parallel, yes you have only 4 cores, but not all time is spent processing on each core at 100% - the jobs that run (gcc, as, ld) spend time waiting for disk reads and writes to complete.  You can watch the activity with top, press 1 to show cpu stats.

Alrighty. Thanks for the tip.

---

