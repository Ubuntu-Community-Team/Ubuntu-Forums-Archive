---
title: "Check for internet connection cron?"
date: 2011-09-20
forum: Server Platforms
---

### Post by mac666 on 2011-09-20
Hey
I would like to add a cronjob to check for internet connection.
If the internet connection is down, i would like it to preform certain tasks. 

Perhaps ping Google and if hostname isnt responding or resolved it will do this tasks,
how ever my bash skills is very low...
Anyone who has any idea how to do this? 
Any input are welcome!
Thanks

---

### Post by Ryan Dwyer on 2011-09-20
My bash skills are pretty poor too, but this seems to work:

```

#!/bin/sh

result=`dig google.com +short | wc -l`

if [ "$result" -eq 0 ]; then
    echo "The lookup failed"
fi

```

---

### Post by Lars Noodén on 2011-09-20
You can also use the special variable **$?**

```

#!/bin/sh

/usr/bin/host www.google.com 8.8.8.8 > /dev/null 2>&1;

if [ 0 -eq $? ]; then
  /bin/echo OK;
else
  /bin/echo NO;
fi

```

Unfortunately it does not work with [dig](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/854705), since dig returns 0 regardless of the outcome of the query passed to it.

---

### Post by SeijiSensei on 2011-09-20
> **Lars Noodén said:**
> 
```

#!/bin/sh

/usr/bin/host www.google.com > /dev/null 2>&1;

if [ 0 -eq $? ]; then
  echo OK;
else
  echo NO;
fi

```

I haven't experimented to know if this is true, but might this fail to test properly if you use an internal nameserver that caches records?  I suggest forcing the DNS query to use an external nameserver like Google's at 8.8.8.8.  To do so, replace the host command above with:

```
/usr/bin/host www.google.com 8.8.8.8 > /dev/null 2>&1
```

---

