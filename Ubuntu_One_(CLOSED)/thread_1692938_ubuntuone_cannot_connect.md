---
title: "ubuntuone cannot connect"
date: 2011-02-22
forum: Ubuntu One (CLOSED)
---

### Post by zensys on 2011-02-22
Ubuntuone worked a year ago but not anymore, due to an ill-tweaked system I thought. But yesterday I had to do a fresh 10.10 install (except for my home directory) and still no luck. I have an account, can log in via the web, and have a working internet connection. Below is what the ubuntuone-indicator says:

Apart from the below my main problem is that in Nautilus I cannot see the Ubuntuone options in my context menu.

Any suggestions are appreciated as I really like ubuntuone as a backup solution.

```
Initializing Application...
Initializing Indicator...
Initializing Client...
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/status: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/publicfiles: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
The call to DBus timed out
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/pymodules/python2.6/ubuntuone_indicator/__init__.py", line 226, in meta_queue_changed_handler
    self.meta_queue_changed_cb()
  File "/usr/bin/ubuntuone-indicator", line 187, in update_meta_queue_info
    cur_count = self.client.get_meta_queue_length()
  File "/usr/lib/pymodules/python2.6/ubuntuone_indicator/__init__.py", line 248, in get_meta_queue_length
    meta = self.status_if.waiting_metadata()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/dbus_interface.py", line 276, in waiting_metadata
    data['path'] = self._get_command_path(cmd)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/dbus_interface.py", line 251, in _get_command_path
    cmd.node_id).path
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/filesystem_manager.py", line 613, in get_by_node_id
    mdid = self._idx_node_id[(share_id, node_id)]
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/filesystem_manager.py", line 161, in __getitem__
    raise ValueError("The node_id can not be None")
ValueError: The node_id can not be None

ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/pymodules/python2.6/ubuntuone_indicator/__init__.py", line 182, in status_changed_handler
    self.status_changed_cb(info)
  File "/usr/bin/ubuntuone-indicator", line 273, in update_status_info
    self.initialize_queues()
  File "/usr/bin/ubuntuone-indicator", line 174, in initialize_queues
    self.metadata_count = self.client.get_meta_queue_length()
  File "/usr/lib/pymodules/python2.6/ubuntuone_indicator/__init__.py", line 247, in get_meta_queue_length
    if self.is_dbus_ready():
  File "/usr/lib/pymodules/python2.6/ubuntuone_indicator/__init__.py", line 238, in is_dbus_ready
    info = self.get_current_status()
  File "/usr/lib/pymodules/python2.6/ubuntuone_indicator/__init__.py", line 305, in get_current_status
    info = self.status_if.current_status()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
^CSegmentation fault

```

---

### Post by zensys on 2011-02-22
like when I go to the doctor my pain usually disappears, now my ubuntuone suddenly started working. Somehow installing the ubuntuone indicator got things going.

I am still interested to know however what all the error messages mean. Just to know if I can expect trouble ahead.

---

