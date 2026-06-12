---
title: "Ubuntu One connecting/disconnecting on Natty"
date: 2011-03-18
forum: Ubuntu One (CLOSED)
---

### Post by r-senior on 2011-03-18
First of all, a disclaimer: This is a Natty test machine and there is already a thread in Natty Testing and Discussion where I and at least one other have this problem. I'm looking for advice really - trying to work out whether there are sync problems with other releases and/or whether I should file a bug report against Natty.

As I started typing this I've had about four notifications from Ubuntu One that it is connected, then disconnected, then connected and so on. My Ubuntu One client shows "Sync in progress". It seems like it's stuck in a connect/disconnect loop. Tomboy Notes sync appears to be working but file sync does not.

I've stopped the sync daemon and deleted ~/.cache/ubuntuone and ~/.local/share/ubuntuone. Restarted and these notifications are still going on. Every 30 seconds or so (I've not timed it).

Log files in ~/.cache/ubuntuone/log contain:

*credentials.log*
```

2011-03-18 12:40:55,034 - ubuntuone.credentials - INFO - Starting Ubuntu One login manager for bus 'com.ubuntuone.Credentials'.
2011-03-18 12:40:55,040 - ubuntuone.credentials - DEBUG - ref_count is 0, changing value to 1.
2011-03-18 12:40:55,574 - ubuntuone.credentials - DEBUG - Handling DBus signal for member: 'CredentialsFound', app_name: dbus.String(u'Ubuntu One').
2011-03-18 12:40:55,575 - ubuntuone.credentials - INFO - 'CredentialsFound'
2011-03-18 12:40:55,575 - ubuntuone.credentials - DEBUG - ref_count is 1, changing value to 0.
2011-03-18 12:40:55,575 - ubuntuone.credentials - DEBUG - Setting up timer with <built-in function timeout_add> (10000, <bound method CredentialsManagement.shutdown of <ubuntuone.platform.linux.credentials.CredentialsManagement at /credentials at 0x27f3d50>>).
2011-03-18 12:40:55,575 - ubuntuone.credentials - INFO - CredentialsManagement: emitting CredentialsFound.
2011-03-18 12:41:05,583 - ubuntuone.credentials - DEBUG - shutdown!, ref_count is 0.
2011-03-18 12:41:05,584 - ubuntuone.credentials - INFO - Shutting down, calling <built-in method quit of glib.MainLoop object at 0x224f2f0>.

```

*syncdaemon.log*
```

2011-03-18 12:40:52,264 - ubuntuone.SyncDaemon.tritcask - INFO - Initializing Tritcask on: /home/richard/.local/share/ubuntuone/syncdaemon/tritcask
2011-03-18 12:40:52,265 - ubuntuone.SyncDaemon.tritcask - DEBUG - lookingup data files
2011-03-18 12:40:52,266 - ubuntuone.SyncDaemon.tritcask - INFO - found 1 data files and 0 dead files
2011-03-18 12:40:52,266 - ubuntuone.SyncDaemon.tritcask - DEBUG - building the keydir, using: []
2011-03-18 12:40:52,266 - ubuntuone.SyncDaemon.tritcask - INFO - keydir ready! (keys: 0)
2011-03-18 12:40:52,318 - ubuntuone.SyncDaemon.VM.MD - DEBUG - metadata version: 7
2011-03-18 12:40:52,318 - ubuntuone.SyncDaemon.VM - DEBUG - creating shares directory: '/home/richard/.local/share/ubuntuone/shares'
2011-03-18 12:40:52,320 - ubuntuone.SyncDaemon.fsm - INFO - loading metadata from old version None
2011-03-18 12:40:52,341 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 0, idx_node_id: 0, shares: 0
2011-03-18 12:40:52,343 - ubuntuone.SyncDaemon.filesystem_notifications.GeneralProcessor - INFO - Ignoring files: ['\\A#.*\\Z', '\\A.*~\\Z', '\\A.*\\.py[oc]\\Z', '\\A.*\\.sw[nopx]\\Z', '\\A.*\\.swpx\\Z', '\\A\\..*\\.tmp\\Z']
2011-03-18 12:40:52,345 - ubuntuone.SyncDaemon.VM - DEBUG - init_root
2011-03-18 12:40:52,346 - ubuntuone.SyncDaemon.VM - DEBUG - adding inotify watch to: /home/richard/Ubuntu One
2011-03-18 12:40:52,348 - ubuntuone.SyncDaemon.FSMonitor - DEBUG - Adding general inotify watch to '/home/richard/Ubuntu One'
2011-03-18 12:40:52,349 - ubuntuone.SyncDaemon.fsm - DEBUG - create: path='/home/richard/Ubuntu One' mdid='b21e303f-8090-424f-aaf5-2aea4d61785f' share_id='' node_id=None is_dir=True
2011-03-18 12:40:52,350 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2011-03-18 12:40:52,351 - ubuntuone.SyncDaemon.QueueManager - DEBUG - start
2011-03-18 12:40:52,352 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - start
2011-03-18 12:40:52,352 - ubuntuone.SyncDaemon.StateManager - DEBUG - start
2011-03-18 12:40:53,767 - ubuntuone.SyncDaemon.DBus - DEBUG - using the real system bus
2011-03-18 12:40:53,774 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2011-03-18 12:40:53,774 - ubuntuone.SyncDaemon.DBus - INFO - connect was requested. Are we autoconnecting? True.
2011-03-18 12:40:53,966 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/richard/Ubuntu One' as root dir
2011-03-18 12:40:53,967 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/richard/.local/share/ubuntuone/syncdaemon' as data dir
2011-03-18 12:40:53,967 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/richard/.local/share/ubuntuone/shares' as shares root dir
2011-03-18 12:40:53,968 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'INIT'  (queues IDLE  connection 'Not User Not Network')>; queue: 0; hash: 0) ----
2011-03-18 12:40:53,968 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_INIT_DONE, kwargs: {}
2011-03-18 12:40:53,973 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_INIT_DONE'
2011-03-18 12:40:53,975 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition INIT --[SYS_INIT_DONE]--> LOCAL_RESCAN (queues: IDLE; connection: Not User Not Network)
2011-03-18 12:40:53,975 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2011-03-18 12:40:53,976 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all volumes
2011-03-18 12:40:53,976 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2011-03-18 12:40:53,977 - ubuntuone.SyncDaemon.local_rescan - INFO - processing move limbo
2011-03-18 12:40:53,977 - ubuntuone.SyncDaemon.local_rescan - DEBUG - process next in queue (len 1)
2011-03-18 12:40:53,977 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': LOCAL_RESCAN (error=False connected=False online=False)  Queue: IDLE  Connection: Not User Not Network}
2011-03-18 12:40:53,977 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:40:54,006 - ubuntuone.SyncDaemon.FSMonitor - DEBUG - Adding general inotify watch to '/home/richard/Ubuntu One'
2011-03-18 12:40:54,011 - ubuntuone.SyncDaemon.local_rescan - DEBUG - _scan_tree:  share_path: '/home/richard/Ubuntu One'  path: '/home/richard/Ubuntu One'
2011-03-18 12:40:54,012 - ubuntuone.SyncDaemon.local_rescan - DEBUG - Path already has watch: '/home/richard/Ubuntu One'
2011-03-18 12:40:54,013 - ubuntuone.SyncDaemon.filesystem_notifications.GeneralProcessor - DEBUG - Freeze begin: '/home/richard/Ubuntu One'
2011-03-18 12:40:54,013 - ubuntuone.SyncDaemon.local_rescan - DEBUG - scanning the dir '/home/richard/Ubuntu One'
2011-03-18 12:40:54,022 - ubuntuone.SyncDaemon.local_rescan - DEBUG - comparing directory '/home/richard/Ubuntu One'
2011-03-18 12:40:54,022 - ubuntuone.SyncDaemon.local_rescan - DEBUG - checking root: '/home/richard/Ubuntu One' in NONE, ok!
2011-03-18 12:40:54,022 - ubuntuone.SyncDaemon.local_rescan - DEBUG - comp yield: file '/home/richard/Ubuntu One/wep.txt' is new!
2011-03-18 12:40:54,023 - ubuntuone.SyncDaemon.filesystem_notifications.GeneralProcessor - DEBUG - Freeze commit: '/home/richard/Ubuntu One' (2 events)
2011-03-18 12:40:54,024 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: FS_FILE_CREATE, kwargs: {'path': '/home/richard/Ubuntu One/wep.txt'}
2011-03-18 12:40:54,024 - ubuntuone.SyncDaemon.sync - DEBUG - -:-:- - ['-'::'-'] ''/home/richard/Ubuntu One/wep.txt'' | EVENT: FS_FILE_CREATE:{} with ARGS:('/home/richard/Ubuntu One/wep.txt',)
2011-03-18 12:40:54,025 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/richard/Ubuntu One/wep.txt'' | Calling new_local_file (got FS_FILE_CREATE:{})
2011-03-18 12:40:54,027 - ubuntuone.SyncDaemon.fsm - DEBUG - create: path='/home/richard/Ubuntu One/wep.txt' mdid='1945d635-2c34-48ca-91bc-30609235dc11' share_id='' node_id=None is_dir=False
2011-03-18 12:40:54,033 - ubuntuone.SyncDaemon.fsm - DEBUG - set mdid='1945d635-2c34-48ca-91bc-30609235dc11': {'local_hash': '', 'server_hash': ''}
2011-03-18 12:40:54,058 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - MakeFile                     share:''                                       node:marker:1945d635-2c34-48ca-91bc-30609235dc11 MakeFile(share_id="''", name="u'wep.txt'", parent_id='marker:b21e303f-8090-424f-aaf5-2aea4d61785f', running='False', marker='marker:1945d635-2c34-48ca-91bc-30609235dc11', path="'/home/richard/Ubuntu One/wep.txt'") queueing
2011-03-18 12:40:54,059 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_QUEUE_ADDED, kwargs: {'command': <ubuntuone.syncdaemon.action_queue.MakeFile object at 0x3c516d8>}
2011-03-18 12:40:54,059 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_QUEUE_WAITING, kwargs: {}
2011-03-18 12:40:54,059 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - MakeFile                     share:''                                       node:marker:1945d635-2c34-48ca-91bc-30609235dc11 MakeFile(share_id="''", name="u'wep.txt'", parent_id='marker:b21e303f-8090-424f-aaf5-2aea4d61785f', running='False', marker='marker:1945d635-2c34-48ca-91bc-30609235dc11', path="'/home/richard/Ubuntu One/wep.txt'") waiting for the real value of marker:b21e303f-8090-424f-aaf5-2aea4d61785f
2011-03-18 12:40:54,060 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - MakeFile                     share:''                                       node:marker:1945d635-2c34-48ca-91bc-30609235dc11 MakeFile(share_id="''", name="u'wep.txt'", parent_id='marker:b21e303f-8090-424f-aaf5-2aea4d61785f', running='False', marker='marker:1945d635-2c34-48ca-91bc-30609235dc11', path="'/home/richard/Ubuntu One/wep.txt'") pathlock acquiring on ('', 'home', 'richard', 'Ubuntu One', 'wep.txt') (on_parent=True, on_children=False); wait for: 0
2011-03-18 12:40:54,060 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - MakeFile                     share:''                                       node:marker:1945d635-2c34-48ca-91bc-30609235dc11 MakeFile(share_id="''", name="u'wep.txt'", parent_id='marker:b21e303f-8090-424f-aaf5-2aea4d61785f', running='False', marker='marker:1945d635-2c34-48ca-91bc-30609235dc11', path="'/home/richard/Ubuntu One/wep.txt'") starting
2011-03-18 12:40:54,060 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - MakeFile                     share:''                                       node:marker:1945d635-2c34-48ca-91bc-30609235dc11 MakeFile(share_id="''", name="u'wep.txt'", parent_id='marker:b21e303f-8090-424f-aaf5-2aea4d61785f', running='False', marker='marker:1945d635-2c34-48ca-91bc-30609235dc11', path="'/home/richard/Ubuntu One/wep.txt'") not running because of inactive queue
2011-03-18 12:40:54,061 - ubuntuone.SyncDaemon.sync - DEBUG - T:NONE:F 1945d635-2c34-48ca-91bc-30609235dc11 ['root'::marker:1945d635-2c34-48ca-91bc-30609235dc11] ''Ubuntu One/wep.txt'' | Called new_local_file
2011-03-18 12:40:54,093 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_QUEUE_WAITING'
2011-03-18 12:40:54,103 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to QueueManager
2011-03-18 12:40:54,103 - ubuntuone.SyncDaemon.QueueManager - DEBUG - Changing state  IDLE -> WORKING
2011-03-18 12:40:54,104 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': LOCAL_RESCAN (error=False connected=False online=False)  Queue: WORKING  Connection: Not User Not Network}
2011-03-18 12:40:54,104 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:40:54,141 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: FS_FILE_CLOSE_WRITE, kwargs: {'path': '/home/richard/Ubuntu One/wep.txt'}
2011-03-18 12:40:54,143 - ubuntuone.SyncDaemon.sync - DEBUG - T:NONE:F 1945d635-2c34-48ca-91bc-30609235dc11 ['root'::marker:1945d635-2c34-48ca-91bc-30609235dc11] ''Ubuntu One/wep.txt'' | EVENT: FS_FILE_CLOSE_WRITE:{} with ARGS:()
2011-03-18 12:40:54,156 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 1945d635-2c34-48ca-91bc-30609235dc11 ['root'::marker:1945d635-2c34-48ca-91bc-30609235dc11] ''Ubuntu One/wep.txt'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2011-03-18 12:40:54,156 - ubuntuone.SyncDaemon.HQ - DEBUG - HashQueue: inserting path '/home/richard/Ubuntu One/wep.txt'  mdid 1945d635-2c34-48ca-91bc-30609235dc11
2011-03-18 12:40:54,184 - ubuntuone.SyncDaemon.HQ.hasher - DEBUG - Hasher: got file to hash: path '/home/richard/Ubuntu One/wep.txt'  mdid 1945d635-2c34-48ca-91bc-30609235dc11
2011-03-18 12:40:54,185 - ubuntuone.SyncDaemon.sync - DEBUG - T:NONE:F 1945d635-2c34-48ca-91bc-30609235dc11 ['root'::marker:1945d635-2c34-48ca-91bc-30609235dc11] ''Ubuntu One/wep.txt'' | Called calculate_hash
2011-03-18 12:40:54,186 - ubuntuone.SyncDaemon.local_rescan - DEBUG - process next in queue (len 0)
2011-03-18 12:40:54,186 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2011-03-18 12:40:54,187 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2011-03-18 12:40:54,187 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_LOCAL_RESCAN_DONE, kwargs: {}
2011-03-18 12:40:54,187 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_LOCAL_RESCAN_DONE'
2011-03-18 12:40:54,187 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition LOCAL_RESCAN --[SYS_LOCAL_RESCAN_DONE]--> READY (queues: WORKING; connection: Not User Not Network)
2011-03-18 12:40:54,188 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': READY (error=False connected=False online=False)  Queue: WORKING  Connection: Not User Not Network}
2011-03-18 12:40:54,188 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:40:54,212 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: FS_FILE_OPEN, kwargs: {'path': '/home/richard/Ubuntu One/wep.txt'}
2011-03-18 12:40:54,226 - ubuntuone.SyncDaemon.DBus - DEBUG - called current_status
2011-03-18 12:40:54,226 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:40:54,238 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_NET_CONNECTED, kwargs: {}
2011-03-18 12:40:54,238 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_NET_CONNECTED'
2011-03-18 12:40:54,239 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:40:54,239 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Internal transition 'Not User Not Network' -> 'Not User With Network'
2011-03-18 12:40:54,239 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned None
2011-03-18 12:40:54,247 - ubuntuone.SyncDaemon.HQ.hasher - DEBUG - Hasher: path hash pushed:  path='/home/richard/Ubuntu One/wep.txt'  hash=sha1:3b5c3c244810b4ecbbf099dfada8b570008b891d  crc=257689939  size=27  st_ino=917602  st_size=27  st_mtime=1299750612.1577723
2011-03-18 12:40:54,261 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: HQ_HASH_NEW, kwargs: {'crc32': 257689939L, 'path': '/home/richard/Ubuntu One/wep.txt', 'stat': posix.stat_result(st_mode=33188, st_ino=917602, st_dev=2050L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=27, st_atime=1300125023, st_mtime=1299750612, st_ctime=1299760885), 'hash': 'sha1:3b5c3c244810b4ecbbf099dfada8b570008b891d', 'size': 27}
2011-03-18 12:40:54,264 - ubuntuone.SyncDaemon.sync - DEBUG - T:NONE:F 1945d635-2c34-48ca-91bc-30609235dc11 ['root'::marker:1945d635-2c34-48ca-91bc-30609235dc11] ''Ubuntu One/wep.txt'' | EVENT: HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'} with ARGS:('sha1:3b5c3c244810b4ecbbf099dfada8b570008b891d', 257689939L, 27, posix.stat_result(st_mode=33188, st_ino=917602, st_dev=2050L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=27, st_atime=1300125023, st_mtime=1299750612, st_ctime=1299760885))
2011-03-18 12:40:54,265 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 1945d635-2c34-48ca-91bc-30609235dc11 ['root'::marker:1945d635-2c34-48ca-91bc-30609235dc11] ''Ubuntu One/wep.txt'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2011-03-18 12:40:54,266 - ubuntuone.SyncDaemon.fsm - DEBUG - set mdid='1945d635-2c34-48ca-91bc-30609235dc11': {'crc32': 257689939L, 'stat': posix.stat_result(st_mode=33188, st_ino=917602, st_dev=2050L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=27, st_atime=1300125023, st_mtime=1299750612, st_ctime=1299760885), 'local_hash': 'sha1:3b5c3c244810b4ecbbf099dfada8b570008b891d', 'size': 27}
2011-03-18 12:40:54,278 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Upload                       share:''                                       node:marker:1945d635-2c34-48ca-91bc-30609235dc11 Upload(share_id="''", hash="'sha1:3b5c3c244810b4ecbbf099dfada8b570008b891d'", running='False', node_id='marker:1945d635-2c34-48ca-91bc-30609235dc11', upload_id='None', crc32='257689939L', path="'/home/richard/Ubuntu One/wep.txt'", previous_hash="''", size='27') queueing
2011-03-18 12:40:54,278 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_QUEUE_ADDED, kwargs: {'command': <ubuntuone.syncdaemon.action_queue.Upload object at 0x3c0b050>}
2011-03-18 12:40:54,279 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Upload                       share:''                                       node:marker:1945d635-2c34-48ca-91bc-30609235dc11 Upload(share_id="''", hash="'sha1:3b5c3c244810b4ecbbf099dfada8b570008b891d'", running='False', node_id='marker:1945d635-2c34-48ca-91bc-30609235dc11', upload_id='None', crc32='257689939L', path="'/home/richard/Ubuntu One/wep.txt'", previous_hash="''", size='27') waiting for the real value of marker:1945d635-2c34-48ca-91bc-30609235dc11
2011-03-18 12:40:54,279 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Upload                       share:''                                       node:marker:1945d635-2c34-48ca-91bc-30609235dc11 Upload(share_id="''", hash="'sha1:3b5c3c244810b4ecbbf099dfada8b570008b891d'", running='False', node_id='marker:1945d635-2c34-48ca-91bc-30609235dc11', upload_id='None', crc32='257689939L', path="'/home/richard/Ubuntu One/wep.txt'", previous_hash="''", size='27') pathlock acquiring on ('', 'home', 'richard', 'Ubuntu One', 'wep.txt') (on_parent=False, on_children=False); wait for: 1
2011-03-18 12:40:54,294 - ubuntuone.SyncDaemon.sync - DEBUG - T:LOCAL:F 1945d635-2c34-48ca-91bc-30609235dc11 ['root'::marker:1945d635-2c34-48ca-91bc-30609235dc11] ''Ubuntu One/wep.txt'' | Called put_file
2011-03-18 12:40:54,296 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: FS_FILE_CLOSE_NOWRITE, kwargs: {'path': '/home/richard/Ubuntu One/wep.txt'}
2011-03-18 12:40:55,577 - ubuntuone.SyncDaemon.DBus - DEBUG - Handling DBus signal for member: 'CredentialsFound'.
2011-03-18 12:40:55,577 - ubuntuone.SyncDaemon.DBus - INFO - 'CredentialsFound': callbacking with credentials.
2011-03-18 12:40:55,577 - ubuntuone.SyncDaemon.DBus - INFO - connect: credential request was successful, pushing SYS_USER_CONNECT.
2011-03-18 12:40:55,578 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_USER_CONNECT, kwargs: *
2011-03-18 12:40:55,578 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_USER_CONNECT'
2011-03-18 12:40:55,578 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:40:55,579 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Internal transition 'Not User With Network' -> 'With User With Network'
2011-03-18 12:40:55,599 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned None
2011-03-18 12:40:55,624 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - SRV lookup done, choosing a server.
2011-03-18 12:40:55,625 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Using record: <RR name=_https._tcp.fs.ubuntuone.com type=SRV class=IN ttl=594s auth=False>
2011-03-18 12:40:55,626 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-03-18 12:40:55,736 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-03-18 12:40:55,736 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-03-18 12:40:55,737 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_MADE, kwargs: {}
2011-03-18 12:40:55,737 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_MADE'
2011-03-18 12:40:55,737 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition READY --[SYS_CONNECTION_MADE]--> CHECK_VERSION (queues: WORKING; connection: With User With Network)
2011-03-18 12:40:55,738 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:40:55,739 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': CHECK_VERSION (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:40:55,764 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:40:56,115 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-03-18 12:40:56,115 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_PROTOCOL_VERSION_OK, kwargs: {}
2011-03-18 12:40:56,116 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_PROTOCOL_VERSION_OK'
2011-03-18 12:40:56,116 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition CHECK_VERSION --[SYS_PROTOCOL_VERSION_OK]--> SET_CAPABILITIES (queues: WORKING; connection: With User With Network)
2011-03-18 12:40:56,116 - ubuntuone.SyncDaemon.Main - DEBUG - capabilities query: frozenset(['resumable-uploads', 'no-content', 'account-info', 'volumes', 'generations', 'fix462230'])
2011-03-18 12:40:56,118 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:40:56,120 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': SET_CAPABILITIES (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:40:56,120 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:40:56,265 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:40:56,375 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:40:56,376 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_SET_CAPABILITIES_OK, kwargs: {}
2011-03-18 12:40:56,376 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_SET_CAPABILITIES_OK'
2011-03-18 12:40:56,376 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition SET_CAPABILITIES --[SYS_SET_CAPABILITIES_OK]--> AUTHENTICATE (queues: WORKING; connection: With User With Network)
2011-03-18 12:40:56,379 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:40:56,379 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': AUTHENTICATE (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:40:56,379 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:41:46,379 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Handshake timeout!
2011-03-18 12:41:46,380 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_HANDSHAKE_TIMEOUT, kwargs: {}
2011-03-18 12:41:46,380 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_HANDSHAKE_TIMEOUT'
2011-03-18 12:41:46,380 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:41:46,380 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned STANDOFF
2011-03-18 12:41:46,381 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition AUTHENTICATE --[SYS_HANDSHAKE_TIMEOUT]--> STANDOFF (queues: WORKING; connection: With User With Network)
2011-03-18 12:41:46,381 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Disconnected.
2011-03-18 12:41:46,381 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': STANDOFF (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:41:46,381 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:41:46,383 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionDone'>: Connection was closed cleanly.
].
2011-03-18 12:41:46,383 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Client mismatch while processing the request 'oauth_authenticate', client (<ubuntuone.syncdaemon.action_queue.ActionQueueProtocol instance at 0x3c16710>) is not self.client (None).
2011-03-18 12:41:46,384 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_LOST, kwargs: {}
2011-03-18 12:41:46,384 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_LOST'
2011-03-18 12:41:46,384 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:41:46,384 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned WAITING
2011-03-18 12:41:46,385 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition STANDOFF --[SYS_CONNECTION_LOST]--> WAITING (queues: WORKING; connection: With User With Network)
2011-03-18 12:41:46,385 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'waiting' timer on 2 secs
2011-03-18 12:41:46,385 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': WAITING (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:41:46,421 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:41:46,421 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection was closed cleanly.
2011-03-18 12:41:48,386 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Waiting time expired
2011-03-18 12:41:48,386 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_RETRY, kwargs: {}
2011-03-18 12:41:48,387 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_RETRY'
2011-03-18 12:41:48,387 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition WAITING --[SYS_CONNECTION_RETRY]--> READY (queues: WORKING; connection: With User With Network)
2011-03-18 12:41:48,389 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': READY (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:41:48,389 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:41:48,415 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - SRV lookup done, choosing a server.
2011-03-18 12:41:48,415 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Using record: <RR name=_https._tcp.fs.ubuntuone.com type=SRV class=IN ttl=541s auth=False>
2011-03-18 12:41:48,416 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-03-18 12:41:48,535 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-03-18 12:41:48,535 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-03-18 12:41:48,535 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_MADE, kwargs: {}
2011-03-18 12:41:48,536 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_MADE'
2011-03-18 12:41:48,536 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition READY --[SYS_CONNECTION_MADE]--> CHECK_VERSION (queues: WORKING; connection: With User With Network)
2011-03-18 12:41:48,537 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:41:48,537 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': CHECK_VERSION (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:41:48,544 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:41:48,895 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-03-18 12:41:48,895 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_PROTOCOL_VERSION_OK, kwargs: {}
2011-03-18 12:41:48,895 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_PROTOCOL_VERSION_OK'
2011-03-18 12:41:48,895 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition CHECK_VERSION --[SYS_PROTOCOL_VERSION_OK]--> SET_CAPABILITIES (queues: WORKING; connection: With User With Network)
2011-03-18 12:41:48,896 - ubuntuone.SyncDaemon.Main - DEBUG - capabilities query: frozenset(['resumable-uploads', 'no-content', 'account-info', 'volumes', 'generations', 'fix462230'])
2011-03-18 12:41:48,897 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:41:48,897 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': SET_CAPABILITIES (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:41:48,898 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:41:49,005 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:41:49,115 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:41:49,115 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_SET_CAPABILITIES_OK, kwargs: {}
2011-03-18 12:41:49,116 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_SET_CAPABILITIES_OK'
2011-03-18 12:41:49,116 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition SET_CAPABILITIES --[SYS_SET_CAPABILITIES_OK]--> AUTHENTICATE (queues: WORKING; connection: With User With Network)
2011-03-18 12:41:49,118 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:41:49,118 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': AUTHENTICATE (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:41:49,119 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:42:39,118 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Handshake timeout!
2011-03-18 12:42:39,119 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_HANDSHAKE_TIMEOUT, kwargs: {}
2011-03-18 12:42:39,119 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_HANDSHAKE_TIMEOUT'
2011-03-18 12:42:39,119 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:42:39,120 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned STANDOFF
2011-03-18 12:42:39,120 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition AUTHENTICATE --[SYS_HANDSHAKE_TIMEOUT]--> STANDOFF (queues: WORKING; connection: With User With Network)
2011-03-18 12:42:39,120 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Disconnected.
2011-03-18 12:42:39,121 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': STANDOFF (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:42:39,121 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:42:39,135 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionDone'>: Connection was closed cleanly.
].
2011-03-18 12:42:39,136 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Client mismatch while processing the request 'oauth_authenticate', client (<ubuntuone.syncdaemon.action_queue.ActionQueueProtocol instance at 0x3c00cf8>) is not self.client (None).
2011-03-18 12:42:39,136 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_LOST, kwargs: {}
2011-03-18 12:42:39,136 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_LOST'
2011-03-18 12:42:39,137 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:42:39,137 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned WAITING
2011-03-18 12:42:39,137 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition STANDOFF --[SYS_CONNECTION_LOST]--> WAITING (queues: WORKING; connection: With User With Network)
2011-03-18 12:42:39,137 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'waiting' timer on 4 secs
2011-03-18 12:42:39,138 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': WAITING (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:42:39,188 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:42:39,188 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection was closed cleanly.
2011-03-18 12:42:43,138 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Waiting time expired
2011-03-18 12:42:43,139 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_RETRY, kwargs: {}
2011-03-18 12:42:43,139 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_RETRY'
2011-03-18 12:42:43,139 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition WAITING --[SYS_CONNECTION_RETRY]--> READY (queues: WORKING; connection: With User With Network)
2011-03-18 12:42:43,141 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': READY (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:42:43,141 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:42:43,165 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - SRV lookup done, choosing a server.
2011-03-18 12:42:43,166 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Using record: <RR name=_https._tcp.fs.ubuntuone.com type=SRV class=IN ttl=569s auth=False>
2011-03-18 12:42:43,167 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-03-18 12:42:43,315 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-03-18 12:42:43,315 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-03-18 12:42:43,316 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_MADE, kwargs: {}
2011-03-18 12:42:43,316 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_MADE'
2011-03-18 12:42:43,316 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition READY --[SYS_CONNECTION_MADE]--> CHECK_VERSION (queues: WORKING; connection: With User With Network)
2011-03-18 12:42:43,317 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:42:43,317 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': CHECK_VERSION (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:42:43,321 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:42:43,685 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-03-18 12:42:43,685 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_PROTOCOL_VERSION_OK, kwargs: {}
2011-03-18 12:42:43,686 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_PROTOCOL_VERSION_OK'
2011-03-18 12:42:43,686 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition CHECK_VERSION --[SYS_PROTOCOL_VERSION_OK]--> SET_CAPABILITIES (queues: WORKING; connection: With User With Network)
2011-03-18 12:42:43,686 - ubuntuone.SyncDaemon.Main - DEBUG - capabilities query: frozenset(['resumable-uploads', 'no-content', 'account-info', 'volumes', 'generations', 'fix462230'])
2011-03-18 12:42:43,688 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:42:43,689 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': SET_CAPABILITIES (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:42:43,689 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:42:43,825 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:42:43,935 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:42:43,936 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_SET_CAPABILITIES_OK, kwargs: {}
2011-03-18 12:42:43,936 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_SET_CAPABILITIES_OK'
2011-03-18 12:42:43,936 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition SET_CAPABILITIES --[SYS_SET_CAPABILITIES_OK]--> AUTHENTICATE (queues: WORKING; connection: With User With Network)
2011-03-18 12:42:43,938 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:42:43,939 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': AUTHENTICATE (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:42:43,939 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:42:53,968 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTHENTICATE'  (queues WORKING  connection 'With User With Network')>; queue: 2; hash: 0) ----
2011-03-18 12:43:33,939 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Handshake timeout!
2011-03-18 12:43:33,939 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_HANDSHAKE_TIMEOUT, kwargs: {}
2011-03-18 12:43:33,940 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_HANDSHAKE_TIMEOUT'
2011-03-18 12:43:33,940 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:43:33,940 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned STANDOFF
2011-03-18 12:43:33,940 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition AUTHENTICATE --[SYS_HANDSHAKE_TIMEOUT]--> STANDOFF (queues: WORKING; connection: With User With Network)
2011-03-18 12:43:33,941 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Disconnected.
2011-03-18 12:43:33,941 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': STANDOFF (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:43:33,941 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:43:33,954 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionDone'>: Connection was closed cleanly.
].
2011-03-18 12:43:33,955 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Client mismatch while processing the request 'oauth_authenticate', client (<ubuntuone.syncdaemon.action_queue.ActionQueueProtocol instance at 0x3c00cf8>) is not self.client (None).
2011-03-18 12:43:33,955 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_LOST, kwargs: {}
2011-03-18 12:43:33,955 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_LOST'
2011-03-18 12:43:33,956 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:43:33,956 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned WAITING
2011-03-18 12:43:33,956 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition STANDOFF --[SYS_CONNECTION_LOST]--> WAITING (queues: WORKING; connection: With User With Network)
2011-03-18 12:43:33,956 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'waiting' timer on 8 secs
2011-03-18 12:43:33,956 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': WAITING (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:43:34,010 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:43:34,011 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection was closed cleanly.
2011-03-18 12:43:41,957 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Waiting time expired
2011-03-18 12:43:41,957 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_RETRY, kwargs: {}
2011-03-18 12:43:41,957 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_RETRY'
2011-03-18 12:43:41,957 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition WAITING --[SYS_CONNECTION_RETRY]--> READY (queues: WORKING; connection: With User With Network)
2011-03-18 12:43:41,959 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': READY (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:43:41,959 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:43:41,985 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - SRV lookup done, choosing a server.
2011-03-18 12:43:41,986 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Using record: <RR name=_https._tcp.fs.ubuntuone.com type=SRV class=IN ttl=511s auth=False>
2011-03-18 12:43:41,987 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-03-18 12:43:42,115 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-03-18 12:43:42,116 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-03-18 12:43:42,116 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_MADE, kwargs: {}
2011-03-18 12:43:42,116 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_MADE'
2011-03-18 12:43:42,117 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition READY --[SYS_CONNECTION_MADE]--> CHECK_VERSION (queues: WORKING; connection: With User With Network)
2011-03-18 12:43:42,118 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:43:42,118 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': CHECK_VERSION (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:43:42,124 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:43:42,495 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-03-18 12:43:42,496 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_PROTOCOL_VERSION_OK, kwargs: {}
2011-03-18 12:43:42,496 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_PROTOCOL_VERSION_OK'
2011-03-18 12:43:42,496 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition CHECK_VERSION --[SYS_PROTOCOL_VERSION_OK]--> SET_CAPABILITIES (queues: WORKING; connection: With User With Network)
2011-03-18 12:43:42,496 - ubuntuone.SyncDaemon.Main - DEBUG - capabilities query: frozenset(['resumable-uploads', 'no-content', 'account-info', 'volumes', 'generations', 'fix462230'])
2011-03-18 12:43:42,498 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:43:42,498 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': SET_CAPABILITIES (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:43:42,499 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:43:42,655 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:43:42,766 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:43:42,766 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_SET_CAPABILITIES_OK, kwargs: {}
2011-03-18 12:43:42,767 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_SET_CAPABILITIES_OK'
2011-03-18 12:43:42,767 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition SET_CAPABILITIES --[SYS_SET_CAPABILITIES_OK]--> AUTHENTICATE (queues: WORKING; connection: With User With Network)
2011-03-18 12:43:42,769 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:43:42,770 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': AUTHENTICATE (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:43:42,770 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:44:32,770 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Handshake timeout!
2011-03-18 12:44:32,771 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_HANDSHAKE_TIMEOUT, kwargs: {}
2011-03-18 12:44:32,771 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_HANDSHAKE_TIMEOUT'
2011-03-18 12:44:32,771 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:44:32,771 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned STANDOFF
2011-03-18 12:44:32,772 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition AUTHENTICATE --[SYS_HANDSHAKE_TIMEOUT]--> STANDOFF (queues: WORKING; connection: With User With Network)
2011-03-18 12:44:32,772 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Disconnected.
2011-03-18 12:44:32,772 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': STANDOFF (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:44:32,773 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:44:32,784 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionDone'>: Connection was closed cleanly.
].
2011-03-18 12:44:32,785 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Client mismatch while processing the request 'oauth_authenticate', client (<ubuntuone.syncdaemon.action_queue.ActionQueueProtocol instance at 0x3c00cf8>) is not self.client (None).
2011-03-18 12:44:32,786 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_LOST, kwargs: {}
2011-03-18 12:44:32,786 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_LOST'
2011-03-18 12:44:32,786 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:44:32,786 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned WAITING
2011-03-18 12:44:32,786 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition STANDOFF --[SYS_CONNECTION_LOST]--> WAITING (queues: WORKING; connection: With User With Network)
2011-03-18 12:44:32,787 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'waiting' timer on 16 secs
2011-03-18 12:44:32,787 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': WAITING (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:44:32,830 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:44:32,830 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection was closed cleanly.
2011-03-18 12:44:48,787 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Waiting time expired
2011-03-18 12:44:48,787 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_RETRY, kwargs: {}
2011-03-18 12:44:48,788 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_RETRY'
2011-03-18 12:44:48,788 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition WAITING --[SYS_CONNECTION_RETRY]--> READY (queues: WORKING; connection: With User With Network)
2011-03-18 12:44:48,789 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': READY (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:44:48,790 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:44:48,815 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - SRV lookup done, choosing a server.
2011-03-18 12:44:48,816 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Using record: <RR name=_https._tcp.fs.ubuntuone.com type=SRV class=IN ttl=444s auth=False>
2011-03-18 12:44:48,817 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-03-18 12:44:48,936 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-03-18 12:44:48,936 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-03-18 12:44:48,936 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_MADE, kwargs: {}
2011-03-18 12:44:48,936 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_MADE'
2011-03-18 12:44:48,937 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition READY --[SYS_CONNECTION_MADE]--> CHECK_VERSION (queues: WORKING; connection: With User With Network)
2011-03-18 12:44:48,937 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:44:48,938 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': CHECK_VERSION (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:44:48,983 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:44:49,386 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-03-18 12:44:49,386 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_PROTOCOL_VERSION_OK, kwargs: {}
2011-03-18 12:44:49,386 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_PROTOCOL_VERSION_OK'
2011-03-18 12:44:49,386 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition CHECK_VERSION --[SYS_PROTOCOL_VERSION_OK]--> SET_CAPABILITIES (queues: WORKING; connection: With User With Network)
2011-03-18 12:44:49,387 - ubuntuone.SyncDaemon.Main - DEBUG - capabilities query: frozenset(['resumable-uploads', 'no-content', 'account-info', 'volumes', 'generations', 'fix462230'])
2011-03-18 12:44:49,388 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:44:49,389 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': SET_CAPABILITIES (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:44:49,389 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:44:49,516 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:44:50,516 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:44:50,517 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_SET_CAPABILITIES_OK, kwargs: {}
2011-03-18 12:44:50,517 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_SET_CAPABILITIES_OK'
2011-03-18 12:44:50,517 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition SET_CAPABILITIES --[SYS_SET_CAPABILITIES_OK]--> AUTHENTICATE (queues: WORKING; connection: With User With Network)
2011-03-18 12:44:50,521 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:44:50,521 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': AUTHENTICATE (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:44:50,521 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:44:53,968 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTHENTICATE'  (queues WORKING  connection 'With User With Network')>; queue: 2; hash: 0) ----
2011-03-18 12:45:40,521 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Handshake timeout!
2011-03-18 12:45:40,522 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_HANDSHAKE_TIMEOUT, kwargs: {}
2011-03-18 12:45:40,522 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_HANDSHAKE_TIMEOUT'
2011-03-18 12:45:40,522 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:45:40,522 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned STANDOFF
2011-03-18 12:45:40,523 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition AUTHENTICATE --[SYS_HANDSHAKE_TIMEOUT]--> STANDOFF (queues: WORKING; connection: With User With Network)
2011-03-18 12:45:40,523 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Disconnected.
2011-03-18 12:45:40,523 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': STANDOFF (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:45:40,524 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:45:40,528 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionDone'>: Connection was closed cleanly.
].
2011-03-18 12:45:40,528 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Client mismatch while processing the request 'oauth_authenticate', client (<ubuntuone.syncdaemon.action_queue.ActionQueueProtocol instance at 0x3c16710>) is not self.client (None).
2011-03-18 12:45:40,529 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_LOST, kwargs: {}
2011-03-18 12:45:40,529 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_LOST'
2011-03-18 12:45:40,529 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:45:40,530 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned WAITING
2011-03-18 12:45:40,530 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition STANDOFF --[SYS_CONNECTION_LOST]--> WAITING (queues: WORKING; connection: With User With Network)
2011-03-18 12:45:40,530 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'waiting' timer on 32 secs
2011-03-18 12:45:40,530 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': WAITING (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:45:40,575 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:45:40,575 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection was closed cleanly.
2011-03-18 12:46:12,531 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Waiting time expired
2011-03-18 12:46:12,531 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_RETRY, kwargs: {}
2011-03-18 12:46:12,532 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_RETRY'
2011-03-18 12:46:12,532 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition WAITING --[SYS_CONNECTION_RETRY]--> READY (queues: WORKING; connection: With User With Network)
2011-03-18 12:46:12,533 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': READY (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:46:12,534 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:46:12,556 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - SRV lookup done, choosing a server.
2011-03-18 12:46:12,556 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Using record: <RR name=_https._tcp.fs.ubuntuone.com type=SRV class=IN ttl=360s auth=False>
2011-03-18 12:46:12,557 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-03-18 12:46:12,666 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-03-18 12:46:12,666 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-03-18 12:46:12,667 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_MADE, kwargs: {}
2011-03-18 12:46:12,667 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_MADE'
2011-03-18 12:46:12,667 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition READY --[SYS_CONNECTION_MADE]--> CHECK_VERSION (queues: WORKING; connection: With User With Network)
2011-03-18 12:46:12,668 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:46:12,669 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': CHECK_VERSION (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:46:12,700 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:46:13,076 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-03-18 12:46:13,077 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_PROTOCOL_VERSION_OK, kwargs: {}
2011-03-18 12:46:13,077 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_PROTOCOL_VERSION_OK'
2011-03-18 12:46:13,077 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition CHECK_VERSION --[SYS_PROTOCOL_VERSION_OK]--> SET_CAPABILITIES (queues: WORKING; connection: With User With Network)
2011-03-18 12:46:13,077 - ubuntuone.SyncDaemon.Main - DEBUG - capabilities query: frozenset(['resumable-uploads', 'no-content', 'account-info', 'volumes', 'generations', 'fix462230'])
2011-03-18 12:46:13,079 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:46:13,079 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': SET_CAPABILITIES (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:46:13,080 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:46:13,204 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:46:13,316 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:46:13,317 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_SET_CAPABILITIES_OK, kwargs: {}
2011-03-18 12:46:13,317 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_SET_CAPABILITIES_OK'
2011-03-18 12:46:13,317 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition SET_CAPABILITIES --[SYS_SET_CAPABILITIES_OK]--> AUTHENTICATE (queues: WORKING; connection: With User With Network)
2011-03-18 12:46:13,319 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:46:13,320 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': AUTHENTICATE (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:46:13,320 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:46:53,968 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTHENTICATE'  (queues WORKING  connection 'With User With Network')>; queue: 2; hash: 0) ----
2011-03-18 12:47:03,320 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Handshake timeout!
2011-03-18 12:47:03,321 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_HANDSHAKE_TIMEOUT, kwargs: {}
2011-03-18 12:47:03,321 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_HANDSHAKE_TIMEOUT'
2011-03-18 12:47:03,321 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:47:03,321 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned STANDOFF
2011-03-18 12:47:03,322 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition AUTHENTICATE --[SYS_HANDSHAKE_TIMEOUT]--> STANDOFF (queues: WORKING; connection: With User With Network)
2011-03-18 12:47:03,322 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Disconnected.
2011-03-18 12:47:03,322 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': STANDOFF (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:47:03,323 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:47:03,335 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionDone'>: Connection was closed cleanly.
].
2011-03-18 12:47:03,335 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Client mismatch while processing the request 'oauth_authenticate', client (<ubuntuone.syncdaemon.action_queue.ActionQueueProtocol instance at 0x3c16cf8>) is not self.client (None).
2011-03-18 12:47:03,336 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_LOST, kwargs: {}
2011-03-18 12:47:03,336 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_LOST'
2011-03-18 12:47:03,336 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:47:03,337 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned WAITING
2011-03-18 12:47:03,337 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition STANDOFF --[SYS_CONNECTION_LOST]--> WAITING (queues: WORKING; connection: With User With Network)
2011-03-18 12:47:03,337 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'waiting' timer on 64 secs
2011-03-18 12:47:03,344 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': WAITING (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:47:03,382 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:47:03,388 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection was closed cleanly.
2011-03-18 12:47:38,359 - ubuntuone.SyncDaemon.DBus - DEBUG - Folders.get_folders
2011-03-18 12:47:38,360 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - Folders.get_folders
2011-03-18 12:47:38,361 - ubuntuone.SyncDaemon.DBus - DEBUG - called get_shared
2011-03-18 12:47:38,362 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called get_shared
2011-03-18 12:47:40,261 - ubuntuone.SyncDaemon.DBus - DEBUG - get_metadata_and_quick_tree_synced: dbus.String(u'/home/richard/Ubuntu One')
2011-03-18 12:47:40,261 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - get_metadata_and_quick_tree_synced: dbus.String(u'/home/richard/Ubuntu One')
2011-03-18 12:47:40,263 - ubuntuone.SyncDaemon.DBus - DEBUG - called get_shares
2011-03-18 12:47:40,263 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called get_shares
2011-03-18 12:48:07,344 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Waiting time expired
2011-03-18 12:48:07,345 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_RETRY, kwargs: {}
2011-03-18 12:48:07,345 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_RETRY'
2011-03-18 12:48:07,345 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition WAITING --[SYS_CONNECTION_RETRY]--> READY (queues: WORKING; connection: With User With Network)
2011-03-18 12:48:07,347 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': READY (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:48:07,348 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:48:07,377 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - SRV lookup done, choosing a server.
2011-03-18 12:48:07,377 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Using record: <RR name=_https._tcp.fs.ubuntuone.com type=SRV class=IN ttl=245s auth=False>
2011-03-18 12:48:07,378 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-03-18 12:48:07,487 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-03-18 12:48:07,487 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-03-18 12:48:07,488 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_MADE, kwargs: {}
2011-03-18 12:48:07,488 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_MADE'
2011-03-18 12:48:07,488 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition READY --[SYS_CONNECTION_MADE]--> CHECK_VERSION (queues: WORKING; connection: With User With Network)
2011-03-18 12:48:07,490 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:48:07,490 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': CHECK_VERSION (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:48:07,583 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:48:08,004 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-03-18 12:48:08,005 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_PROTOCOL_VERSION_OK, kwargs: {}
2011-03-18 12:48:08,005 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_PROTOCOL_VERSION_OK'
2011-03-18 12:48:08,005 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition CHECK_VERSION --[SYS_PROTOCOL_VERSION_OK]--> SET_CAPABILITIES (queues: WORKING; connection: With User With Network)
2011-03-18 12:48:08,006 - ubuntuone.SyncDaemon.Main - DEBUG - capabilities query: frozenset(['resumable-uploads', 'no-content', 'account-info', 'volumes', 'generations', 'fix462230'])
2011-03-18 12:48:08,007 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:48:08,008 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': SET_CAPABILITIES (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:48:08,008 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:48:08,117 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:48:08,227 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:48:08,229 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_SET_CAPABILITIES_OK, kwargs: {}
2011-03-18 12:48:08,229 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_SET_CAPABILITIES_OK'
2011-03-18 12:48:08,230 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition SET_CAPABILITIES --[SYS_SET_CAPABILITIES_OK]--> AUTHENTICATE (queues: WORKING; connection: With User With Network)
2011-03-18 12:48:08,233 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:48:08,233 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': AUTHENTICATE (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:48:08,234 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:48:53,968 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTHENTICATE'  (queues WORKING  connection 'With User With Network')>; queue: 2; hash: 0) ----
2011-03-18 12:48:58,233 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Handshake timeout!
2011-03-18 12:48:58,234 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_HANDSHAKE_TIMEOUT, kwargs: {}
2011-03-18 12:48:58,234 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_HANDSHAKE_TIMEOUT'
2011-03-18 12:48:58,234 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:48:58,235 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned STANDOFF
2011-03-18 12:48:58,235 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition AUTHENTICATE --[SYS_HANDSHAKE_TIMEOUT]--> STANDOFF (queues: WORKING; connection: With User With Network)
2011-03-18 12:48:58,235 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Disconnected.
2011-03-18 12:48:58,236 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': STANDOFF (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:48:58,236 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:48:58,241 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionDone'>: Connection was closed cleanly.
].
2011-03-18 12:48:58,241 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Client mismatch while processing the request 'oauth_authenticate', client (<ubuntuone.syncdaemon.action_queue.ActionQueueProtocol instance at 0x3c01488>) is not self.client (None).
2011-03-18 12:48:58,242 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_LOST, kwargs: {}
2011-03-18 12:48:58,242 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_LOST'
2011-03-18 12:48:58,242 - ubuntuone.SyncDaemon.StateManager - DEBUG - sending event to ConnectionManager
2011-03-18 12:48:58,242 - ubuntuone.SyncDaemon.StateManager - DEBUG - ConnectionManager returned WAITING
2011-03-18 12:48:58,242 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition STANDOFF --[SYS_CONNECTION_LOST]--> WAITING (queues: WORKING; connection: With User With Network)
2011-03-18 12:48:58,243 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'waiting' timer on 120 secs
2011-03-18 12:48:58,243 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': WAITING (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:48:58,308 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:48:58,309 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection was closed cleanly.
2011-03-18 12:50:53,968 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'WAITING'  (queues WORKING  connection 'With User With Network')>; queue: 2; hash: 0) ----
2011-03-18 12:50:58,243 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Waiting time expired
2011-03-18 12:50:58,243 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_RETRY, kwargs: {}
2011-03-18 12:50:58,244 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_RETRY'
2011-03-18 12:50:58,244 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition WAITING --[SYS_CONNECTION_RETRY]--> READY (queues: WORKING; connection: With User With Network)
2011-03-18 12:50:58,246 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': READY (error=False connected=False online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:50:58,246 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:50:58,277 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - SRV lookup done, choosing a server.
2011-03-18 12:50:58,278 - ubuntuone.SyncDaemon.ActionQueue - DEBUG - Using record: <RR name=_https._tcp.fs.ubuntuone.com type=SRV class=IN ttl=74s auth=False>
2011-03-18 12:50:58,279 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2011-03-18 12:50:58,398 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-03-18 12:50:58,398 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-03-18 12:50:58,398 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_CONNECTION_MADE, kwargs: {}
2011-03-18 12:50:58,399 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_CONNECTION_MADE'
2011-03-18 12:50:58,399 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition READY --[SYS_CONNECTION_MADE]--> CHECK_VERSION (queues: WORKING; connection: With User With Network)
2011-03-18 12:50:58,400 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:50:58,400 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': CHECK_VERSION (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:50:58,422 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:50:59,158 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2011-03-18 12:50:59,158 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_PROTOCOL_VERSION_OK, kwargs: {}
2011-03-18 12:50:59,159 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_PROTOCOL_VERSION_OK'
2011-03-18 12:50:59,159 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition CHECK_VERSION --[SYS_PROTOCOL_VERSION_OK]--> SET_CAPABILITIES (queues: WORKING; connection: With User With Network)
2011-03-18 12:50:59,159 - ubuntuone.SyncDaemon.Main - DEBUG - capabilities query: frozenset(['resumable-uploads', 'no-content', 'account-info', 'volumes', 'generations', 'fix462230'])
2011-03-18 12:50:59,160 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:50:59,161 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': SET_CAPABILITIES (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:50:59,161 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status
2011-03-18 12:50:59,278 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:50:59,408 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2011-03-18 12:50:59,408 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_SET_CAPABILITIES_OK, kwargs: {}
2011-03-18 12:50:59,408 - ubuntuone.SyncDaemon.StateManager - DEBUG - received event 'SYS_SET_CAPABILITIES_OK'
2011-03-18 12:50:59,408 - ubuntuone.SyncDaemon.StateManager - DEBUG - Transition SET_CAPABILITIES --[SYS_SET_CAPABILITIES_OK]--> AUTHENTICATE (queues: WORKING; connection: With User With Network)
2011-03-18 12:50:59,411 - ubuntuone.SyncDaemon.ConnectionManager - DEBUG - Setting up the 'handshake' timer on 50 secs
2011-03-18 12:50:59,411 - ubuntuone.SyncDaemon.EQ - DEBUG - push_event: SYS_STATE_CHANGED, kwargs: {'state': AUTHENTICATE (error=False connected=True online=False)  Queue: WORKING  Connection: With User With Network}
2011-03-18 12:50:59,411 - ubuntuone.SyncDaemon.InteractionInterfaces - DEBUG - called current_status

```

---

### Post by Koffeehaus on 2011-05-17
I get the same thing, have been trying to upload one single PDF file for about an hour now. Have registered for a new account - same thing.....

What's even more strange, when I remove the machine from devices list and I get thrown back to the initial "Join Now" page - I still get the "'reference' is being uploaded to your cloud message"! wtf?  ](*,)

natty 32bit

I'm coming to think Natty was a mistake...

---

