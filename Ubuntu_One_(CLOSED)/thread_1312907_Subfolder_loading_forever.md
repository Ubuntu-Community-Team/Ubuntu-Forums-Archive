---
title: "Subfolder loading forever"
date: 2009-11-03
forum: Ubuntu One (CLOSED)
---

### Post by GabrielWolff on 2009-11-03
When trying to open a subfolder in Ubuntu One (Ubuntu One/Noten), it will show seven files and continue loading forever, while in the folder there are actually 14 files. 

When on the directory level above (Ubuntu One), it will show next to the folder Noten, that it contains 14 files.

Via the browser it shows all the files.

How come? How do I fix it?

G

---

### Post by James Henstridge on 2009-11-04
It take it you're talking about browsing the Ubuntu One folder with the file manager right?

What you see there is a replicated version of what is stored on our systems.  If some files have not shown up locally yet, it could indicate a problem with the synchronisation process.  If that's the case, then waiting longer won't cause the files to appear.

A few things you could check include:

1. Does the button on t he brown "Ubuntu One File Sharing" bar that appears at the top of the file manager window when browsing the Ubuntu One folder say "Connect" or "Disconnect"?  If it says "Connect", does clicking it help?

2. The Ubuntu One synchronisation daemon needs to be running in order for files to synchronise.  If you open the System Monitor (System -> Administration -> System Monitor), do you see ubuntuone-syncdaemon on the processes tab?

3. The synchronisation daemon keeps log files in ~/.cache/ubuntuone/log.  Do you see anything interesting in those files?

---

### Post by GabrielWolff on 2009-11-04
> **James Henstridge said:**
> 1. Does the button on t he brown "Ubuntu One File Sharing" bar that appears at the top of the file manager window when browsing the Ubuntu One folder say "Connect" or "Disconnect"?  If it says "Connect", does clicking it help?

2. The Ubuntu One synchronisation daemon needs to be running in order for files to synchronise.  If you open the System Monitor (System -> Administration -> System Monitor), do you see ubuntuone-syncdaemon on the processes tab?

3. The synchronisation daemon keeps log files in ~/.cache/ubuntuone/log.  Do you see anything interesting in those files?

1: It's connected, the button says "Disconnect"
2: The ubuntuone-syncdaemon runs.
3: In ~/.cache/ubuntuone/log/syncdaemon.log.2009-11-02_13-38-19 I see a few things that catch my attention, but I'm not quite sure which are actually those that matter. The file looks like this: ```
2009-11-02 13:38:24,248 - ubuntuone.SyncDaemon.fsm - INFO - loading metadata from old version None
2009-11-02 13:38:24,249 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 0, idx_node_id: 0, shares: 0
2009-11-02 13:38:24,347 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2009-11-02 13:38:25,435 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2009-11-02 13:38:25,435 - ubuntuone.SyncDaemon.Main - INFO - Using /home/gabriel/Ubuntu One as root dir
2009-11-02 13:38:25,435 - ubuntuone.SyncDaemon.Main - INFO - Using /home/gabriel/.local/share/ubuntuone/syncdaemon as data dir
2009-11-02 13:38:25,435 - ubuntuone.SyncDaemon.Main - INFO - Using /home/gabriel/.local/share/ubuntuone/shares as shares root dir
2009-11-02 13:38:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: INIT; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=0 miss=0) ----
2009-11-02 13:38:25,437 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2009-11-02 13:38:25,437 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all shares
2009-11-02 13:38:25,438 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2009-11-02 13:38:25,439 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2009-11-02 13:38:25,439 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2009-11-02 13:40:07,208 - ubuntuone.SyncDaemon.ActionQueue - INFO - Protocol version OK
2009-11-02 13:40:08,635 - ubuntuone.SyncDaemon.ActionQueue - INFO - Oauth OK
2009-11-02 13:40:09,196 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: will query 1 objects
2009-11-02 13:40:09,851 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T e690e341-9f7d-49c4-b2a5-b224a13dbe71 [root:ff62649e-0379-42b8-86ad-615de6e84d97] ''/home/gabriel/Ubuntu One'' | Called get_dir (In: T:NONE:T)
2009-11-02 13:40:09,853 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: done
2009-11-02 13:40:12,722 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T e690e341-9f7d-49c4-b2a5-b224a13dbe71 [root:ff62649e-0379-42b8-86ad-615de6e84d97] ''/home/gabriel/Ubuntu One'' | Called merge_directory (In: T:SERVER:T)
2009-11-02 13:40:12,860 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 3068907a-5714-493d-bbc4-da26402411b6 [root:6f5597d1-7bd9-4008-9fc0-9aeab0737886] ''Ubuntu One/Mumuki vln solo.mp3'' | Called new_file (In: F:NA:NA)
2009-11-02 13:40:12,893 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T ceae8349-003d-403d-aa47-b7b4645ac000 [root:d7246541-674e-484a-b683-ab7c8f9e2477] ''Ubuntu One/Transcription'' | Called new_dir (In: F:NA:NA)
2009-11-02 13:40:12,904 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T ceae8349-003d-403d-aa47-b7b4645ac000 [root:d7246541-674e-484a-b683-ab7c8f9e2477] ''Ubuntu One/Transcription'' | Called nothing (In: T:NONE:T)
2009-11-02 13:40:13,580 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 3068907a-5714-493d-bbc4-da26402411b6 [root:6f5597d1-7bd9-4008-9fc0-9aeab0737886] ''Ubuntu One/Mumuki vln solo.mp3'' | Called get_file (In: T:NONE:F)
2009-11-02 13:40:16,399 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T ceae8349-003d-403d-aa47-b7b4645ac000 [root:d7246541-674e-484a-b683-ab7c8f9e2477] ''Ubuntu One/Transcription'' | Called get_dir (In: T:NONE:T)
2009-11-02 13:40:17,679 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 3068907a-5714-493d-bbc4-da26402411b6 [root:6f5597d1-7bd9-4008-9fc0-9aeab0737886] ''Ubuntu One/Mumuki vln solo.mp3'' | Called commit_file (In: T:SERVER:F)
2009-11-02 13:40:18,989 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T ceae8349-003d-403d-aa47-b7b4645ac000 [root:d7246541-674e-484a-b683-ab7c8f9e2477] ''Ubuntu One/Transcription'' | Called merge_directory (In: T:SERVER:T)
2009-11-02 13:40:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=394 miss=3) ----
2009-11-02 13:40:52,194 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - [-:-] ''/home/gabriel/Ubuntu One/Mumuki vln solo.mp3'' | Called delete_on_server (In: T:NONE:F)
2009-11-02 13:41:03,161 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - [:6f5597d1-7bd9-4008-9fc0-9aeab0737886] ''-'' | Called remove_trash (In: F:NA:NA)
2009-11-02 13:42:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=422 miss=3) ----
2009-11-02 13:44:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=422 miss=3) ----
2009-11-02 13:46:25,440 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=422 miss=3) ----
2009-11-02 13:48:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=422 miss=3) ----
2009-11-02 13:50:20,958 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 2fcdd54c-6298-4720-9c9e-a63c7ca8b6d4 [root:2fcdd54c-6298-4720-9c9e-a63c7ca8b6d4] ''Ubuntu One/Transcription/Mumuki solo.sib'' | Called new_local_file (In: F:NA:NA)
2009-11-02 13:50:20,963 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 2fcdd54c-6298-4720-9c9e-a63c7ca8b6d4 [root:2fcdd54c-6298-4720-9c9e-a63c7ca8b6d4] ''Ubuntu One/Transcription/Mumuki solo.sib'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 13:50:20,966 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F f3283ff1-3641-44f9-a8a1-9efd5de147e9 [root:f3283ff1-3641-44f9-a8a1-9efd5de147e9] ''Ubuntu One/Transcription/Nuestro Tiempo.sib'' | Called new_local_file (In: F:NA:NA)
2009-11-02 13:50:20,968 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F f3283ff1-3641-44f9-a8a1-9efd5de147e9 [root:f3283ff1-3641-44f9-a8a1-9efd5de147e9] ''Ubuntu One/Transcription/Nuestro Tiempo.sib'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 13:50:20,995 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 2fcdd54c-6298-4720-9c9e-a63c7ca8b6d4 [root:2fcdd54c-6298-4720-9c9e-a63c7ca8b6d4] ''Ubuntu One/Transcription/Mumuki solo.sib'' | Called put_file (In: T:NONE:F)
2009-11-02 13:50:20,998 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F f3283ff1-3641-44f9-a8a1-9efd5de147e9 [root:f3283ff1-3641-44f9-a8a1-9efd5de147e9] ''Ubuntu One/Transcription/Nuestro Tiempo.sib'' | Called put_file (In: T:NONE:F)
2009-11-02 13:50:21,889 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 2fcdd54c-6298-4720-9c9e-a63c7ca8b6d4 [root:0413f2c5-49a8-4dc9-9e2c-f2bea4689270] ''Ubuntu One/Transcription/Mumuki solo.sib'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 13:50:23,799 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F f3283ff1-3641-44f9-a8a1-9efd5de147e9 [root:19b705e6-e281-45c9-a938-19ced3da929e] ''Ubuntu One/Transcription/Nuestro Tiempo.sib'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 13:50:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: WORKING_ON_CONTENT; queues: metadata: 0; content: 1; hash: 0, fsm-cache: hit=733 miss=5) ----
2009-11-02 13:50:27,748 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 2fcdd54c-6298-4720-9c9e-a63c7ca8b6d4 [root:0413f2c5-49a8-4dc9-9e2c-f2bea4689270] ''Ubuntu One/Transcription/Mumuki solo.sib'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 13:50:28,889 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F f36d6044-d303-46a0-8409-376d7b1b75bc [root:f36d6044-d303-46a0-8409-376d7b1b75bc] ''Ubuntu One/Transcription/PDF Nuestro Tiempo.pdf'' | Called new_local_file (In: F:NA:NA)
2009-11-02 13:50:28,893 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F f36d6044-d303-46a0-8409-376d7b1b75bc [root:f36d6044-d303-46a0-8409-376d7b1b75bc] ''Ubuntu One/Transcription/PDF Nuestro Tiempo.pdf'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 13:50:28,929 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F f36d6044-d303-46a0-8409-376d7b1b75bc [root:f36d6044-d303-46a0-8409-376d7b1b75bc] ''Ubuntu One/Transcription/PDF Nuestro Tiempo.pdf'' | Called put_file (In: T:NONE:F)
2009-11-02 13:50:30,321 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F f36d6044-d303-46a0-8409-376d7b1b75bc [root:03d729d7-503e-4a17-8ca0-9ca3118ac8fb] ''Ubuntu One/Transcription/PDF Nuestro Tiempo.pdf'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 13:50:30,859 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F f3283ff1-3641-44f9-a8a1-9efd5de147e9 [root:19b705e6-e281-45c9-a938-19ced3da929e] ''Ubuntu One/Transcription/Nuestro Tiempo.sib'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 13:50:33,920 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F f36d6044-d303-46a0-8409-376d7b1b75bc [root:03d729d7-503e-4a17-8ca0-9ca3118ac8fb] ''Ubuntu One/Transcription/PDF Nuestro Tiempo.pdf'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 13:50:39,934 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 441042e8-eb80-43a9-9cd2-4fedd5daf798 [root:441042e8-eb80-43a9-9cd2-4fedd5daf798] ''Ubuntu One/Transcription/One who knows.odt'' | Called new_local_file (In: F:NA:NA)
2009-11-02 13:50:39,944 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 441042e8-eb80-43a9-9cd2-4fedd5daf798 [root:441042e8-eb80-43a9-9cd2-4fedd5daf798] ''Ubuntu One/Transcription/One who knows.odt'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 13:50:39,960 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 441042e8-eb80-43a9-9cd2-4fedd5daf798 [root:441042e8-eb80-43a9-9cd2-4fedd5daf798] ''Ubuntu One/Transcription/One who knows.odt'' | Called put_file (In: T:NONE:F)
2009-11-02 13:50:42,211 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 441042e8-eb80-43a9-9cd2-4fedd5daf798 [root:5eca05cc-7ba8-4778-a023-a2054cc20aa3] ''Ubuntu One/Transcription/One who knows.odt'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 13:50:42,415 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ab95b13c-bb50-4852-af02-26db972b482c [root:ab95b13c-bb50-4852-af02-26db972b482c] ''Ubuntu One/Transcription/One Who Knows lyrics.pdf'' | Called new_local_file (In: F:NA:NA)
2009-11-02 13:50:42,424 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ab95b13c-bb50-4852-af02-26db972b482c [root:ab95b13c-bb50-4852-af02-26db972b482c] ''Ubuntu One/Transcription/One Who Knows lyrics.pdf'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 13:50:42,531 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F ab95b13c-bb50-4852-af02-26db972b482c [root:ab95b13c-bb50-4852-af02-26db972b482c] ''Ubuntu One/Transcription/One Who Knows lyrics.pdf'' | Called put_file (In: T:NONE:F)
2009-11-02 13:50:44,684 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F ab95b13c-bb50-4852-af02-26db972b482c [root:8bdb9fed-e30d-49b2-a429-9d3958fbf00c] ''Ubuntu One/Transcription/One Who Knows lyrics.pdf'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 13:50:45,428 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 441042e8-eb80-43a9-9cd2-4fedd5daf798 [root:5eca05cc-7ba8-4778-a023-a2054cc20aa3] ''Ubuntu One/Transcription/One who knows.odt'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 13:51:00,870 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ab95b13c-bb50-4852-af02-26db972b482c [root:8bdb9fed-e30d-49b2-a429-9d3958fbf00c] ''Ubuntu One/Transcription/One Who Knows lyrics.pdf'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 13:51:10,413 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 9443d771-f00d-46b1-bada-c16045e74951 [root:9443d771-f00d-46b1-bada-c16045e74951] ''Ubuntu One/Transcription/04 La VI LLegar (Tango).mp3'' | Called new_local_file (In: F:NA:NA)
2009-11-02 13:51:10,417 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 9443d771-f00d-46b1-bada-c16045e74951 [root:9443d771-f00d-46b1-bada-c16045e74951] ''Ubuntu One/Transcription/04 La VI LLegar (Tango).mp3'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 13:51:11,124 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 9443d771-f00d-46b1-bada-c16045e74951 [root:9443d771-f00d-46b1-bada-c16045e74951] ''Ubuntu One/Transcription/04 La VI LLegar (Tango).mp3'' | Called put_file (In: T:NONE:F)
2009-11-02 13:51:11,757 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 9443d771-f00d-46b1-bada-c16045e74951 [root:4adddfed-ec23-480a-b293-6f19ff7de55a] ''Ubuntu One/Transcription/04 La VI LLegar (Tango).mp3'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 13:52:08,258 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 9443d771-f00d-46b1-bada-c16045e74951 [root:4adddfed-ec23-480a-b293-6f19ff7de55a] ''Ubuntu One/Transcription/04 La VI LLegar (Tango).mp3'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 13:52:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 13:54:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 13:56:25,456 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 13:58:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 14:00:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 14:02:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 14:04:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 14:06:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 14:08:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 14:10:25,439 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1618 miss=9) ----
2009-11-02 14:12:23,708 - ubuntuone.SyncDaemon.fsm - WARNING - OSError [Errno 2] No such file or directory: '/home/gabriel/.cache/ubuntuone/partials/e690e341-9f7d-49c4-b2a5-b224a13dbe71.u1partial.Ubuntu One' when trying to remove partial_path '/home/gabriel/.cache/ubuntuone/partials/e690e341-9f7d-49c4-b2a5-b224a13dbe71.u1partial.Ubuntu One'
2009-11-02 14:12:23,777 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T ceae8349-003d-403d-aa47-b7b4645ac000 [root:d7246541-674e-484a-b683-ab7c8f9e2477] ''Ubuntu One/Noten'' | Called client_moved (In: T:NONE:T)
2009-11-02 14:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: START_WORKING_ON_METADATA; queues: metadata: 1; content: 0; hash: 0, fsm-cache: hit=1677 miss=9) ----
2009-11-02 14:12:26,900 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T e690e341-9f7d-49c4-b2a5-b224a13dbe71 [root:ff62649e-0379-42b8-86ad-615de6e84d97] ''/home/gabriel/Ubuntu One'' | Called get_dir (In: T:NONE:T)
2009-11-02 14:12:27,831 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T e690e341-9f7d-49c4-b2a5-b224a13dbe71 [root:ff62649e-0379-42b8-86ad-615de6e84d97] ''/home/gabriel/Ubuntu One'' | Called merge_directory (In: T:SERVER:T)
2009-11-02 14:12:32,184 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F b8b7523c-b979-47d7-a01b-f1fc78399b7b [root:b8b7523c-b979-47d7-a01b-f1fc78399b7b] ''Ubuntu One/Noten/Emil_Alle_Noten_je.pdf'' | Called new_local_file (In: F:NA:NA)
2009-11-02 14:12:32,188 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F b8b7523c-b979-47d7-a01b-f1fc78399b7b [root:b8b7523c-b979-47d7-a01b-f1fc78399b7b] ''Ubuntu One/Noten/Emil_Alle_Noten_je.pdf'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 14:12:33,004 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F b8b7523c-b979-47d7-a01b-f1fc78399b7b [root:b8b7523c-b979-47d7-a01b-f1fc78399b7b] ''Ubuntu One/Noten/Emil_Alle_Noten_je.pdf'' | Called put_file (In: T:NONE:F)
2009-11-02 14:12:33,336 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F b8b7523c-b979-47d7-a01b-f1fc78399b7b [root:189ee268-e7de-45a0-a1eb-f65a671f521e] ''Ubuntu One/Noten/Emil_Alle_Noten_je.pdf'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 14:12:39,573 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F bccb46a7-e6ef-425d-8697-b829025693fd [root:bccb46a7-e6ef-425d-8697-b829025693fd] ''Ubuntu One/Noten/Klezmer Music Short History.pdf'' | Called new_local_file (In: F:NA:NA)
2009-11-02 14:12:39,592 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F bccb46a7-e6ef-425d-8697-b829025693fd [root:bccb46a7-e6ef-425d-8697-b829025693fd] ''Ubuntu One/Noten/Klezmer Music Short History.pdf'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 14:12:39,626 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F bccb46a7-e6ef-425d-8697-b829025693fd [root:bccb46a7-e6ef-425d-8697-b829025693fd] ''Ubuntu One/Noten/Klezmer Music Short History.pdf'' | Called put_file (In: T:NONE:F)
2009-11-02 14:12:43,271 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F bccb46a7-e6ef-425d-8697-b829025693fd [root:5d6c1010-12ac-4283-bfcf-9ae2c720ee66] ''Ubuntu One/Noten/Klezmer Music Short History.pdf'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 14:12:44,127 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 931308b2-cad9-4f7c-8460-0fb29a126762 [root:931308b2-cad9-4f7c-8460-0fb29a126762] ''Ubuntu One/Noten/Metallica - Black Album.pdf'' | Called new_local_file (In: F:NA:NA)
2009-11-02 14:12:44,134 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 931308b2-cad9-4f7c-8460-0fb29a126762 [root:931308b2-cad9-4f7c-8460-0fb29a126762] ''Ubuntu One/Noten/Metallica - Black Album.pdf'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 14:12:44,924 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 931308b2-cad9-4f7c-8460-0fb29a126762 [root:931308b2-cad9-4f7c-8460-0fb29a126762] ''Ubuntu One/Noten/Metallica - Black Album.pdf'' | Called put_file (In: T:NONE:F)
2009-11-02 14:12:46,692 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F b20a3fbc-6cea-406b-89f0-f9617ccb80f2 [root:b20a3fbc-6cea-406b-89f0-f9617ccb80f2] ''Ubuntu One/Noten/Metallica - Black Album.tif'' | Called new_local_file (In: F:NA:NA)
2009-11-02 14:12:46,694 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F b20a3fbc-6cea-406b-89f0-f9617ccb80f2 [root:b20a3fbc-6cea-406b-89f0-f9617ccb80f2] ''Ubuntu One/Noten/Metallica - Black Album.tif'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 14:12:46,709 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F b20a3fbc-6cea-406b-89f0-f9617ccb80f2 [root:b20a3fbc-6cea-406b-89f0-f9617ccb80f2] ''Ubuntu One/Noten/Metallica - Black Album.tif'' | Called put_file (In: T:NONE:F)
2009-11-02 14:12:48,424 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 931308b2-cad9-4f7c-8460-0fb29a126762 [root:6ad7246b-1eea-4a38-874b-5108ea8eb45b] ''Ubuntu One/Noten/Metallica - Black Album.pdf'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 14:12:49,140 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F d6a2b751-d714-4a73-b9bd-0cd4370cdba2 [root:d6a2b751-d714-4a73-b9bd-0cd4370cdba2] ''Ubuntu One/Noten/Macedonia D'' | Called new_local_file (In: F:NA:NA)
2009-11-02 14:12:49,141 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F d6a2b751-d714-4a73-b9bd-0cd4370cdba2 [root:d6a2b751-d714-4a73-b9bd-0cd4370cdba2] ''Ubuntu One/Noten/Macedonia D'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 14:12:49,148 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F d6a2b751-d714-4a73-b9bd-0cd4370cdba2 [root:d6a2b751-d714-4a73-b9bd-0cd4370cdba2] ''Ubuntu One/Noten/Macedonia D'' | Called put_file (In: T:NONE:F)
2009-11-02 14:12:51,832 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F b20a3fbc-6cea-406b-89f0-f9617ccb80f2 [root:9ba01989-d0fd-4a03-9978-030b4797ca4a] ''Ubuntu One/Noten/Metallica - Black Album.tif'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 14:12:55,280 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F d6a2b751-d714-4a73-b9bd-0cd4370cdba2 [root:8dfd4fe3-7228-4a6d-a0c4-e772969d19dc] ''Ubuntu One/Noten/Macedonia D'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 14:13:03,905 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ba4fb518-adc1-4bcb-9fbb-583e0f96cded [root:ba4fb518-adc1-4bcb-9fbb-583e0f96cded] ''Ubuntu One/Noten/Think transc..odt'' | Called new_local_file (In: F:NA:NA)
2009-11-02 14:13:03,909 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ba4fb518-adc1-4bcb-9fbb-583e0f96cded [root:ba4fb518-adc1-4bcb-9fbb-583e0f96cded] ''Ubuntu One/Noten/Think transc..odt'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 14:13:03,927 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F ba4fb518-adc1-4bcb-9fbb-583e0f96cded [root:ba4fb518-adc1-4bcb-9fbb-583e0f96cded] ''Ubuntu One/Noten/Think transc..odt'' | Called put_file (In: T:NONE:F)
2009-11-02 14:13:07,348 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F ba4fb518-adc1-4bcb-9fbb-583e0f96cded [root:4f7497db-e316-40d2-a3cd-3f2164915227] ''Ubuntu One/Noten/Think transc..odt'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 14:13:20,466 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 31f3b57a-f175-456a-9a57-56c42b476426 [root:31f3b57a-f175-456a-9a57-56c42b476426] ''Ubuntu One/Noten/How to Practice.pdf'' | Called new_local_file (In: F:NA:NA)
2009-11-02 14:13:20,471 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 31f3b57a-f175-456a-9a57-56c42b476426 [root:31f3b57a-f175-456a-9a57-56c42b476426] ''Ubuntu One/Noten/How to Practice.pdf'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 14:13:20,503 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 31f3b57a-f175-456a-9a57-56c42b476426 [root:31f3b57a-f175-456a-9a57-56c42b476426] ''Ubuntu One/Noten/How to Practice.pdf'' | Called put_file (In: T:NONE:F)
2009-11-02 14:13:24,461 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 31f3b57a-f175-456a-9a57-56c42b476426 [root:ce213288-5019-4c87-879b-36d8819e60a5] ''Ubuntu One/Noten/How to Practice.pdf'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 14:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: WORKING_ON_CONTENT; queues: metadata: 0; content: 6; hash: 0, fsm-cache: hit=2872 miss=16) ----
2009-11-02 14:16:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: WORKING_ON_CONTENT; queues: metadata: 0; content: 6; hash: 0, fsm-cache: hit=2872 miss=16) ----
2009-11-02 14:18:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: WORKING_ON_CONTENT; queues: metadata: 0; content: 6; hash: 0, fsm-cache: hit=2872 miss=16) ----
2009-11-02 14:19:59,983 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F b8b7523c-b979-47d7-a01b-f1fc78399b7b [root:189ee268-e7de-45a0-a1eb-f65a671f521e] ''Ubuntu One/Noten/Emil_Alle_Noten_je.pdf'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 14:20:02,652 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F bccb46a7-e6ef-425d-8697-b829025693fd [root:5d6c1010-12ac-4283-bfcf-9ae2c720ee66] ''Ubuntu One/Noten/Klezmer Music Short History.pdf'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 14:20:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: START_WORKING_ON_CONTENT; queues: metadata: 0; content: 4; hash: 0, fsm-cache: hit=2962 miss=16) ----
2009-11-02 14:22:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: START_WORKING_ON_CONTENT; queues: metadata: 0; content: 4; hash: 0, fsm-cache: hit=2962 miss=16) ----
2009-11-02 14:24:22,855 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 931308b2-cad9-4f7c-8460-0fb29a126762 [root:6ad7246b-1eea-4a38-874b-5108ea8eb45b] ''Ubuntu One/Noten/Metallica - Black Album.pdf'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 14:24:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: START_WORKING_ON_CONTENT; queues: metadata: 0; content: 3; hash: 0, fsm-cache: hit=3007 miss=16) ----
2009-11-02 14:24:29,136 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F b20a3fbc-6cea-406b-89f0-f9617ccb80f2 [root:9ba01989-d0fd-4a03-9978-030b4797ca4a] ''Ubuntu One/Noten/Metallica - Black Album.tif'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 14:24:31,170 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F d6a2b751-d714-4a73-b9bd-0cd4370cdba2 [root:8dfd4fe3-7228-4a6d-a0c4-e772969d19dc] ''Ubuntu One/Noten/Macedonia D'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 14:24:33,613 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ba4fb518-adc1-4bcb-9fbb-583e0f96cded [root:4f7497db-e316-40d2-a3cd-3f2164915227] ''Ubuntu One/Noten/Think transc..odt'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 14:24:36,297 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 31f3b57a-f175-456a-9a57-56c42b476426 [root:ce213288-5019-4c87-879b-36d8819e60a5] ''Ubuntu One/Noten/How to Practice.pdf'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 14:26:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:28:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:30:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:32:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:34:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:36:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:38:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:40:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:42:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:44:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:46:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:48:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:50:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:52:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:54:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:56:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 14:58:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 15:00:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 15:02:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 15:04:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 15:06:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 15:08:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3184 miss=16) ----
2009-11-02 15:09:18,301 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 2ce48cdf-b6ad-48cf-b0b0-9770d2e56678 [root:2ce48cdf-b6ad-48cf-b0b0-9770d2e56678] ''Ubuntu One/Noten/bolotin_BOLOTIN_HoraPico_Cuarteto.pdf'' | Called new_local_file (In: F:NA:NA)
2009-11-02 15:09:18,309 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 2ce48cdf-b6ad-48cf-b0b0-9770d2e56678 [root:2ce48cdf-b6ad-48cf-b0b0-9770d2e56678] ''Ubuntu One/Noten/bolotin_BOLOTIN_HoraPico_Cuarteto.pdf'' | Called calculate_hash (In: T:NONE:F)
2009-11-02 15:09:18,324 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 2ce48cdf-b6ad-48cf-b0b0-9770d2e56678 [root:2ce48cdf-b6ad-48cf-b0b0-9770d2e56678] ''Ubuntu One/Noten/bolotin_BOLOTIN_HoraPico_Cuarteto.pdf'' | Called put_file (In: T:NONE:F)
2009-11-02 15:09:19,521 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 2ce48cdf-b6ad-48cf-b0b0-9770d2e56678 [root:663b64e1-95d9-426c-8363-efb15a8b0fe0] ''Ubuntu One/Noten/bolotin_BOLOTIN_HoraPico_Cuarteto.pdf'' | Called new_local_file_created (In: T:LOCAL:F)
2009-11-02 15:09:29,259 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 2ce48cdf-b6ad-48cf-b0b0-9770d2e56678 [root:663b64e1-95d9-426c-8363-efb15a8b0fe0] ''Ubuntu One/Noten/bolotin_BOLOTIN_HoraPico_Cuarteto.pdf'' | Called commit_upload (In: T:LOCAL:F)
2009-11-02 15:10:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3383 miss=17) ----
2009-11-02 15:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3383 miss=17) ----
2009-11-02 15:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3383 miss=17) ----
2009-11-02 22:32:40,646 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3383 miss=17) ----
2009-11-02 22:32:41,735 - ubuntuone.SyncDaemon.ActionQueue - WARNING - connection lost: Connection was closed cleanly.
2009-11-02 22:32:54,023 - ubuntuone.SyncDaemon.ActionQueue - INFO - SRV lookup error, fallback to 'fs-1.one.ubuntu.com':443 
Traceback (most recent call last):
Failure: twisted.internet.defer.TimeoutError: [Query('_https._tcp.fs.ubuntuone.com', 33, 1)]

2009-11-02 22:32:54,720 - ubuntuone.SyncDaemon.ActionQueue - INFO - Protocol version OK
2009-11-02 22:32:55,634 - ubuntuone.SyncDaemon.ActionQueue - INFO - Oauth OK
2009-11-02 22:32:55,893 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: will query 16 objects
2009-11-02 22:32:56,597 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T ceae8349-003d-403d-aa47-b7b4645ac000 [root:d7246541-674e-484a-b683-ab7c8f9e2477] ''Ubuntu One/Noten'' | Called get_dir (In: T:NONE:T)
2009-11-02 22:32:56,616 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: done
2009-11-02 22:32:58,741 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T ceae8349-003d-403d-aa47-b7b4645ac000 [root:d7246541-674e-484a-b683-ab7c8f9e2477] ''Ubuntu One/Noten'' | Called merge_directory (In: T:SERVER:T)
2009-11-02 22:34:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:36:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:38:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:40:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:42:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:44:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:46:25,446 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:48:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:50:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:52:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:54:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:56:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 22:58:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:00:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:02:25,438 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:04:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:06:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:08:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:10:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:16:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:18:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:20:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:22:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:24:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:26:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:28:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:30:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3547 miss=17) ----
2009-11-02 23:31:58,471 - ubuntuone.SyncDaemon.ActionQueue - WARNING - connection lost: Connection was closed cleanly.
2009-11-02 23:32:06,049 - ubuntuone.SyncDaemon.ActionQueue - INFO - SRV lookup error, fallback to 'fs-1.one.ubuntu.com':443 
Traceback (most recent call last):
Failure: twisted.internet.defer.TimeoutError: [Query('_https._tcp.fs.ubuntuone.com', 33, 1)]

2009-11-02 23:32:06,556 - ubuntuone.SyncDaemon.ActionQueue - INFO - Protocol version OK
2009-11-02 23:32:07,641 - ubuntuone.SyncDaemon.ActionQueue - INFO - Oauth OK
2009-11-02 23:32:07,895 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: will query 16 objects
2009-11-02 23:32:09,045 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: done
2009-11-02 23:32:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3564 miss=17) ----
2009-11-03 08:09:09,781 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3564 miss=17) ----
2009-11-03 08:09:10,173 - ubuntuone.SyncDaemon.ActionQueue - WARNING - connection lost: Connection was closed cleanly.
2009-11-03 08:09:19,028 - ubuntuone.SyncDaemon.ActionQueue - INFO - SRV lookup error, fallback to 'fs-1.one.ubuntu.com':443 
Traceback (most recent call last):
Failure: twisted.internet.defer.TimeoutError: [Query('_https._tcp.fs.ubuntuone.com', 33, 1)]

2009-11-03 08:09:23,522 - ubuntuone.SyncDaemon.ActionQueue - INFO - Protocol version OK
2009-11-03 08:09:24,528 - ubuntuone.SyncDaemon.ActionQueue - INFO - Oauth OK
2009-11-03 08:09:24,774 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: will query 16 objects
2009-11-03 08:09:25,543 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: done
2009-11-03 08:10:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:16:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:18:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:20:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:22:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:24:25,437 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:26:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:28:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:30:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:32:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:34:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:36:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:38:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:40:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:42:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:44:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:46:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:50:37,461 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3581 miss=17) ----
2009-11-03 08:50:37,834 - ubuntuone.SyncDaemon.ActionQueue - WARNING - connection lost: Connection was closed cleanly.
2009-11-03 08:50:46,037 - ubuntuone.SyncDaemon.ActionQueue - INFO - SRV lookup error, fallback to 'fs-1.one.ubuntu.com':443 
Traceback (most recent call last):
Failure: twisted.internet.defer.TimeoutError: [Query('_https._tcp.fs.ubuntuone.com', 33, 1)]

2009-11-03 08:50:47,753 - ubuntuone.SyncDaemon.ActionQueue - INFO - Protocol version OK
2009-11-03 08:50:49,771 - ubuntuone.SyncDaemon.ActionQueue - INFO - Oauth OK
2009-11-03 08:50:50,147 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: will query 16 objects
2009-11-03 08:50:51,402 - ubuntuone.SyncDaemon.ActionQueue - INFO - server rescan: done
2009-11-03 08:52:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 08:54:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 08:56:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 08:58:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:00:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:02:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:04:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:06:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:08:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:10:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:16:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:18:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:20:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:22:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:24:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:26:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:28:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:30:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:32:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:34:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:36:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:38:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:40:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:42:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:44:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:46:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:48:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:50:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:52:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:54:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:56:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 09:58:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:00:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:02:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:04:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:06:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:08:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:10:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:16:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:18:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:20:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:22:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:24:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:26:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:28:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:30:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:32:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:34:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:36:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:38:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:40:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:42:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:44:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:46:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:48:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:50:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:52:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:54:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:56:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 10:58:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:00:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:02:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:04:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:06:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:08:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:10:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:16:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:18:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:20:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:22:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:24:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:26:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:28:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:30:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:32:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:34:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:36:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:38:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:40:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:42:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:44:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:46:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:48:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:50:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:52:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:54:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:56:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 11:58:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:00:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:02:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:04:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:06:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:08:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:10:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:16:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:18:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:20:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:22:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:24:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:26:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:28:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:30:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:32:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:34:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:36:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:38:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:40:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:42:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:44:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:46:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:48:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:50:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:52:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:54:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:56:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 12:58:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:00:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:02:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:04:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:06:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:08:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:10:25,446 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:12:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:14:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:16:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:18:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:20:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:22:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:24:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:26:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:28:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:30:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:32:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:34:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
2009-11-03 13:36:25,436 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: IDLE; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=3598 miss=17) ----
```

Attached is a screenshot

Thanks :)

---

### Post by webm0nk3y on 2009-11-04
I had a similar problem a while back when something caused the metadata locally to get out of whack with what's on the server. I assume this is because I use early alpha versions of the client.

To resolve it I did the following:
[1] Stop the client
[2] mv ~/.local/share/ubuntuone ~/.local/share/ubuntuone_save
[3] mv ~/Ubuntu\ One/ ~/Ubuntu\ One_save
[4] restart the client 

When you restart the client it will pull down the versions of the file on the web. If you have updated versions, you should be able to update them from the ~/Ubuntu\ One_save folder

Hope this helps

---

