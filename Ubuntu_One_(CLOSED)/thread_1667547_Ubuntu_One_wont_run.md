---
title: "Ubuntu One wont run"
date: 2011-01-15
forum: Ubuntu One (CLOSED)
---

### Post by Archmage on 2011-01-15
Ubuntu 10.04 (LTS):

Ubuntu One did create the folder and allow me to make an account and add the PC.

However it isn't running and the status gives me something I don't understand at all:

```
u1sdtool -s
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 396, in fireEvent
    DeferredList(beforeResults).addCallback(self._continueFiring)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 224, in addCallback
    callbackKeywords=kw)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 213, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 371, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 409, in _continueFiring
    callable(*args, **kwargs)
  File "/usr/bin/u1sdtool", line 53, in main
    bus = dbus.SessionBus(mainloop=loop)
  File "/usr/lib/pymodules/python2.6/dbus/_dbus.py", line 219, in __new__
    mainloop=mainloop)
  File "/usr/lib/pymodules/python2.6/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-qyo9cJHz12: Connection refused

```

---

### Post by Pepe Lebuntu on 2011-01-24
I am SOOO sick of this!

Ubuntu One is a paid service, and it NEVER runs properly. It's constantly refusing to connect. It's ridiculously slow. Its services are limited especially when compared to equivalents like Dropbox. I don't mind having to put up with some things in Ubuntu's OS, because it's not a paid service. But when I'm paying for something, I expect it to work.

---

