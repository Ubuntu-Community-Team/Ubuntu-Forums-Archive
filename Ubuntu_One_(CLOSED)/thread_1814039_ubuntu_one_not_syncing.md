---
title: "ubuntu one not syncing"
date: 2011-07-28
forum: Ubuntu One (CLOSED)
---

### Post by olegio on 2011-07-28
My ubuntu one is not working. I am using Ubuntu 10.04. 
I've included the error log file for sync. Any idea if this can be fixed?

```

u1sdtool -s

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

```

cat ~/.cache/ubuntuone/log/syncdaemon-exceptions.log
2011-07-28 10:29:23,077 - ubuntuone.SyncDaemon.sync - ERROR - T:NONE:F 20916284-3bf2-42bd-bc8a-d9aca5cd3c3e ['b09cbe82-e5c0-4ad5-b6a3-c88379e40905'::marker:20916284-3bf2-42bd-bc8a-d9aca5cd3c3e] ''zeprogs/\xbc\x12\xee\xb7\xbc\x12\xee\xb7'' | Executing ACTION_FUNC 'new_local_file' gave an exception: UnicodeDecodeError('utf8', '\xbc\x12\xee\xb7\xbc\x12\xee\xb7', 0, 1, 'unexpected code byte')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/fsm/fsm.py", line 137, in on_event
    af(event_name, parameters, *args)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/sync.py", line 635, in new_local_file
    self.m.action_q.make_file(share_id, parent_id, name, marker)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1053, in make_file
    name, marker).start()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1496, in __init__
    self.name = name.decode("utf8")
  File "/usr/lib/python2.6/encodings/utf_8.py", line 16, in decode
    return codecs.utf_8_decode(input, errors, True)
UnicodeDecodeError: 'utf8' codec can't decode byte 0xbc in position 0: unexpected code byte
2011-07-28 10:29:23,254 - ubuntuone.SyncDaemon.sync - ERROR - T:NONE:F f4cce570-a5d5-481b-aee0-63b3c3820b7b ['b09cbe82-e5c0-4ad5-b6a3-c88379e40905'::marker:f4cce570-a5d5-481b-aee0-63b3c3820b7b] ''zeprogs/jobshop/\xbc\xa2\xe2\xb7\xbc\xa2\xe2\xb7'' | Executing ACTION_FUNC 'new_local_file' gave an exception: UnicodeDecodeError('utf8', '\xbc\xa2\xe2\xb7\xbc\xa2\xe2\xb7', 0, 1, 'unexpected code byte')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/fsm/fsm.py", line 137, in on_event
    af(event_name, parameters, *args)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/sync.py", line 635, in new_local_file
    self.m.action_q.make_file(share_id, parent_id, name, marker)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1053, in make_file
    name, marker).start()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1496, in __init__
    self.name = name.decode("utf8")
  File "/usr/lib/python2.6/encodings/utf_8.py", line 16, in decode
    return codecs.utf_8_decode(input, errors, True)
UnicodeDecodeError: 'utf8' codec can't decode byte 0xbc in position 0: unexpected code byte
2011-07-28 10:31:25,262 - ubuntuone.SyncDaemon.sync - ERROR - T:NONE:F dd94bce5-f7e5-4e73-be07-08ef3abce092 ['15139049-b50b-4426-9531-028ac6ca28c3'::marker:dd94bce5-f7e5-4e73-be07-08ef3abce092] ''Short/\xe1\xaf\xa8\xe1\xae\xaa_\xe0\xa0\xa1\xae\xe2_\x98\xa8\xab\xae_\x82.\x8f.(edited_gt).doc'' | Executing ACTION_FUNC 'new_local_file' gave an exception: UnicodeDecodeError('utf8', '\xe1\xaf\xa8\xe1\xae\xaa_\xe0\xa0\xa1\xae\xe2_\x98\xa8\xab\xae_\x82.\x8f.(edited_gt).doc', 10, 11, 'unexpected code byte')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/fsm/fsm.py", line 137, in on_event
    af(event_name, parameters, *args)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/sync.py", line 635, in new_local_file
    self.m.action_q.make_file(share_id, parent_id, name, marker)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1053, in make_file
    name, marker).start()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/action_queue.py", line 1496, in __init__
    self.name = name.decode("utf8")
  File "/usr/lib/python2.6/encodings/utf_8.py", line 16, in decode
    return codecs.utf_8_decode(input, errors, True)
UnicodeDecodeError: 'utf8' codec can't decode byte 0xae in position 10: unexpected code byte
```

---

### Post by olegio on 2011-07-31
See below the response from the Ubuntu support. The problem is fixed after renaming the files provided by the script.
-------------------------------------------------------------------------------------------------------
It looks like some of your files have characters that are not utf8.

I have a script that you can run to identify these file names so you can change
them.
Use the following steps to download and run the script.

1. wget [http://people.canonical.com/~roman.yepishev/us/utf8-filename-check.py](http://people.canonical.com/~roman.yepishev/us/utf8-filename-check.py)

2. python utf8-filename-check.py /home/username/path/to/folder

Just replace /home/username/path/to/folder in step 2 with the path to the
folder you are syncing.

If you have anymore questions let me know.
Thank you,
Duane Hinnen

---

