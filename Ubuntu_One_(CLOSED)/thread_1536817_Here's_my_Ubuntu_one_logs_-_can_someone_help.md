---
title: "Here's my Ubuntu one logs - can someone help?"
date: 2010-07-22
forum: Ubuntu One (CLOSED)
---

### Post by barrybevel on 2010-07-22
Hi,
  I can't get Ubuntu One working in 10.4 (fully updated)

I never connect according to "Ubuntu One Preferences"
I never have a key in "passwords & encryption keys"
I never see an add machine button

Here's the logs from ~/.cache/ubuntuone/log.

Can anyone make sense of them?

Thanks.

u1-prefs.log
============
2010-07-22 21:03:47,952 - ubuntuone-preferences - DEBUG - starting
2010-07-22 21:03:49,029 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-07-22 21:04:10,370 - ubuntuone-preferences - ERROR - Database enablement is unavailable.
2010-07-22 21:15:11,373 - ubuntuone-preferences - DEBUG - starting
2010-07-22 21:15:12,246 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-07-22 21:22:01,015 - ubuntuone-preferences - ERROR - Database enablement is unavailable.
2010-07-22 21:33:28,707 - ubuntuone-preferences - ERROR - org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/bin/ubuntuone-preferences", line 1072, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 748, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 167, in __init__
    raise ValueError("No pairing record for ubuntuone.")
ValueError: No pairing record for ubuntuone.

2010-07-22 21:34:12,455 - ubuntuone-preferences - DEBUG - starting
2010-07-22 21:34:12,497 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-07-22 21:35:03,511 - ubuntuone-preferences - ERROR - org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/bin/ubuntuone-preferences", line 1072, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 748, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 167, in __init__
    raise ValueError("No pairing record for ubuntuone.")
ValueError: No pairing record for ubuntuone.

2010-07-22 21:36:19,703 - ubuntuone-preferences - DEBUG - starting
2010-07-22 21:36:19,747 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-07-22 21:40:06,541 - ubuntuone-preferences - DEBUG - starting
2010-07-22 21:40:07,910 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-07-22 21:41:50,883 - ubuntuone-preferences - DEBUG - starting
2010-07-22 21:41:50,970 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-07-22 21:55:32,132 - ubuntuone-preferences - DEBUG - starting
2010-07-22 21:55:32,198 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-07-22 22:00:35,981 - ubuntuone-preferences - DEBUG - starting
2010-07-22 22:00:36,124 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-07-22 22:06:59,143 - ubuntuone-preferences - DEBUG - starting
2010-07-22 22:07:00,036 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))


syncdaemon.log
==============
2010-07-22 22:06:59,411 - ubuntuone.SyncDaemon.fsm - INFO - loading updated metadata
2010-07-22 22:06:59,411 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 1, idx_node_id: 0, shares: 1
2010-07-22 22:06:59,412 - ubuntuone.SyncDaemon.GeneralINotProc - INFO - Ignoring files: ['\\A#.*\\Z', '\\A.*~\\Z', '\\A.*\\.py[oc]\\Z', '\\A.*\\.sw[nopx]\\Z', '\\A.*\\.swpx\\Z', '\\A\\..*\\.tmp\\Z']
2010-07-22 22:06:59,414 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2010-07-22 22:07:00,027 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2010-07-22 22:07:00,027 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/barry/Ubuntu One' as root dir
2010-07-22 22:07:00,027 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/barry/.local/share/ubuntuone/syncdaemon' as data dir
2010-07-22 22:07:00,027 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/barry/.local/share/ubuntuone/shares' as shares root dir
2010-07-22 22:07:00,027 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'INIT'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1 miss=1) ----
2010-07-22 22:07:00,028 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2010-07-22 22:07:00,028 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all volumes
2010-07-22 22:07:00,029 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2010-07-22 22:07:00,029 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2010-07-22 22:07:00,030 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2010-07-22 22:09:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:11:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:13:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:15:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:17:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:19:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:21:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:23:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:25:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:27:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:29:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:31:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:33:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:35:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:37:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----
2010-07-22 22:39:00,028 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=4 miss=1) ----

oauth-login.log
================
2010-07-22 21:03:49,895:895.77794075 ubuntuone-login Starting Ubuntu One login manager version 1.2.2
2010-07-22 21:15:12,862:862.912893295 ubuntuone-login Starting Ubuntu One login manager version 1.2.2
2010-07-22 21:40:07,759:759.413003922 ubuntuone-login Starting Ubuntu One login manager version 1.2.2
2010-07-22 22:03:22,945:945.225954056 ubuntuone-login Starting Ubuntu One login manager version 1.2.2
2010-07-22 22:07:00,670:670.058012009 ubuntuone-login Starting Ubuntu One login manager version 1.2.2

---

### Post by barrybevel on 2010-07-22
I got it to connect....this may help someone in a similar situation:

I'm using a Vodafone Mobile Stick and the "Vodafone Mobile Connect" software from Betavine to connect to the Internet which works fine - but the network manager thinks it's disconnected - even though it's not.

So I closed the Vodafone Mobile Connect app and connected using the Network Manager and I once I did this - Ubuntu One connected with no problems :)

---

### Post by duanedesign on 2010-07-25
Thank you for updating the thread with your solution.

---

