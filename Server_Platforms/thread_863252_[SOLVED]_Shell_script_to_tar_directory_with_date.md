---
title: "[SOLVED] Shell script to tar directory with date"
date: 2008-07-18
forum: Server Platforms
---

### Post by Keymaster on 2008-07-18
[COLOR="Red"]**EDIT: Problem solved**[/COLOR]

I need to write a script to tar a directory /datab/data based on the current date.  The date needs to be in the format YYMMDD  the filename should be database_YYMMDD.  How can I do this?  Thanks

PS: This is actually for a redhat EL 4 database production mysql server but I only belong to my beloved Ubuntu forums.  I'm using /bin/bash  Thanks

---

### Post by hyper_ch on 2008-07-18
```

#!/bin/bash
DATE=/bin/date;
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
echo $NOW

```
that will give you a variable $NOW with YYYY-MM-DD_HH:mm

you can change it accordingly

---

### Post by Keymaster on 2008-07-18
Thank you.  I actually figured it out through some books I found laying around the office.

---

