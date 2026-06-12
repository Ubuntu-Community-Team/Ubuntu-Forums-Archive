---
title: "waiting-metadata"
date: 2010-06-07
forum: Ubuntu One (CLOSED)
---

### Post by Dave Smith on 2010-06-07
I have just used the command:

*u1sdtool --waiting-metadata | wc -l *

... and received the following confusing (and I suspect unpleasant) response:

[I]Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Python.UnicodeEncodeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 204, in waiting_metadata
    waiting_metadata.append(str(cmd))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1442, in __str__
    for attr in str_attrs]
UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 26: ordinal not in range(128 )

2
[/I]
I have re-issued the command a number of times and get the same response with contents waiting to be synchronised gradually building up.

Does anyone know what this might mean? Will it clear itself if I leave it or is this something I have to do something about?

Thanks (as usual).

---

### Post by laoshi on 2010-06-08
This is a bug, which has already been reported - and work on it is apparently going on
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/557160]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/557160")
If you have a long list of files in the queue you will get the notification with different exceptions as a file with different characters out of range (accents and Danish characters like æ,ø,å).
But as far as I can see at the moment the files are synchronized all the same.

---

### Post by Dave Smith on 2010-06-08
Thanks for your observations. I'll keep an eye on this. I have some files in Spanish and so this could well be the cause.

---

