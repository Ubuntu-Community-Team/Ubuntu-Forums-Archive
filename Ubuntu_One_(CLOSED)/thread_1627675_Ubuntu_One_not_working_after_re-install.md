---
title: "Ubuntu One not working after re-install"
date: 2010-11-21
forum: Ubuntu One (CLOSED)
---

### Post by ellis rowell on 2010-11-21
After upgrading to Ubuntu v10.10 I had problems with audio, so re-installed v10.04. Now I can't get Ubuntu One synchronising to the computer. I've tried downloading the files but they don't sync. now.

What do I have to do? If I can't get it working then I shall have to revert to saving on Ext HDD's again.

---

### Post by duanedesign on 2010-11-22
ellis,
could you look in ~/.cache/ubuntuone/log/ (you may need to view > show hidden files or ctrl + h to see the .cache directory) and see if you have a file called syncdaemon-exceptions.log. If so could you post it here. Please use the CODE tags. You can wrap your text in Code tags by clicking the # symbol in the Forum post editor.

thank you,
duanedesign

---

### Post by ellis rowell on 2010-11-22
This is the latest log:-
```
2010-11-22 12:55:33,484 - ubuntuone.SyncDaemon.fsm - INFO - loading updated metadata
2010-11-22 12:55:33,516 - ubuntuone.SyncDaemon.fsm - INFO - initialized: idx_path: 12, idx_node_id: 0, shares: 1
2010-11-22 12:55:33,516 - ubuntuone.SyncDaemon.GeneralINotProc - INFO - Ignoring files: ['\\A#.*\\Z', '\\A.*~\\Z', '\\A.*\\.py[oc]\\Z', '\\A.*\\.sw[nopx]\\Z', '\\A.*\\.swpx\\Z', '\\A\\..*\\.tmp\\Z']
2010-11-22 12:55:33,520 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher started
2010-11-22 12:55:34,313 - ubuntuone.SyncDaemon.DBus - INFO - DBusInterface initialized.
2010-11-22 12:55:34,313 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/ellis/Ubuntu One' as root dir
2010-11-22 12:55:34,313 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/ellis/.local/share/ubuntuone/syncdaemon' as data dir
2010-11-22 12:55:34,313 - ubuntuone.SyncDaemon.Main - INFO - Using '/home/ellis/.local/share/ubuntuone/shares' as shares root dir
2010-11-22 12:55:34,314 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'INIT'  (queues IDLE  connection 'Not User Not Network')>; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1 miss=12) ----
2010-11-22 12:55:34,314 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2010-11-22 12:55:34,314 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all volumes
2010-11-22 12:55:34,455 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/Idif Files'' | Calling new_local_dir (got FS_DIR_CREATE:{})
2010-11-22 12:55:34,482 - ubuntuone.SyncDaemon.local_rescan - INFO - scan dir: '/home/ellis/Ubuntu One/Idif Files'  mdid: d9cbe06e-c704-4c8a-bc4d-45a741d0f4b1
2010-11-22 12:55:34,483 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:T d9cbe06e-c704-4c8a-bc4d-45a741d0f4b1 ['root'::marker:d9cbe06e-c704-4c8a-bc4d-45a741d0f4b1] ''Ubuntu One/Idif Files'' | Called new_local_dir (In: F:NA:NA)
2010-11-22 12:55:34,484 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/CTC-C.csv'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,486 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 9942b7e0-63a6-4453-8d6e-fb2aae03d559 ['root'::marker:9942b7e0-63a6-4453-8d6e-fb2aae03d559] ''Ubuntu One/CTC-C.csv'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,487 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 9942b7e0-63a6-4453-8d6e-fb2aae03d559 ['root'::marker:9942b7e0-63a6-4453-8d6e-fb2aae03d559] ''Ubuntu One/CTC-C.csv'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,488 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 9942b7e0-63a6-4453-8d6e-fb2aae03d559 ['root'::marker:9942b7e0-63a6-4453-8d6e-fb2aae03d559] ''Ubuntu One/CTC-C.csv'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,489 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/CTC.ics'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,491 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F e6762066-ba81-407b-a2aa-d59d21842c94 ['root'::marker:e6762066-ba81-407b-a2aa-d59d21842c94] ''Ubuntu One/CTC.ics'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,491 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F e6762066-ba81-407b-a2aa-d59d21842c94 ['root'::marker:e6762066-ba81-407b-a2aa-d59d21842c94] ''Ubuntu One/CTC.ics'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,492 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F e6762066-ba81-407b-a2aa-d59d21842c94 ['root'::marker:e6762066-ba81-407b-a2aa-d59d21842c94] ''Ubuntu One/CTC.ics'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,493 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/Rotation-plan.pdf'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,495 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 7ad746a8-f4df-46f2-bed3-161f3c9f5e08 ['root'::marker:7ad746a8-f4df-46f2-bed3-161f3c9f5e08] ''Ubuntu One/Rotation-plan.pdf'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,496 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 7ad746a8-f4df-46f2-bed3-161f3c9f5e08 ['root'::marker:7ad746a8-f4df-46f2-bed3-161f3c9f5e08] ''Ubuntu One/Rotation-plan.pdf'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,498 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 7ad746a8-f4df-46f2-bed3-161f3c9f5e08 ['root'::marker:7ad746a8-f4df-46f2-bed3-161f3c9f5e08] ''Ubuntu One/Rotation-plan.pdf'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,499 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/VegetableRotation.pdf'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,500 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F cefe554d-35fd-4fc2-bc91-c89a4126d403 ['root'::marker:cefe554d-35fd-4fc2-bc91-c89a4126d403] ''Ubuntu One/VegetableRotation.pdf'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,501 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F cefe554d-35fd-4fc2-bc91-c89a4126d403 ['root'::marker:cefe554d-35fd-4fc2-bc91-c89a4126d403] ''Ubuntu One/VegetableRotation.pdf'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,502 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F cefe554d-35fd-4fc2-bc91-c89a4126d403 ['root'::marker:cefe554d-35fd-4fc2-bc91-c89a4126d403] ''Ubuntu One/VegetableRotation.pdf'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,503 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/spring2010bulletin.pdf'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,505 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 86842880-9465-4d4d-bb7c-9d90cd69f28b ['root'::marker:86842880-9465-4d4d-bb7c-9d90cd69f28b] ''Ubuntu One/spring2010bulletin.pdf'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,506 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 86842880-9465-4d4d-bb7c-9d90cd69f28b ['root'::marker:86842880-9465-4d4d-bb7c-9d90cd69f28b] ''Ubuntu One/spring2010bulletin.pdf'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,507 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 86842880-9465-4d4d-bb7c-9d90cd69f28b ['root'::marker:86842880-9465-4d4d-bb7c-9d90cd69f28b] ''Ubuntu One/spring2010bulletin.pdf'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,508 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/University.ics'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,513 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 14ddf822-a676-4abb-a907-ed09e4340aec ['root'::marker:14ddf822-a676-4abb-a907-ed09e4340aec] ''Ubuntu One/University.ics'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,513 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 14ddf822-a676-4abb-a907-ed09e4340aec ['root'::marker:14ddf822-a676-4abb-a907-ed09e4340aec] ''Ubuntu One/University.ics'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,514 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 14ddf822-a676-4abb-a907-ed09e4340aec ['root'::marker:14ddf822-a676-4abb-a907-ed09e4340aec] ''Ubuntu One/University.ics'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,515 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/Joyce.ics'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,519 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ea35c16d-146d-4559-b83d-66a87d03e187 ['root'::marker:ea35c16d-146d-4559-b83d-66a87d03e187] ''Ubuntu One/Joyce.ics'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,520 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ea35c16d-146d-4559-b83d-66a87d03e187 ['root'::marker:ea35c16d-146d-4559-b83d-66a87d03e187] ''Ubuntu One/Joyce.ics'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,521 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ea35c16d-146d-4559-b83d-66a87d03e187 ['root'::marker:ea35c16d-146d-4559-b83d-66a87d03e187] ''Ubuntu One/Joyce.ics'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,522 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/Peter.ics'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,530 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 47831bcb-3b6a-400b-ba62-a6560bb1e95f ['root'::marker:47831bcb-3b6a-400b-ba62-a6560bb1e95f] ''Ubuntu One/Peter.ics'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,531 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 47831bcb-3b6a-400b-ba62-a6560bb1e95f ['root'::marker:47831bcb-3b6a-400b-ba62-a6560bb1e95f] ''Ubuntu One/Peter.ics'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,531 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 47831bcb-3b6a-400b-ba62-a6560bb1e95f ['root'::marker:47831bcb-3b6a-400b-ba62-a6560bb1e95f] ''Ubuntu One/Peter.ics'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,532 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/Home.ics'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,533 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F fd8b6895-f157-44b4-91f8-cbcb8ccf9222 ['root'::marker:fd8b6895-f157-44b4-91f8-cbcb8ccf9222] ''Ubuntu One/Home.ics'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,534 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F fd8b6895-f157-44b4-91f8-cbcb8ccf9222 ['root'::marker:fd8b6895-f157-44b4-91f8-cbcb8ccf9222] ''Ubuntu One/Home.ics'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,535 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F fd8b6895-f157-44b4-91f8-cbcb8ccf9222 ['root'::marker:fd8b6895-f157-44b4-91f8-cbcb8ccf9222] ''Ubuntu One/Home.ics'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,536 - ubuntuone.SyncDaemon.sync - INFO - -:-:- - ['-'::'-'] ''/home/ellis/Ubuntu One/Macug.ics'' | Calling new_local_file (got FS_FILE_CREATE:{})
2010-11-22 12:55:34,537 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 85ad051f-fd83-4043-b3e9-ddbeb887647a ['root'::marker:85ad051f-fd83-4043-b3e9-ddbeb887647a] ''Ubuntu One/Macug.ics'' | Called new_local_file (In: F:NA:NA)
2010-11-22 12:55:34,538 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 85ad051f-fd83-4043-b3e9-ddbeb887647a ['root'::marker:85ad051f-fd83-4043-b3e9-ddbeb887647a] ''Ubuntu One/Macug.ics'' | Calling calculate_hash (got FS_FILE_CLOSE_WRITE:{})
2010-11-22 12:55:34,539 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 85ad051f-fd83-4043-b3e9-ddbeb887647a ['root'::marker:85ad051f-fd83-4043-b3e9-ddbeb887647a] ''Ubuntu One/Macug.ics'' | Called calculate_hash (In: T:NONE:F)
2010-11-22 12:55:34,540 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 9942b7e0-63a6-4453-8d6e-fb2aae03d559 ['root'::marker:9942b7e0-63a6-4453-8d6e-fb2aae03d559] ''Ubuntu One/CTC-C.csv'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,541 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 4025 bytes (available: None)
2010-11-22 12:55:34,541 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 9942b7e0-63a6-4453-8d6e-fb2aae03d559 ['root'::marker:9942b7e0-63a6-4453-8d6e-fb2aae03d559] ''Ubuntu One/CTC-C.csv'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,542 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F e6762066-ba81-407b-a2aa-d59d21842c94 ['root'::marker:e6762066-ba81-407b-a2aa-d59d21842c94] ''Ubuntu One/CTC.ics'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,543 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 22105 bytes (available: None)
2010-11-22 12:55:34,544 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F e6762066-ba81-407b-a2aa-d59d21842c94 ['root'::marker:e6762066-ba81-407b-a2aa-d59d21842c94] ''Ubuntu One/CTC.ics'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,545 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 7ad746a8-f4df-46f2-bed3-161f3c9f5e08 ['root'::marker:7ad746a8-f4df-46f2-bed3-161f3c9f5e08] ''Ubuntu One/Rotation-plan.pdf'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,546 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 208463 bytes (available: None)
2010-11-22 12:55:34,546 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 7ad746a8-f4df-46f2-bed3-161f3c9f5e08 ['root'::marker:7ad746a8-f4df-46f2-bed3-161f3c9f5e08] ''Ubuntu One/Rotation-plan.pdf'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,547 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F cefe554d-35fd-4fc2-bc91-c89a4126d403 ['root'::marker:cefe554d-35fd-4fc2-bc91-c89a4126d403] ''Ubuntu One/VegetableRotation.pdf'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,548 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 210856 bytes (available: None)
2010-11-22 12:55:34,549 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F cefe554d-35fd-4fc2-bc91-c89a4126d403 ['root'::marker:cefe554d-35fd-4fc2-bc91-c89a4126d403] ''Ubuntu One/VegetableRotation.pdf'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,550 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 86842880-9465-4d4d-bb7c-9d90cd69f28b ['root'::marker:86842880-9465-4d4d-bb7c-9d90cd69f28b] ''Ubuntu One/spring2010bulletin.pdf'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,550 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 2430542 bytes (available: None)
2010-11-22 12:55:34,551 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 86842880-9465-4d4d-bb7c-9d90cd69f28b ['root'::marker:86842880-9465-4d4d-bb7c-9d90cd69f28b] ''Ubuntu One/spring2010bulletin.pdf'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,552 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 14ddf822-a676-4abb-a907-ed09e4340aec ['root'::marker:14ddf822-a676-4abb-a907-ed09e4340aec] ''Ubuntu One/University.ics'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,553 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 26738 bytes (available: None)
2010-11-22 12:55:34,553 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 14ddf822-a676-4abb-a907-ed09e4340aec ['root'::marker:14ddf822-a676-4abb-a907-ed09e4340aec] ''Ubuntu One/University.ics'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,554 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F ea35c16d-146d-4559-b83d-66a87d03e187 ['root'::marker:ea35c16d-146d-4559-b83d-66a87d03e187] ''Ubuntu One/Joyce.ics'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,555 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 4591 bytes (available: None)
2010-11-22 12:55:34,556 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F ea35c16d-146d-4559-b83d-66a87d03e187 ['root'::marker:ea35c16d-146d-4559-b83d-66a87d03e187] ''Ubuntu One/Joyce.ics'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,557 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 47831bcb-3b6a-400b-ba62-a6560bb1e95f ['root'::marker:47831bcb-3b6a-400b-ba62-a6560bb1e95f] ''Ubuntu One/Peter.ics'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,557 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 7114 bytes (available: None)
2010-11-22 12:55:34,558 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 47831bcb-3b6a-400b-ba62-a6560bb1e95f ['root'::marker:47831bcb-3b6a-400b-ba62-a6560bb1e95f] ''Ubuntu One/Peter.ics'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,559 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F fd8b6895-f157-44b4-91f8-cbcb8ccf9222 ['root'::marker:fd8b6895-f157-44b4-91f8-cbcb8ccf9222] ''Ubuntu One/Home.ics'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,560 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 2345 bytes (available: None)
2010-11-22 12:55:34,561 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F fd8b6895-f157-44b4-91f8-cbcb8ccf9222 ['root'::marker:fd8b6895-f157-44b4-91f8-cbcb8ccf9222] ''Ubuntu One/Home.ics'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,561 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F 85ad051f-fd83-4043-b3e9-ddbeb887647a ['root'::marker:85ad051f-fd83-4043-b3e9-ddbeb887647a] ''Ubuntu One/Macug.ics'' | Calling put_file (got HQ_HASH_NEW:{'hash_eq_local_hash': 'F', 'hash_eq_server_hash': 'F'})
2010-11-22 12:55:34,562 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 1954 bytes (available: None)
2010-11-22 12:55:34,563 - ubuntuone.SyncDaemon.sync - INFO - T:LOCAL:F 85ad051f-fd83-4043-b3e9-ddbeb887647a ['root'::marker:85ad051f-fd83-4043-b3e9-ddbeb887647a] ''Ubuntu One/Macug.ics'' | Called put_file (In: T:NONE:F)
2010-11-22 12:55:34,564 - ubuntuone.SyncDaemon.local_rescan - INFO - processing trash
2010-11-22 12:55:34,579 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2010-11-22 12:55:34,580 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2010-11-22 12:57:34,314 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues WORKING_ON_BOTH  connection 'Not User With Network')>; queues: metadata: 11; content: 10; hash: 0, fsm-cache: hit=1086 miss=23) ----
2010-11-22 12:59:34,314 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues WORKING_ON_BOTH  connection 'Not User With Network')>; queues: metadata: 11; content: 10; hash: 0, fsm-cache: hit=1087 miss=23) ----
2010-11-22 13:01:34,314 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues WORKING_ON_BOTH  connection 'Not User With Network')>; queues: metadata: 11; content: 10; hash: 0, fsm-cache: hit=1087 miss=23) ----
2010-11-22 13:03:34,314 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues WORKING_ON_BOTH  connection 'Not User With Network')>; queues: metadata: 11; content: 10; hash: 0, fsm-cache: hit=1087 miss=23) ----
2010-11-22 13:05:34,314 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'READY'  (queues WORKING_ON_BOTH  connection 'Not User With Network')>; queues: metadata: 11; content: 10; hash: 0, fsm-cache: hit=1087 miss=23) ----
```

---

