---
title: "U1 useless after update"
date: 2011-10-24
forum: Ubuntu One (CLOSED)
---

### Post by Neon612 on 2011-10-24
U1 was working fine just before the last update I ran (last weekend). Now, when I try to connect, open ubuntuone-preferences, magicicada, etc. all I'm given is python error trace

```
ubuntuone-preferences 

Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 38, in <module>
    from ubuntuone.syncdaemon.tools import SyncDaemonTool
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 24, in <module>
    from ubuntuone.syncdaemon.dbus_interface import (
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 34, in <module>
    from ubuntuone.syncdaemon import config
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/config.py", line 28, in <module>
    from configglue import TypedConfigParser, glue
ImportError: cannot import name TypedConfigParser
```

I'm not entirely sure what was updated, but I did find out I had a weird version string for one of the desktopcouch packages. I reinstalled that and believe it is working now.

I've tried the reset desktopcouch stuff. Removing the ini file and running the dbus command to restart couch but the html file says DesktopCouch not started (or something similar).

I've also tried reinstalling U1 itself with no luck. I'm using Lucid if that makes a difference.

Thanks.

---

