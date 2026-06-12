---
title: "Ubuntu One doesn't launch/sync/ack my existence"
date: 2010-04-28
forum: Ubuntu One (CLOSED)
---

### Post by bryceowen on 2010-04-28
Just installed 10.04 and did all the updates this morning. Tried to connect to U1 and it would never give me the 'add this computer' option. I followed the instructions in [this]("http://ubuntuforums.org/showthread.php?t=1448624") post and it allowed me to add my computer (finally), but I wasn't able to actually sync anything (the U1 folder had a ! icon on it). When I tried to reopen the preferences, the 'starting ubuntuone' shows on the panel, but disappears after a few seconds. When I tried to launch ubuntuone-preferences in terminal, it spits out:
```
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 62, in <module>
    from desktopcouch.replication_services import ubuntuone as dcouch
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 20, in <module>
    from desktopcouch.start_local_couchdb import process_is_couchdb, read_pidfile
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 38, in <module>
    from desktopcouch import local_files
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 297, in <module>
    xdg_base_dirs.save_config_path("desktop-couch"))
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 237, in __init__
    self.configuration = _Configuration(self)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 65, in __init__
    self._fill_from_file(self.file_name_used)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 173, in _fill_from_file
    self._c.readfp(f)
  File "/usr/lib/python2.6/ConfigParser.py", line 305, in readfp
    self._read(fp, filename)
  File "/usr/lib/python2.6/ConfigParser.py", line 482, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/pspicer/.config/desktop-couch/desktop-couchdb.ini, line: 1
'\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00...(several thousand times)
```

I kinda rely on U1 and, while I can still get to my files through the web interface, it's highly inconvenient. Willing to try anything up to and including reinstalling Lucid.

--EDIT--
Found the source of my problem. The desktop-couchdb.ini file had a blank line for line 1 (filled with thousands of null characters). I deleted that line and tried to launch Ubuntu One again and it's working!

If only I had my tray icon. :(

--EDIT--
Oops. No, it isn't working. It connected to U1 long enough to get the directory structure, but none of the actual files.

So I stopped everything ubuntuone, removed ubuntuone-client and ubuntuone-client-gnome, deleted the U1 key under "Passwords and Encryption Keys", rebooted, reinstalled u1-client and u1-client-gnome and launched u1-preferences. It brought up Firefox to the U1 site, asking for my login. I logged it and it asked me to add this machine. So far, so good. That's when terminal started spitting out garbage:
```
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
ERROR:root:Starting couchdb failed on try 0
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 132, in run_couchdb
    raise RuntimeError("Can not start couchdb.")
RuntimeError: Can not start couchdb.
Apache CouchDB has started, time to relax.
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
ERROR:root:Unable to find file descriptors in /proc/2158
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2158/fd'
ERROR:root:Starting couchdb failed on try 1
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2158 exited.  Permissions?
Apache CouchDB has started, time to relax.
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
ERROR:root:Unable to find file descriptors in /proc/2349
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2349/fd'
ERROR:root:Starting couchdb failed on try 2
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2349 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/2491
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2491/fd'
ERROR:root:Starting couchdb failed on try 3
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2491 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/2591
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2591/fd'
ERROR:root:Starting couchdb failed on try 4
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2591 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
WARNING:root:Pid file does not contain int: ''
ERROR:root:Unable to find file descriptors in /proc/2792
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2792/fd'
ERROR:root:Starting couchdb failed on try 5
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2792 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/3092
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/3092/fd'
ERROR:root:Starting couchdb failed on try 6
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID3092 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/3292
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/3292/fd'
ERROR:root:Starting couchdb failed on try 7
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID3292 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/3392
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/3392/fd'
ERROR:root:Starting couchdb failed on try 8
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID3392 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/3492
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/3492/fd'
ERROR:root:Starting couchdb failed on try 9
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID3492 exited.  Permissions?
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/bin/ubuntuone-preferences", line 1083, in got_newcredentials
    self.present()
  File "/usr/bin/ubuntuone-preferences", line 1071, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 747, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 157, in __init__
    ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 53, in __init__
    port = desktopcouch.find_port(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 51, in find_port
    return _direct_access_find_port(pid=pid, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 75, in __find_port__linux
    pid = find_pid(start_if_not_running=True, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 35, in find_pid
    pid = start_local_couchdb.start_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 260, in start_couchdb
    raise saved_exception
RuntimeError: Couchdb PID3492 exited.  Permissions?
ERROR:ubuntuone-preferences:Invalid request token: 2HlfWccHSp7MfpcB4MjJ
ERROR:ubuntuone-preferences:Authorization was denied.

```
Getting frustrated...

---

### Post by bryceowen on 2010-04-28
Bump since editing doesn't bump the post.

---

### Post by cariboo on 2010-04-28
Moved to Ubuntu One. Please don't bump your thread until 24 hours has elapsed.

---

### Post by joshuahoover on 2010-04-29
> **bryceowen said:**
> 

--EDIT--
Oops. No, it isn't working. It connected to U1 long enough to get the directory structure, but none of the actual files.

So I stopped everything ubuntuone, removed ubuntuone-client and ubuntuone-client-gnome, deleted the U1 key under "Passwords and Encryption Keys", rebooted, reinstalled u1-client and u1-client-gnome and launched u1-preferences. It brought up Firefox to the U1 site, asking for my login. I logged it and it asked me to add this machine. So far, so good. That's when terminal started spitting out garbage:
```
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
ERROR:root:Starting couchdb failed on try 0
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 132, in run_couchdb
    raise RuntimeError("Can not start couchdb.")
RuntimeError: Can not start couchdb.
Apache CouchDB has started, time to relax.
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
ERROR:root:Unable to find file descriptors in /proc/2158
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2158/fd'
ERROR:root:Starting couchdb failed on try 1
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2158 exited.  Permissions?
Apache CouchDB has started, time to relax.
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
WARNING:root:Pid file does not contain int: '\n\n'
ERROR:root:Unable to find file descriptors in /proc/2349
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2349/fd'
ERROR:root:Starting couchdb failed on try 2
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2349 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/2491
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2491/fd'
ERROR:root:Starting couchdb failed on try 3
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2491 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/2591
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2591/fd'
ERROR:root:Starting couchdb failed on try 4
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2591 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
WARNING:root:Pid file does not contain int: ''
ERROR:root:Unable to find file descriptors in /proc/2792
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/2792/fd'
ERROR:root:Starting couchdb failed on try 5
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID2792 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/3092
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/3092/fd'
ERROR:root:Starting couchdb failed on try 6
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID3092 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/3292
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/3292/fd'
ERROR:root:Starting couchdb failed on try 7
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID3292 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/3392
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/3392/fd'
ERROR:root:Starting couchdb failed on try 8
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID3392 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/3492
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/3492/fd'
ERROR:root:Starting couchdb failed on try 9
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID3492 exited.  Permissions?
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/bin/ubuntuone-preferences", line 1083, in got_newcredentials
    self.present()
  File "/usr/bin/ubuntuone-preferences", line 1071, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 747, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 157, in __init__
    ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 53, in __init__
    port = desktopcouch.find_port(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 51, in find_port
    return _direct_access_find_port(pid=pid, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 75, in __find_port__linux
    pid = find_pid(start_if_not_running=True, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 35, in find_pid
    pid = start_local_couchdb.start_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 260, in start_couchdb
    raise saved_exception
RuntimeError: Couchdb PID3492 exited.  Permissions?
ERROR:ubuntuone-preferences:Invalid request token: 2HlfWccHSp7MfpcB4MjJ
ERROR:ubuntuone-preferences:Authorization was denied.

```Getting frustrated...

I'm sorry to hear Ubuntu One isn't working properly for you. Can you try a couple of things for me? In a terminal session run and report back the output:

apt-cache policy desktopcouch

Then try:

mv ~/.cache/desktop-couch/desktop-couchdb.pid ~/.cache/desktop-couch/desktop-couchdb.pid.old
killall ubuntuone-login ubuntuone-syncdaemon
ubuntuone-preferences

Thank you,

Joshua

---

### Post by bryceowen on 2010-04-29
Sorry, Joshua. I already reinstalled Lucid (mainly out of frustration). I'm still having problems, but that's in a different thread I'm watching. Thanks for the reply, however.

---

### Post by engineer on 2010-05-02
Same problem here! I already followed your steps and renamed the .pid file. That didn't help in any sense, ubuntuone-preferences crashed as soon as the window showed up.

I'm running Lucid, after upgrade from Karmic. Ubuntuone used to work some time ago in Karmic, I didn't use it recently, so I can't tell, if the update to Lucid broke it or not.

```
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/config: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:ubuntuone-preferences:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:ubuntuone-preferences:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/15353
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/15353/fd'
ERROR:root:Starting couchdb failed on try 0
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID15353 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/15571
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/15571/fd'
ERROR:root:Starting couchdb failed on try 1

```

---

### Post by danielsbrewer on 2010-06-01
I'm having exactly the same problem after upgrading to Lucid.  Did anyone get to the bottom of this?

---

### Post by engineer on 2010-07-07
Same here (I think since karmic times).
Unfortunately I didn't find any solution yet.

---

### Post by duanedesign on 2010-07-07
Could you please try the following.

Open a Terminal (Applications > Accessories > Terminal) and run the command:

```
killall beam.smp; killall beam
```

Then run the command:

```
rm ~/.config/desktop-couch/desktop-couchdb.ini
```
**NOTE:**this will remove the desktopcouch configuration file, which will then be re-generated. (This will not lose any data stored in desktopcouch, do not worry.) 

Then restart desktopcouch with the command:
```
dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort
```

Now to see if desktopcouch restarted correctly run the command which should then correctly take you to your desktopcouch web interface.
NOTE: replace [COLOR="Red"]YOURUSERNAME[/COLOR] with , well your username. Unless of course your username is username :)
```
xdg-open file:///home/[COLOR="Red"]YOURUSERNAME[/COLOR]/.local/share/desktop-couch/couchdb.html
```

You should see FUTON the couchDB interface.

---

