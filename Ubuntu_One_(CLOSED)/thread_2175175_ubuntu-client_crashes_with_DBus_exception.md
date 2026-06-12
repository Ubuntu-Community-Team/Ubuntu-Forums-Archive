---
title: "ubuntu-client crashes with DBus exception"
date: 2013-09-17
forum: Ubuntu One (CLOSED)
---

### Post by rszimm on 2013-09-17
Here's what happens:
[EMAIL="rzimmerman@hydra:~$"]rzimmerman@hydra:~$[/EMAIL] u1sdtool --start[INDENT]Traceback (most recent call last):
  File "/usr/bin/u1sdtool", line 39, in <module>
    bus = dbus.SessionBus(mainloop=loop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 211, in __new__
    mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 100, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 122, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-QN3U2Wb4O0: Connection refused[/INDENT]

It's client version 4.2.0 and Ubuntu 13.04.

dbus is running.  However, I get a similar error if I do this:[INDENT][EMAIL="rzimmerman@hydra:~$"]rzimmerman@hydra:~$[/EMAIL] dbus-monitor
Failed to open connection to session bus: Failed to connect to socket /tmp/dbus-QN3U2Wb4O0: Connection refused[/INDENT]

sudo dbus-monitor does work though... huh?
Now, oddly if I run sudo u1sdtool --start, I get the following:
[EMAIL="rzimmerman@hydra:~$"]rzimmerman@hydra:~$[/EMAIL] sudo u1sdtool --start
Oops, an error occurred:
org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

So what's happening here?  Seems like something odd is going on with dbus, but I don't know enough to be sure.

---

