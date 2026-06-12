---
title: "Ubuntu One not syncing and Folders keep crashing"
date: 2011-06-05
forum: Ubuntu One (CLOSED)
---

### Post by dr_crazy on 2011-06-05
Hi everyone, 

I'm experiencing some weird problems at the moment. After a restart, for some reason Ubuntu One isn't syncing and returns the error:

File Sync error. (org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

I'm connected to the internet fine, and I'm not using anything like proxies that could cause problem. I've tried following all the steps on [Ubuntu One Bugs Wiki]("https://wiki.ubuntu.com/UbuntuOne/Bugs") but nothing seems to have fixed the syncing issues.

Furthermore, after the restart, whenever I try to open any folders, such as Home via the taskbar or via the Places option on the toolbar, either the window opens then crashes, or it simply just doesn't open.

I'm currently using 11.04 Natty Narwhal and have been searching the forums for a couple of days now, and I don't know what it going on. Please help!

---

### Post by duanedesign on 2011-06-06
Do you have anything in the following file:

~/.cache/ubuntuone/log/syncdaemon-exceptions.log

thank you,
duanedesign

---

### Post by dr_crazy on 2011-06-10
This is what I found in the syncdaemon-exceptions.log:

2011-06-10 08:56:52,813 - ubuntuone.SyncDaemon - ERROR - Unexpected error
Traceback (most recent call last):
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 187, in <module>
    main(sys.argv)
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 136, in main
    ignore_files=options.ignore)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/main.py", line 100, in __init__
    self.db = tritcask.Tritcask(self.tritcask_dir)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 575, in __init__
    self._build_keydir()
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 695, in _build_keydir
    self._load_from_hint(data_file)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 711, in _load_from_hint
    for hint_entry in hint_file.iter_entries():
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 408, in iter_entries
    fmap = mmap.mmap(self.fd.fileno(), 0, access=mmap.ACCESS_READ)
ValueError: mmap offset is greater than file size

---

### Post by dr_crazy on 2011-06-10
Not sure if this will help, or maybe too much info, but i ran this script to see if this would help:

killall ubuntuone-syncdaemon; /usr/lib/ubuntuone-client/ubuntuone-syncdaemon --debug

The results are below:


2011-06-10 09:07:49,511 - ubuntuone.SyncDaemon.Main - INFO - Starting Ubuntu One client version 1.7
2011-06-10 09:07:49,512 - ubuntuone.SyncDaemon.tritcask - INFO - Initializing Tritcask on: /home/chris/.local/share/ubuntuone/syncdaemon/tritcask
2011-06-10 09:07:49,512 - ubuntuone.SyncDaemon.tritcask - DEBUG - lookingup data files
2011-06-10 09:07:49,513 - ubuntuone.SyncDaemon.tritcask - INFO - found 8 data files and 0 dead files
2011-06-10 09:07:49,515 - ubuntuone.SyncDaemon.tritcask - DEBUG - building the keydir, using: ['130684264459305', '130683665647195', '130693698173329', '130700663237004', '130696532901371', '130682834109833', '130682834087993']
2011-06-10 09:07:49,522 - ubuntuone.SyncDaemon.tritcask - DEBUG - loading entries from hint of: /home/chris/.local/share/ubuntuone/syncdaemon/tritcask/130682834087993.inactive.tritcask-v1.data
2011-06-10 09:07:49,544 - ubuntuone.SyncDaemon.tritcask - DEBUG - loading entries from hint of: /home/chris/.local/share/ubuntuone/syncdaemon/tritcask/130682834109833.inactive.tritcask-v1.data
2011-06-10 09:07:49,559 - ubuntuone.SyncDaemon.tritcask - DEBUG - loading entries from hint of: /home/chris/.local/share/ubuntuone/syncdaemon/tritcask/130683665647195.inactive.tritcask-v1.data
2011-06-10 09:07:49,562 - ubuntuone.SyncDaemon.tritcask - DEBUG - loading entries from hint of: /home/chris/.local/share/ubuntuone/syncdaemon/tritcask/130684264459305.inactive.tritcask-v1.data
2011-06-10 09:07:49,563 - ubuntuone.SyncDaemon.tritcask - DEBUG - loading entries from hint of: /home/chris/.local/share/ubuntuone/syncdaemon/tritcask/130693698173329.inactive.tritcask-v1.data
2011-06-10 09:07:49,563 - ubuntuone.SyncDaemon.tritcask - DEBUG - loading entries from hint of: /home/chris/.local/share/ubuntuone/syncdaemon/tritcask/130696532901371.inactive.tritcask-v1.data
2011-06-10 09:07:49,563 - ubuntuone.SyncDaemon.tritcask - DEBUG - loading entries from hint of: /home/chris/.local/share/ubuntuone/syncdaemon/tritcask/130700663237004.inactive.tritcask-v1.data
2011-06-10 09:07:49,566 - ubuntuone.SyncDaemon - ERROR - Unexpected error
Traceback (most recent call last):
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 187, in <module>
    main(sys.argv)
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 136, in main
    ignore_files=options.ignore)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/main.py", line 100, in __init__
    self.db = tritcask.Tritcask(self.tritcask_dir)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 575, in __init__
    self._build_keydir()
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 695, in _build_keydir
    self._load_from_hint(data_file)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 711, in _load_from_hint
    for hint_entry in hint_file.iter_entries():
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 408, in iter_entries
    fmap = mmap.mmap(self.fd.fileno(), 0, access=mmap.ACCESS_READ)
ValueError: mmap offset is greater than file size
Traceback (most recent call last):
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 187, in <module>
    main(sys.argv)
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 136, in main
    ignore_files=options.ignore)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/main.py", line 100, in __init__
    self.db = tritcask.Tritcask(self.tritcask_dir)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 575, in __init__
    self._build_keydir()
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 695, in _build_keydir
    self._load_from_hint(data_file)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 711, in _load_from_hint
    for hint_entry in hint_file.iter_entries():
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/tritcask.py", line 408, in iter_entries
    fmap = mmap.mmap(self.fd.fileno(), 0, access=mmap.ACCESS_READ)
ValueError: mmap offset is greater than file size

---

### Post by duanedesign on 2011-06-16
This is an odd error I have never seen before. I am trying to get in touch with one of the developers to help me sort this out.

---

