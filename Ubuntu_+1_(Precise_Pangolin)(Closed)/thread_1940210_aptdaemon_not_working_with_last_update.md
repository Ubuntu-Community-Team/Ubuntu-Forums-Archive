---
title: "aptdaemon not working with last update"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sdowney717 on 2012-03-13
An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 249, in _process_transaction
    self.commit_packages(trans, *trans.packages)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 311, in commit_packages
    self._apply_changes(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/pkcompat.py", line 2831, in _apply_changes
    self._emit_require_restart(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/pkcompat.py", line 2157, in _emit_require_restart
    trans.pktrans.RequireRestart(pk_enums.RESTART_SYSTEM, "")
AttributeError: 'Transaction' object has no attribute 'pktrans'


so what are the ramifications of this?

Well so far nothing. I have not rebooted, but did relaunch it.

---

### Post by s4ms0e on 2012-03-15
^
^
|


Hi,

I had the same problem on my new ubuntu 12.04, is there anyone who know how to fix it.?
Or this module where not important.?

thank you
s4ms0e

---

### Post by screaminj3sus on 2012-03-15
I had the same issue last week. After that error appeared I had to enter my password every time I updated in updatemanager, even after rebooting.

Since then it did start working properly again though, and I did see an aptdaemon update come through recently.

> **s4ms0e said:**
> ^
^
|


Hi,

I had the same problem on my new ubuntu 12.04, is there anyone who know how to fix it.?
Or this module where not important.?

thank you
s4ms0e

afiak all aptdaemon really does is let you update without needing a password.

---

