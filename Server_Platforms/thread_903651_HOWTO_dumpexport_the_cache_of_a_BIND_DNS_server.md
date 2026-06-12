---
title: "HOWTO dump/export the cache of a BIND DNS server"
date: 2008-08-28
forum: Server Platforms
---

### Post by tdcdodger on 2008-08-28
Last night I spent about an hour looking around google for how to dump and view the cache of a bind dns server. I just wanted to post this thread on how to do it so maybe next time people search they will able to find it easier :-)

Bind 9 makes it fairly easy to dump and view the cache of a caching BIND DNS server. All you have to do is run under root:

rndc dumpdb -cache

This will create a file called named_dump.db in the /var/cache/bind/ directory. You can easily open this .db with your favorite text editor.

** If your instance of BIND is chrooted, for example to /var/lib/named/, then the cache dump file will be located in the /var/lib/named/var/cache/bind/ directory.

** The dumpdb feature of rndc has other options including a -all or -zone flag. Check 'rndc --help' for more information.

For more information you can check out this [HOWTO]("http://www.gritto.net/db/query.php?id=48&ty=HOWTO") i drafted.

---

