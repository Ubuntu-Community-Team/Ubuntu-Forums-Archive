---
title: "Problems with corrupt folders"
date: 2011-01-25
forum: Ubuntu One (CLOSED)
---

### Post by Peter09 on 2011-01-25
Some weeks ago something happened which caused UbuntuOne on my four connected machines to get really confused. Now nautilus is crashing whenever the syncdemon is running on two of my machines.

Using ulsdtool I find

> u1sdtool --list-folders
Folder list:
  id=e42f243b-5b12-4f45-a76c-0ef8e07cecd7 subscribed=False path=/home/peter/Documents
  id=471858ba-1695-4804-b6d0-76e0f23774f3 subscribed=False path=/home/peter/Documents


I only have one folder of that name....

using 
> u1sdtool --delete-folder=471858ba-1695-4804-b6d0-76e0f23774f3

just hangs

Thought I would try the same command with sudo

> Oops, an error ocurred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 270, in run
    self.__run()
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/tools.py", line 92, in parse_reply
    *message.get_args_list()))
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 345, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 424, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 441, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/bin/u1sdtool", line 118, in <lambda>
    d.addErrback(lambda r: show_error(r, out))
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/tools.py", line 794, in show_error
    raise error.value
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1


Any suggestions?

---

### Post by duanedesign on 2011-02-03
Could you please open a terminal and try the following command:

```
u1sdtool --refresh-folders
```

then try the --list-folders and see if you still see two of the same folder. 

**NOTE:** ubuntu one doesn't like to be run as root so do not use sudo with u1sdtool.

thank you,
duanedesign

---

### Post by Peter09 on 2011-02-05
there is no --refresh-folders option to the command.

---

