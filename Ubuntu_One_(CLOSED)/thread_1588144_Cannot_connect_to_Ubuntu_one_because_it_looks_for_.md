---
title: "Cannot connect to Ubuntu one because it looks for google chrome!"
date: 2010-10-04
forum: Ubuntu One (CLOSED)
---

### Post by jauntybluefish on 2010-10-04
Here are the relevant logs.

oauth-login.log
2010-10-04 19:24:50,369:369.256973267 ubuntuone-login Starting Ubuntu One login manager version 1.2.2
2010-10-04 19:24:55,671:671.637058258 ubuntuone-login Error showing URL: Failed to execute child process "/opt/google/chrome/google-chrome" (No such file or directory)

syncdaemon.log

2010-10-04 19:24:49,296 - ubuntuone.SyncDaemon.fsm - INFO - loading metadata from old version None
2010-10-04 19:24:49,297 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 0, idx_node_id: 0, shares: 0
2010-10-04 19:24:49,299 - ubuntuone.SyncDaemon.GeneralINotProc - INFO - Ignoring files: ['\\A#.*\\Z', '\\A.*~\\Z', '\\A.*\\.py[oc]\\Z', '\\A.*\\.sw[nopx]\\Z', '\\A.*\\.swpx\\Z', '\\A\\..*\\.tmp\\Z']
2010-10-04 19:24:49,319 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2010-10-04 19:24:51,066 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2010-10-04 19:24:51,066 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/andy/Ubuntu One' as root dir
2010-10-04 19:24:51,067 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/andy/.local/share/ubuntuone/syncdaemon' as data dir
2010-10-04 19:24:51,067 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/andy/.local/share/ubuntuone/shares' as shares root dir
2010-10-04 19:24:51,067 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'INIT'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=0 miss=0) ----
2010-10-04 19:24:51,067 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2010-10-04 19:24:51,068 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all volumes
2010-10-04 19:24:51,074 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2010-10-04 19:24:51,074 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2010-10-04 19:24:51,074 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2010-10-04 19:26:51,067 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=2 miss=1) ----
2010-10-04 19:28:51,067 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=2 miss=1) ----
2010-10-04 19:30:51,067 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=2 miss=1) ----
2010-10-04 19:32:51,067 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=2 miss=1) ----
2010-10-04 19:34:51,068 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=2 miss=1) ----

u1prefs.log

2010-10-04 19:24:47,981 - ubuntuone-preferences - DEBUG - starting
2010-10-04 19:24:51,092 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-10-04 19:24:55,666 - ubuntuone-preferences - ERROR - Error showing URL: Failed to execute child process "/opt/google/chrome/google-chrome" (No such file or directory)


How can I correct this please. I have 10.04 Lucid fresh clean install and i want to use firefox.

Thanks

---

### Post by jauntybluefish on 2010-10-05
Ok..heres the answer.
It turns out that Firefox was not set as my default browser. I discovered this because Thunderbird would not open links in my browser.

Setting another browser as default and then going to Firefox and doing the same cured the problem.
I can now connect to Ubuntu One.

Andy

---

### Post by duanedesign on 2010-10-06
Thank you for updating the thread with your solution. In case anyone reads this with a similar problem the default browser is set in:

> System -> Preferences -> Preferred Applications

~duanedesign

---

