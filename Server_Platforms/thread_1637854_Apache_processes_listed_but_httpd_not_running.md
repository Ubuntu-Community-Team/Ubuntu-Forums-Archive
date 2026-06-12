---
title: "Apache processes listed but httpd not running"
date: 2010-12-05
forum: Server Platforms
---

### Post by aschlosberg on 2010-12-05
I have written this script to monitor Apache2:

```

#!/bin/bash

#count lines that show apache2 but not the fgrep itself
let i=`ps aux | fgrep apache2 | fgrep -v grep | wc -l`

if [ "$i" -gt 0 ]
then
#log something
else
#log something
        /usr/sbin/apache2ctl start
fi

```

It has all been working fine until recently when Apache is becoming unresponsive. I manually ran ps to check and there were 3 processes. However when I ran apache2ctl graceful I got the message 'httpd not running, trying to start'

Is there a better way to check if a daemon is up?

---

### Post by CharlesA on 2010-12-05
So does Apache stop listening when it's "not responding" or what happens exactly?

---

### Post by aschlosberg on 2010-12-05
As far as I can tell it is not listening (at least it's not responding). It's behind an nginx reverse proxy which returns 404 errors for any request that would normally be handled by Apache.

---

### Post by CharlesA on 2010-12-05
When that happens, are you able to connect to the box at all?

---

### Post by GDR! on 2010-12-06
I would suggest monitoring Apache using netcat with -z option to connect to its port instead of just counting processes (Apache port, not nginx port)

---

