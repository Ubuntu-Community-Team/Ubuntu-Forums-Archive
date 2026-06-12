---
title: "problem with http-replicator and /bin/sh on 6.10"
date: 2007-01-31
forum: Server Platforms
---

### Post by otaviofcs on 2007-01-31
Hy all,

I have installed a http-replicator on a 5.10 server and a 6.06 server. Both were running very well (the 6.06 is still running).

Now I have, slowly, started to prepare the upgrade to the 6.10 version. Today I've tried to run the http-replicator on that machine and the problem is that the sh shell isn't recognizing the source command. So the daemon does not work. To help you help me I've putted the lines with errors above:

```
#! /bin/sh

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/http-replicator
NAME=http-replicator
DESC="HTTP Proxy"

if [ -x $DAEMON ] && [ -f /etc/default/$NAME ] ; then
        source /etc/default/$NAME      <-LINE WITH ERROR
else
        exit 0
fi

set -e
...
```

It gives me the error: "source: not found". For the record only I have the file /etc/default/http-replicator placed in the right local and it has the right content:

```
# Defaults for http-replicator initscript
# sourced by /etc/init.d/http-replicator and /etc/cron.weekly/http-replicator
# installed at /etc/default/http-replicator by the maintainer scripts

#
# This is a POSIX shell fragment
#

#exit 0 # REMOVE THIS LINE TO ACTIVATE THE PROXY SERVER

# Options that apply to all programs
GENERAL_OPTS="--dir /var/cache/http-replicator"

# Additional options that are passed to the daemon
DAEMON_OPTS="$GENERAL_OPTS --port 8181 --log /var/log/http-replicator.log --user proxy --ip 192.168.0.*"

# Additional options that are passed to the maintenance script.
MAINTENANCE_OPTS="$GENERAL_OPTS --keep 1"
```

If I put the variables GENERAL_OPTS, ... from that file replacing the source line it works well.

Any Ideas in how to change the /bin/sh shell so it starts working like the 6.06, 5.10 versions?

thanks,

otávio

---

### Post by otaviofcs on 2007-01-31
As a matter of fact it is a /bin/sh problem in the 6.10 version....

---

### Post by otaviofcs on 2007-01-31
I understood the problem. In the 6.10 version the /bin/sh is an aliase of /bin/dash and the 6.06 version its an aliase of /bin/bash.

So I've changed my file to #!/bin/sh.distrib and it's working nice.:)

---

