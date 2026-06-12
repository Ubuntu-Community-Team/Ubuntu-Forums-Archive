---
title: "memcached not automatically started upon boot"
date: 2010-02-28
forum: Server Platforms
---

### Post by aks_! on 2010-02-28
I'm using Ubuntu 9.10 Server for my django-based web site and I want to run memcached automatically when booting up, so I've put the following lines to rc.local:
```
python /home/webapp/bin/start_memcached.py site
python /home/webapp/bin/start_django.py site

exit 0

```

start_memcached.py is just a script that starts memcached:
```
from os import system
import sys
import settings

arg = sys.argv[1]
setting = settings.MEMCACHED_SETTINGS[arg]
command = 'memcached start -d -l %s -m %d -P %s/%s_memcached.pid -p %d' % \
        (setting['listen'], setting['memory'],settings.PATH, arg, setting['port'])

system(command)

print 'Started'

```

It just reads some configuration from settings based on some key (that's why I'm calling it with argument site).

Now the thing is that django is started automatically upon boot but memcached is not. If I run the start_memcached.py script manually, then it's ok. Does anybody have any suggestion how to solve this or where the problem may be?

---

