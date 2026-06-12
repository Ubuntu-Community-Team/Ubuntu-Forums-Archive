---
title: "Some folders sync, others do not"
date: 2010-12-01
forum: Ubuntu One (CLOSED)
---

### Post by Dragonbite on 2010-12-01
I am using UbuntuOne (U1) with 2 computers.

I connected with my desktop computer to sync with 3 of my directories (Documents, Projects and Public) and uploaded their contents.

I connect to the U1 with my laptop and the Documents directory is no longer able to sync with U1.  I right-click on the menu and select to Sync but it doesn't work.

The other folders have updated with no problems, just the Documents folder does not.

The Documents folder in the Laptop is cleared out. I was going to sync, and then add the files already on the laptop to the directory and sync to move them up to the cloud (and thus, to download on my desktop the next time I log in).

---

### Post by duanedesign on 2010-12-01
Dragonbite,
could you please look in ~/.cache/ubuntuone/log/ and see if the syncdaemon-exceptions.log contains anything. If so could you post it here.

thank you,
duanedesign

---

### Post by Dragonbite on 2010-12-01
> **duanedesign said:**
> Dragonbite,
could you please look in ~/.cache/ubuntuone/log/ and see if the syncdaemon-exceptions.log contains anything. If so could you post it here.

thank you,
duanedesign

I will when I am back home tonight (just started work).

OH YEAH: I forgot to mention that both machines are running Ubuntu 10.04.

---

### Post by Dragonbite on 2010-12-01
Ok, in that location I had syncdaemon-exceptions.log but it was empty. There were other log files with the same name and a date-time stamp on the end of it.

So this is the contents of the latest one.```
2010-12-01 00:34:58,498 - ubuntuone.SyncDaemon.fsm - INFO - loading updated metadata
2010-12-01 00:35:12,395 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 86, idx_node_id: 86, shares: 5
2010-12-01 00:35:12,397 - ubuntuone.SyncDaemon.GeneralINotProc - INFO - Ignoring files: ['\\A#.*\\Z', '\\A.*~\\Z', '\\A.*\\.py[oc]\\Z', '\\A.*\\.sw[nopx]\\Z', '\\A.*\\.swpx\\Z', '\\A\\..*\\.tmp\\Z']
2010-12-01 00:35:12,404 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2010-12-01 00:35:13,976 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2010-12-01 00:35:13,977 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/drew/Ubuntu One' as root dir
2010-12-01 00:35:13,977 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/drew/.local/share/ubuntuone/syncdaemon' as data dir
2010-12-01 00:35:13,977 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/drew/.local/share/ubuntuone/shares' as shares root dir
2010-12-01 00:35:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'INIT'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1 miss=86) ----
2010-12-01 00:35:13,978 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2010-12-01 00:35:13,978 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all volumes
2010-12-01 00:35:14,208 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2010-12-01 00:35:14,257 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2010-12-01 00:35:14,257 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2010-12-01 00:35:14,600 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2010-12-01 00:35:14,779 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2010-12-01 00:35:14,780 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2010-12-01 00:35:15,067 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2010-12-01 00:35:15,162 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2010-12-01 00:35:15,254 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2010-12-01 00:35:15,971 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'oauth_authenticate' finished OK.
2010-12-01 00:35:16,891 - ubuntuone.SyncDaemon.ActionQueue - INFO - Server rescan: will query 86 objects
2010-12-01 00:35:21,531 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T 8ab2dd70-dad1-47b2-b0db-41f007b52e71 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'c22d344c-cfcd-488d-8478-92d7f57e4e0d'] ''Projects/ShawnaLee'' | Calling get_dir (got SV_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-12-01 00:35:21,625 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T 8ab2dd70-dad1-47b2-b0db-41f007b52e71 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'c22d344c-cfcd-488d-8478-92d7f57e4e0d'] ''Projects/ShawnaLee'' | Called get_dir (In: T:NONE:T)
2010-12-01 00:35:23,230 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request '_get_root_and_query' finished OK.
2010-12-01 00:35:25,222 - ubuntuone.SyncDaemon.local_rescan - INFO - scan dir: '/home/drew/Documents'  mdid: 262be2ae-e6e9-4afa-aef5-956dc528cb40
2010-12-01 00:35:25,235 - ubuntuone.SyncDaemon.VM - INFO - udf_deleted: '52895b29-a0bc-489b-b7b0-eebae6630e39'
2010-12-01 00:35:25,361 - ubuntuone.SyncDaemon.local_rescan - ERROR - in the scan: <type 'exceptions.KeyError'> ('/home/drew/Documents')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 256, in _scan_tree
    d.addCallbacks(self._scan_one_dir)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 213, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 371, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 664, in _scan_one_dir
    d = defer.execute(scan)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 88, in execute
    result = callable(*args, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 624, in scan
    share, partials)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 309, in _compare
    mdobj = self.fsm.get_by_path(fullname)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 550, in get_by_path
    mdid = self._idx_path[path]
exceptions.KeyError: '/home/drew/Documents'

2010-12-01 00:35:25,362 - twisted - ERROR - Unhandled error in Deferred:
2010-12-01 00:35:25,363 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 256, in _scan_tree
    d.addCallbacks(self._scan_one_dir)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 213, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 371, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 664, in _scan_one_dir
    d = defer.execute(scan)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 88, in execute
    result = callable(*args, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 624, in scan
    share, partials)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 309, in _compare
    mdobj = self.fsm.get_by_path(fullname)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 550, in get_by_path
    mdid = self._idx_path[path]
exceptions.KeyError: '/home/drew/Documents'

2010-12-01 00:35:30,008 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T 8ab2dd70-dad1-47b2-b0db-41f007b52e71 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'c22d344c-cfcd-488d-8478-92d7f57e4e0d'] ''Projects/ShawnaLee'' | Calling merge_directory (got AQ_DOWNLOAD_FINISHED:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'T'})
2010-12-01 00:35:30,073 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T 8ab2dd70-dad1-47b2-b0db-41f007b52e71 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'c22d344c-cfcd-488d-8478-92d7f57e4e0d'] ''Projects/ShawnaLee'' | Called merge_directory (In: T:SERVER:T)
2010-12-01 00:35:30,077 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/drew/Projects/ShawnaLee/current'' | Calling new_dir (got SV_DIR_NEW:{})
2010-12-01 00:35:30,096 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T cb3c1a5c-4cfa-4bc3-879b-9f4ea2bbae25 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'67f8a3c1-0b1a-4b03-a705-cdbd5521ae24'] ''Projects/ShawnaLee/current'' | Called new_dir (In: F:NA:NA)
2010-12-01 00:35:30,114 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T cb3c1a5c-4cfa-4bc3-879b-9f4ea2bbae25 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'67f8a3c1-0b1a-4b03-a705-cdbd5521ae24'] ''Projects/ShawnaLee/current'' | Calling nothing (got FS_DIR_CREATE:{})
2010-12-01 00:35:30,116 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T cb3c1a5c-4cfa-4bc3-879b-9f4ea2bbae25 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'67f8a3c1-0b1a-4b03-a705-cdbd5521ae24'] ''Projects/ShawnaLee/current'' | Called nothing (In: T:NONE:T)
2010-12-01 00:35:32,486 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T cb3c1a5c-4cfa-4bc3-879b-9f4ea2bbae25 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'67f8a3c1-0b1a-4b03-a705-cdbd5521ae24'] ''Projects/ShawnaLee/current'' | Calling get_dir (got SV_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-12-01 00:35:32,492 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T cb3c1a5c-4cfa-4bc3-879b-9f4ea2bbae25 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'67f8a3c1-0b1a-4b03-a705-cdbd5521ae24'] ''Projects/ShawnaLee/current'' | Called get_dir (In: T:NONE:T)
2010-12-01 00:35:33,737 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T cb3c1a5c-4cfa-4bc3-879b-9f4ea2bbae25 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'67f8a3c1-0b1a-4b03-a705-cdbd5521ae24'] ''Projects/ShawnaLee/current'' | Calling merge_directory (got AQ_DOWNLOAD_FINISHED:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'T'})
2010-12-01 00:35:33,755 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T cb3c1a5c-4cfa-4bc3-879b-9f4ea2bbae25 ['01dc4fd5-64e5-410e-83ba-1a8a54f9d134'::'67f8a3c1-0b1a-4b03-a705-cdbd5521ae24'] ''Projects/ShawnaLee/current'' | Called merge_directory (In: T:SERVER:T)
2010-12-01 00:37:13,979 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=548 miss=87) ----
2010-12-01 00:39:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:41:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:43:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:45:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:47:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:49:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:51:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:53:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:55:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:57:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 00:59:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 01:01:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
2010-12-01 01:03:13,978 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=556 miss=87) ----
```

I see there is a section where it failed at /home/drew/Documents but I included everything to make sure I didn't forget/miss something.

---

### Post by rtg on 2010-12-02
Hello,

Could you please check refreshing the volume list? 

u1sdtool in ubuntu 10.04 does not have --refresh-volumes command but it can be done using
```

dbus-send --session --dest=com.ubuntuone.SyncDaemon --print-reply /folders com.ubuntuone.SyncDaemon.Folders.refresh_volumes

```

Then please check whether u1sdtool --list-folders lists Documents as subscribed and there are no more errors.

---

### Post by Dragonbite on 2010-12-02
Ok, I ran the code you provided```
$ dbus-send --session --dest=com.ubuntuone.SyncDaemon --print-reply /folders com.ubuntuone.SyncDaemon.Folders.refresh_volumes
method return sender=:1.80 -> dest=:1.87 reply_serial=2
```

But what looks more telling is the result of the folderlist```
$ u1sdtool --list-folders
Folder list:
  id=01dc4fd5-64e5-410e-83ba-1a8a54f9d134 subscribed=True path=/home/drew/Projects
  id=8a0c55a4-5960-4507-9431-cfea500c5d67 subscribed=True path=/home/drew/.ubuntuone/Purchased from Ubuntu One
  id=8f19bc5e-67a5-4601-9dd0-443add731971 subscribed= path=/home/drew/Documents
  id=25daa7ba-76a1-4987-be6f-e043729ddae6 subscribed=True path=/home/drew/Public

```

There is a missing "subscribed=True" for the folder giving me difficulty (actually, just the "True" part is missing).  Is this in a config file somewhere where I can manually make the change, or where do I go from here?

---

### Post by Dragonbite on 2010-12-06
Just as a quick update, Ubuntu 10.04 on my laptop still does not sync the ~/Documents folder.  

Ubuntu 10.10, so far, appears to be syncing properly.

Unfortunately, due to hardware issues I need to keep Ubuntu 10.04 on my laptop (which is the one that isn't working).

Any other ideas?

---

