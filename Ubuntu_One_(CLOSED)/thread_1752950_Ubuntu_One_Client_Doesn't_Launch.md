---
title: "Ubuntu One Client Doesn't Launch"
date: 2011-05-08
forum: Ubuntu One (CLOSED)
---

### Post by pisahmet on 2011-05-08
Hi,

I was using 10.10 AMD64. I've upgraded it to Natty. But i had many problems with upgraded system. So i formatted disk and made a fresh installation (AMD64).

While using 10.10, i couldn't use Ubuntu One. Because the client never launched. It was giving this error on console:

```
Traceback (most recent call last):
  File "/usr/bin/u1sdtool", line 33, in <module>
    from ubuntuone.platform.linux.tools import (
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/tools.py", line 24, in <module>
    from ubuntuone.platform.linux.dbus_interface import (
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 32, in <module>
    from ubuntuone.syncdaemon.interaction_interfaces import (
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 24, in <module>
    from ubuntuone.syncdaemon.action_queue import Download, Upload
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/action_queue.py", line 29, in <module>
    import simplejson
  File "/usr/lib/python2.7/dist-packages/simplejson/__init__.py", line 109, in <module>
    from decimal import Decimal
  File "/usr/lib/python2.7/decimal.py", line 3715, in <module>
    val = globals()[globalname]
KeyError: 'ROUND_CEiLiNG'

```

Now i'm using normally installed Natty. But Ubuntu One client still gives same error.

How can i solve this problem?

---

### Post by duanedesign on 2011-05-10
hello pisahmet,
Are you using a Turkish Locale? Looks like you might be affected by [bug 467397]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/467397"). This is a bug in python. See the bug for a possible workaround.

thank you,
duanedesign

---

### Post by pisahmet on 2011-05-11
Yeah, thanks for that bug report page.

I found a solution in that page. Says that we must set another locale for only Ubuntu One, with this command:

```
env LC_ALL=en_US.UTF-8 ubuntuone-client-applet
```

But when i try that, it says that "**ubuntuone-client-applet**" file doesn't exist.

---

