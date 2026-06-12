---
title: "ubuntu one won't start"
date: 2010-10-26
forum: Ubuntu One (CLOSED)
---

### Post by xealous on 2010-10-26
when i run ubuntuone-preferences i get this error

```
xealous@xealous-1001p:~$ ubuntuone-preferences 
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 65, in <module>
    from desktopcouch.replication_services import ubuntuone as dcouch
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/__init__.py", line 3, in <module>
    import ubuntuone
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 10, in <module>
    import simplejson as json
  File "/usr/lib/pymodules/python2.6/simplejson/__init__.py", line 109, in <module>
    from decimal import Decimal
  File "/usr/lib/python2.6/decimal.py", line 3649, in <module>
    val = globals()[globalname]
KeyError: 'ROUND_CEiLiNG'

```

can you please help me to fix this :)

---

