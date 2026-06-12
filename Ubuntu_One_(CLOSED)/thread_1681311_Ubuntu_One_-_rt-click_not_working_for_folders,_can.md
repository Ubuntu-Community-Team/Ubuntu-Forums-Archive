---
title: "Ubuntu One - rt-click not working for folders, can't synch"
date: 2011-02-04
forum: Ubuntu One (CLOSED)
---

### Post by beaucoder on 2011-02-04
Ubuntu One - can't Synch Documents folders with right-click.

Using:  "u1sdtool --create-folder /home/beaucoder/Ubuntu" returns:
(as does any other create attempt) 

Oops, an error ocurred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 249, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 92, in parse_reply
    *message.get_args_list()))
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 307, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 354, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 371, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/bin/u1sdtool", line 111, in <lambda>
    d.addErrback(lambda r: show_error(r, out))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 764, in show_error
    raise error.value
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1

What has gone wrong here??

Thanks, Ken

---

