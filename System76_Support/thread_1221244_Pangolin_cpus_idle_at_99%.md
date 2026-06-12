---
title: "Pangolin cpus idle at 99%"
date: 2009-07-23
forum: System76 Support
---

### Post by marshmallow1304 on 2009-07-23
2 of the last 3 times I turned my Pangolin on, I noticed that the fan was running high.  I checked cpu load and saw that both cpus are registering at 99%, even when I'm not doing anything.  Restarting returns them to normal.

Any ideas as to why this is happening?

---

### Post by jdb on 2009-07-23
> **marshmallow1304 said:**
> 2 of the last 3 times I turned my Pangolin on, I noticed that the fan was running high.  I checked cpu load and saw that both cpus are registering at 99%, even when I'm not doing anything.  Restarting returns them to normal.

Any ideas as to why this is happening?

Run

```
top
```

from the command line.

```
man top
```

will tell you all about it.

jdb

---

### Post by marshmallow1304 on 2009-07-23
Ah.  It seems gnome-do had problems initializing.

Thanks.

---

