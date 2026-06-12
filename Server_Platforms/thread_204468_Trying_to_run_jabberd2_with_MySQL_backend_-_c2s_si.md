---
title: "Trying to run jabberd2 with MySQL backend - c2s silently fails to start"
date: 2006-06-27
forum: Server Platforms
---

### Post by starkruzr on 2006-06-27
The above pretty much sums it up.  Ran fine when I hadn't changed anything in any of the config files, but if I change them according to the jabberd2 docs for mysql authentication and storage, c2s simply doesn't run.

Anyone have experience with this package and have suggestions how to make it work correctly?  I'm on Dapper, naturally.

---

### Post by starkruzr on 2006-06-27
::bump::

Help?

---

### Post by lamego on 2006-06-27
Have you checked the log files ?
The last time I had a problem with jabberd I had to trace it using strace.

---

### Post by starkruzr on 2006-06-27
::headdesk::

I can't believe I didn't remember to check the logs.  Here I am all "c2s -D... ARGH!  NOTHING!"

This is any example of what it does.
```

Tue Jun 27 02:40:06 2006 [notice] starting up
Tue Jun 27 02:40:06 2006 [info] process id is 19694, written to /var/run/jabber/c2s.pid
Tue Jun 27 02:40:06 2006 [notice] initialised auth module 'mysql'
Tue Jun 27 02:40:06 2006 [notice] [localhost] configured; realm=(null)
Tue Jun 27 02:40:06 2006 [notice] attempting connection to router at 127.0.0.1, port=5347
Tue Jun 27 02:40:06 2006 [notice] connection to router established
Tue Jun 27 02:40:06 2006 [error] router refused bind request (409)
```

Any idea what that means?

---

