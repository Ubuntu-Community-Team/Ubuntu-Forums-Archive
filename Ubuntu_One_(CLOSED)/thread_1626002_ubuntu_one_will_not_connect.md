---
title: "ubuntu one will not connect"
date: 2010-11-19
forum: Ubuntu One (CLOSED)
---

### Post by rcrath on 2010-11-19
Hi, 
I am running Ubuntu one on 10.10.  My desktop couch has gotten messed up and will not start, and this in turn prevents ubuntu one from connecting. 

```
u1sdtool --start
```
yields:
```
Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1
```


 I have tried purging desktop couch and ubuntu one, deleting the ubuntu one key, and then reinstalling, but with no luck.  I have a [bug report filed]("https://bugs.launchpad.net/desktopcouch/+bug/674396") with desktop couch, but I don't think anyone has looked at it yet.  I think it might be a permissions problem somewhere from either starting or killing desktop couch from root, but I don't know where.  

```
[~]$python ubuntuone-client-diagnose.py
Checking your Ubuntu One client...
Traceback (most recent call last):
  File "ubuntuone-client-diagnose.py", line 663, in <module>
    main(list_bugs)
  File "ubuntuone-client-diagnose.py", line 620, in main
    bug_found = bug.detect()
  File "ubuntuone-client-diagnose.py", line 262, in detect
    connect = int(appcfg.get("ubuntuone", "connect"))
TypeError: int() argument must be a string or a number, not 'NoneType'

```

Any ideas what I might do to get ubuntuone started?

---

### Post by rcrath on 2010-11-22
bump...

---

### Post by rcrath on 2010-12-07
ANyone??

---

### Post by duanedesign on 2010-12-08
rcrath,
sorry I did not see your thread sooner. I have a bad habit of only looking for threads with 0 replies.

OK your issue. Lets look at the log files. Could you open a Terminal and run this command:

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log
```

If the file is not empty could you please post the contents. (Please enclose the text the CODE tags. You can get them easily in the Forum Post editor by clicking the hash(#) button.)

If that file is empty could you run this command and post the contents of the file:

```
gedit ~/.cache/ubuntuone/log/syncdaemon.log
```

Some of the errors do look like it might be a permission problem. Ubuntu One does not like to be run as root and Ubuntu One uses the per user session of couchDB not the (root)system-wide one.

thank you,
duanedesign

---

### Post by mcmillanje on 2010-12-13
Same issue here... my sync daemon starts but no joy in connecting. here's my log.

```


2010-12-12 21:26:08,906 - ubuntuone.SyncDaemon.local_rescan - ERROR - in the scan: <type 'exceptions.AttributeError'> ('NoneType' object has no attribute 'st_ino')
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 333, in _scan_tree
    d.addCallbacks(self._scan_one_dir)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 249, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 441, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 675, in _scan_one_dir
    d = defer.execute(scan)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 96, in execute
    result = callable(*args, **kw)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 635, in scan
    share)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 486, in _compare
    different = self.check_stat(fullname, statinfo)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 363, in check_stat
    different = (newstat.st_ino != oldstat.st_ino or
exceptions.AttributeError: 'NoneType' object has no attribute 'st_ino'

2010-12-12 21:26:08,907 - twisted - ERROR - Unhandled error in Deferred:
2010-12-12 21:26:08,907 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 333, in _scan_tree
    d.addCallbacks(self._scan_one_dir)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 249, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 441, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 675, in _scan_one_dir
    d = defer.execute(scan)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 96, in execute
    result = callable(*args, **kw)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 635, in scan
    share)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 486, in _compare
    different = self.check_stat(fullname, statinfo)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 363, in check_stat
    different = (newstat.st_ino != oldstat.st_ino or
exceptions.AttributeError: 'NoneType' object has no attribute 'st_ino'

```


was i premature in purchasing additional space?

---

### Post by Jeff.wrenn on 2010-12-18
I'm on 10.10 with three computers.  2 log on to Ubuntu one, the third will not even log in.  I do have an account.  Log using: gedit ~/.cache/ubuntuone/log/syncdaemon.log.  Help.

2010-12-18 08:39:07,270 - ubuntuone.SyncDaemon.fsm - INFO - loading updated metadata
2010-12-18 08:39:07,270 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 1, idx_node_id: 0, shares: 1
2010-12-18 08:39:07,271 - ubuntuone.SyncDaemon.GeneralINotProc - INFO - Ignoring files: ['\\A#.*\\Z', '\\A.*~\\Z', '\\A.*\\.py[oc]\\Z', '\\A.*\\.sw[nopx]\\Z', '\\A.*\\.swpx\\Z', '\\A\\..*\\.tmp\\Z']
2010-12-18 08:39:07,272 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2010-12-18 08:39:07,867 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2010-12-18 08:39:07,867 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/jeff/Ubuntu One' as root dir
2010-12-18 08:39:07,867 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/jeff/.local/share/ubuntuone/syncdaemon' as data dir
2010-12-18 08:39:07,867 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/jeff/.local/share/ubuntuone/shares' as shares root dir
2010-12-18 08:39:07,868 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'INIT'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1 miss=1) ----
2010-12-18 08:39:07,868 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2010-12-18 08:39:07,868 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all volumes
2010-12-18 08:39:07,868 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2010-12-18 08:39:07,869 - ubuntuone.SyncDaemon.local_rescan - INFO - processing move limbo
2010-12-18 08:39:07,870 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2010-12-18 08:39:07,870 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2010-12-18 08:41:07,868 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2010-12-18 08:43:07,868 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2010-12-18 08:45:07,868 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----

---

### Post by duanedesign on 2010-12-18
> **mcmillanje said:**
> Same issue here... my sync daemon starts but no joy in connecting. here's my log.

```


2010-12-12 21:26:08,906 - ubuntuone.SyncDaemon.local_rescan - ERROR - in the scan: <type 'exceptions.AttributeError'> ('NoneType' object has no attribute 'st_ino')
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 333, in _scan_tree
    d.addCallbacks(self._scan_one_dir)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 249, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 441, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 675, in _scan_one_dir
    d = defer.execute(scan)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 96, in execute
    result = callable(*args, **kw)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 635, in scan
    share)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 486, in _compare
    different = self.check_stat(fullname, statinfo)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 363, in check_stat
    different = (newstat.st_ino != oldstat.st_ino or
exceptions.AttributeError: 'NoneType' object has no attribute 'st_ino'

2010-12-12 21:26:08,907 - twisted - ERROR - Unhandled error in Deferred:
2010-12-12 21:26:08,907 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 333, in _scan_tree
    d.addCallbacks(self._scan_one_dir)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 249, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 441, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 675, in _scan_one_dir
    d = defer.execute(scan)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 96, in execute
    result = callable(*args, **kw)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 635, in scan
    share)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 486, in _compare
    different = self.check_stat(fullname, statinfo)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/local_rescan.py", line 363, in check_stat
    different = (newstat.st_ino != oldstat.st_ino or
exceptions.AttributeError: 'NoneType' object has no attribute 'st_ino'

```


was i premature in purchasing additional space?

[Here is the bug report]("https://bugs.launchpad.net/ubuntuone-client/stable-1-4/+bug/665360") on your issue. I am looking for a workaround. You might subscribe to the bug in the meantime to keep current on its status.
-
-
-

---

### Post by duanedesign on 2010-12-18
> **Jeff.wrenn said:**
> I'm on 10.10 with three computers.  2 log on to Ubuntu one, the third will not even log in.  I do have an account.  Log using: gedit ~/.cache/ubuntuone/log/syncdaemon.log.  Help.

 MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----

On this machine it is in the Ready state but not connected. Could you run this command:

```
u1sdtool -c
```

then wait about a minute and run this command and post the output:

```
u1sdtool -s
```

---

### Post by Jeff.wrenn on 2010-12-24
tried to run:  
jeff@jeff-Vostro-220-Series:~$ ulsdtool -s
No command 'ulsdtool' found, did you mean:
 Command 'u1sdtool' from package 'ubuntuone-client' (main)
ulsdtool: command not found


got this response.

---

### Post by Jeff.wrenn on 2010-12-24
ran it with a 1 (one) instead of an l, go this response:

jeff@jeff-Vostro-220-Series:~$ u1sdtool -s
State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: IDLE

---

### Post by owise1 on 2011-03-04
I have the same problem as rcrath.

I get the same error message when using the u1sdtool command

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1

My problem I think occurred on this machine - newly upgraded from an old SUSE install to ubuntu 10.10.  Just after starting ubuntu one to sync with files on anther of my PCs I remembered that I was syncing a very large picture directory that would exceed my 2G allowance so I clicked off the share files tickbox.  Should have disconnected first??  Now it appears that ubuntuone-syncdaemon is not running and trying to start it gives that lovely oops message

---

### Post by duanedesign on 2011-03-14
Can you try opening the Terminal and starting the syncdaemon manually with this command and post the output:

```
/usr/lib/ubuntuone-client/ubuntuone-syncdaemon
```

thank you,
duanedesign

---

### Post by Kelvari on 2011-03-15
Also struggling with the same problem.

Output from /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
```

2011-03-15 22:21:38,224 - ubuntuone.SyncDaemon - ERROR - Unexpected error
Traceback (most recent call last):
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 185, in <module>
    main(sys.argv)
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 134, in main
    ignore_files=options.ignore)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/main.py", line 98, in __init__
    self.vm = volume_manager.VolumeManager(self)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/volume_manager.py", line 346, in __init__
    md_upgrader.upgrade_metadata()
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/volume_manager.py", line 1297, in upgrade_metadata
    self.md_version)
AttributeError: 'MetadataUpgrader' object has no attribute '_upgrade_metadata_7'

```

u1sdtool -c and u1sdtool -s both give the following
```

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1

```

---

### Post by alphaG33k on 2011-04-03
I'm having the same issue on my laptop (Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1)

```
2011-04-03 17:51:39,757 - ubuntuone.SyncDaemon.fsm - INFO - loading updated metadata
2011-04-03 17:51:39,759 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 1, idx_node_id: 0, shares: 1
2011-04-03 17:51:39,760 - ubuntuone.SyncDaemon.GeneralINotProc - INFO - Ignoring files: ['\\A#.*\\Z', '\\A.*~\\Z', '\\A.*\\.py[oc]\\Z', '\\A.*\\.sw[nopx]\\Z', '\\A.*\\.swpx\\Z', '\\A\\..*\\.tmp\\Z']
2011-04-03 17:51:39,764 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2011-04-03 17:51:40,741 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2011-04-03 17:51:40,741 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/bashquandry/Ubuntu One' as root dir
2011-04-03 17:51:40,741 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/bashquandry/.local/share/ubuntuone/syncdaemon' as data dir
2011-04-03 17:51:40,742 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/bashquandry/.local/share/ubuntuone/shares' as shares root dir
2011-04-03 17:51:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'INIT'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1 miss=1) ----
2011-04-03 17:51:40,742 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2011-04-03 17:51:40,742 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all volumes
2011-04-03 17:51:40,743 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2011-04-03 17:51:40,743 - ubuntuone.SyncDaemon.local_rescan - INFO - processing move limbo
2011-04-03 17:51:40,745 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2011-04-03 17:51:40,745 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2011-04-03 17:51:45,534 - ubuntuone.SyncDaemon.DBus - INFO - u'CredentialsFound': callbacking with credentials (token_name: None).
2011-04-03 17:51:45,535 - ubuntuone.SyncDaemon.DBus - INFO - connect: credential request was successful, pushing SYS_USER_CONNECT.
2011-04-03 17:51:45,580 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-04-03 17:51:45,995 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-04-03 17:51:45,996 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-04-03 17:51:46,604 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-04-03 17:51:46,814 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-04-03 17:51:47,014 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-04-03 17:51:47,637 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'oauth_authenticate' failed with the error: AUTHENTICATION_FAILED and was handled with the event: SYS_AUTH_ERROR
2011-04-03 17:53:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 17:55:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 17:57:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 17:58:47,646 - ubuntuone.SyncDaemon - WARNING - Please don't run the syncdaemon as root.
2011-04-03 17:58:48,119 - ubuntuone.SyncDaemon - WARNING - Please don't run the syncdaemon as root.
2011-04-03 17:59:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:01:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:03:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:05:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:07:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:09:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:11:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:13:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:15:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:17:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:19:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:21:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:23:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:25:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:27:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:29:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
2011-04-03 18:31:40,742 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=5 miss=1) ----
```

---

### Post by alphaG33k on 2011-04-04
I purged the password and did u1sdtool -q; u1sdtool -c
It still says it is disconnected, although it did register my computer on the one.ubuntu.com site, and the error I get with u1sdtool --status is differnt. Now it says 

State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

Here's the current log
```
2011-04-04 03:13:11,902 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-04-04 03:13:11,996 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-04-04 03:13:11,996 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-04-04 03:13:12,253 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-04-04 03:13:12,327 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-04-04 03:13:12,402 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-04-04 03:13:12,823 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'oauth_authenticate' failed with the error: AUTHENTICATION_FAILED and was handled with the event: SYS_AUTH_ERROR
2011-04-04 03:15:09,088 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 197; content: 1198; hash: 0, fsm-cache: hit=20703 miss=3738) ----
2011-04-04 03:17:09,088 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 197; content: 1198; hash: 0, fsm-cache: hit=20703 miss=3738) ----
2011-04-04 03:19:09,088 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 197; content: 1198; hash: 0, fsm-cache: hit=20703 miss=3738) ----
```

---

### Post by duanedesign on 2011-04-06
> **Kelvari said:**
> Also struggling with the same problem.

Output from /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
```

2011-03-15 22:21:38,224 - ubuntuone.SyncDaemon - ERROR - Unexpected error
Traceback (most recent call last):
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 185, in <module>
    main(sys.argv)
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 134, in main
    ignore_files=options.ignore)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/main.py", line 98, in __init__
    self.vm = volume_manager.VolumeManager(self)
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/volume_manager.py", line 346, in __init__
    md_upgrader.upgrade_metadata()
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/volume_manager.py", line 1297, in upgrade_metadata
    self.md_version)
AttributeError: 'MetadataUpgrader' object has no attribute '_upgrade_metadata_7'

```

u1sdtool -c and u1sdtool -s both give the following
```

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1

```

Your issue is that you updated to a newer version of Ubuntu One and then reverted to an older version. Your metadata  is out of sync. To fix follow these steps:

1. Quit the Ubuntu One client. From the applet select Quit. Then open a Terminal (Applications > Accessories > Terminal) and run the following to quit the syncdaemon.

u1sdtool -q

2. Delete the old metadata. In a Terminal run.

rm -rf ~/.local/share/ubuntuone

3. Start Ubuntu One as you normally would Applications > Internet > Ubuntu One. It will take a while as your metadata updates.

---

### Post by duanedesign on 2011-04-06
> **alphaG33k said:**
> I purged the password and did u1sdtool -q; u1sdtool -c
It still says it is disconnected, although it did register my computer on the one.ubuntu.com site, and the error I get with u1sdtool --status is differnt. Now it says

State: AUTH_FAILED
connection: With User With Network
description: auth failed
is_connected: False
is_error: True
is_online: False
queues: WORKING_ON_BOTH



When you say purged the password, does that mean you cleared the token?


   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Open Applications->Internet->Ubuntu One
   6. a web page(or dialog) should open, prompting you to add your computer to your Ubuntu One account
  7. Add your computer

---

### Post by Br11 on 2011-11-14
I have the same problem, I also tried this:
[http://askubuntu.com/questions/42065/file-sync-error-with-ubuntu-one](http://askubuntu.com/questions/42065/file-sync-error-with-ubuntu-one)

my u1sdtool --status says:

State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: IDLE

Thanks!

---

### Post by Br11 on 2011-11-14
Ok, I found the solution somewhere in this forum, sorry I cant find 
 the post to give credit but it`s just that the time of my computer wasn't being updated from internet

---

### Post by AnttiT on 2012-01-05
It was the clock for me too. My time was some 15 minutes early and after fixing the AUTH issue got lost. Now I'm facing some SSL issue, though, but that's another story :(

---

### Post by bart.a on 2013-01-31
Did you all solve your problems already? If not, who used an ssh server to make the syncdaemon.conf file?

I used notepad to copy the cccc:dddd part of authentication hash from the terminal to windows and back to the .conf file, and all seemed oké. But it wouldn't connect.
Then when I looked at the output of /usr/lib/ubuntuone-client/ubuntuone-syncdaemon I got an error and I there was a "\n"
that is hidden when I edit the .conf file.

Solution. I deleted the .conf file. made new .conf file.
Retyped (by hand) the cccc:dddd part of the hash. Tried it again and, problem solved.
Now it works like a charm..

I don't know if this helps anyone (after this long time) but wanted to try anyway..

---

