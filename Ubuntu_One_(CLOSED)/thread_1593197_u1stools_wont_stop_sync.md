---
title: "u1stools wont stop sync ?"
date: 2010-10-11
forum: Ubuntu One (CLOSED)
---

### Post by manco1911 on 2010-10-11
Hi all, 
I just suscribed to UbuntuOne, just as a backup plan to dropbox.
Still testing, but i cant seem to stop syncing a folder.

On right Click it shows that option grayed out. 

And if i follow JoshuaHoover link
[https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20~/Ubuntu%20One%20folder](https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20stop%20synchronizing%20a%20folder%20outside%20my%20~/Ubuntu%20One%20folder)

and try to do it with the following commands:
#u1sdtool --list-folders
#u1sdtool --unsubscribe-folder=ID-FROM-COMMAND-ABOVE 

it also wont cut it. (sudo also wont work), it actually spits a strange error:

[I]#sudo u1sdtool --unsubscribe-folder=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx

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
  File "/usr/bin/u1sdtool", line 123, in <lambda>
    d.addErrback(lambda r: show_error(r, out))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 764, in show_error
    raise error.value
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1[/I]


And, besides all this, i tryied to sync the whole DropBox folder, and it wont sync it, but it also wont list it as syncing nor let me "stop syncing" that folder ! :s

Any ideas ?

im running 10.04, just for you to know.

---

### Post by snowmann on 2010-10-11
to stop and start the sync, try this command in a terminal

```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

---

### Post by duanedesign on 2010-10-11
> and try to do it with the following commands:
#u1sdtool --list-folders
#u1sdtool --unsubscribe-folder=ID-FROM-COMMAND-ABOVE

it also wont cut it

After running u1sdtool --unsubscribe-folder, when you run u1sdtool --list-folders you should see subscribed=True change to subscribed=False

If you actually want to remove the folder from the server (without changing the local version) and remove it from --list-folders then run --delete-folder.

There is a good wiki page with lots of info on using u1sdtool [here]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl"). There is a section for removing a folder, before it is done syncing, that you have added to the queue


**NOTE:** it is not a good idea to run U1 or u1sdtool as sudo.

---

