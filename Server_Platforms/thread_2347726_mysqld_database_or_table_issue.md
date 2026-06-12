---
title: "mysqld database or table issue"
date: 2016-12-28
forum: Server Platforms
---

### Post by kheesoon-soh on 2016-12-28
Hello

Do you know what are the issue on the mysqld database or table below as I am new to this.

```
161228  9:23:17  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
161228  9:23:18  InnoDB: Waiting for the background threads to start
161228  9:23:19 InnoDB: 1.1.8 started; log sequence number 2689644
161228  9:23:19 [Note] Event Scheduler: Loaded 0 events
161228  9:23:19 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.22-0ubuntu1'  socket: '/var/run/mysqld/mysqld.sock' port:
3306  (Ubuntu)
161228  9:23:29 [ERROR] /usr/sbin/mysqld: Table './testing/user' is marked as crashed and should be repaired
161228  9:23:29 [ERROR] /usr/sbin/mysqld: Table './testing/user' is marked as crashed and should be repaired
161228  9:23:29 [ERROR] /usr/sbin/mysqld: Table './testing/user' is marked as crashed and should be repaired
161228  9:23:29 [Warning] Checking table:   './testing/user'
161228  9:23:30 [ERROR] /usr/sbin/mysqld: Table './testingsession/session' is marked as crashed and should be repaired
161228  9:23:30 [ERROR] /usr/sbin/mysqld: Table './testingsession/session' is marked as crashed and should be repaired
161228  9:23:30 [ERROR] /usr/sbin/mysqld: Table './testingsession/session' is marked as crashed and should be repaired
161228  9:23:30 [Warning] Checking table: './testingsession/session'
161228  9:23:30 [ERROR] /usr/sbin/mysqld: Table './testingsession/connection_history' is marked as crashed and should be repaired
161228  9:23:30 [Warning] Checking table:
'./testingsession/connection_history'
161228  9:23:30 [ERROR] /usr/sbin/mysqld: Table './testing/1023_Contact' is marked as crashed and should be repaired
161228  9:23:30 [Warning] Checking table: './testing/1023_Contact'
161228  9:23:30 [ERROR] Got an error from unknown thread,
/build/buildd/mysql-5.5-5.5.22/storage/myisam/ha_myisam.cc:870
161228  9:23:30 [Warning] Recovering table: './testing/1023_Contact'
161228  9:23:31 [ERROR] Got an error from unknown thread,
/build/buildd/mysql-5.5-5.5.22/storage/myisam/ha_myisam.cc:870
161228  9:23:31 [Warning] Recovering table:
'./testingsession/connection_history'
161228  9:23:31 [Note] Found 306349 of 306348 rows when repairing './testingsession/connection_history'
161228  9:23:31 [ERROR] /usr/sbin/mysqld: Table './testing/1023_Inbound' is marked as crashed and should be repaired
161228  9:23:31 [Warning] Checking table: './testing/1023_Inbound'
161228  9:23:31 [ERROR] /usr/sbin/mysqld: Table './testing/1031_Contact' is marked as crashed and should be repaired
161228  9:23:31 [Warning] Checking table: './testing/1031_Contact'
161228  9:23:32 [ERROR] /usr/sbin/mysqld: Table './testing/1031_Inbound' is marked as crashed and should be repaired
161228  9:23:32 [Warning] Checking table: './testing/1031_Inbound'
161228  9:23:32 [ERROR] /usr/sbin/mysqld: Table './testing/1036_company' is marked as crashed and should be repaired
161228  9:23:32 [Warning] Checking table: './testing/1036_company'
161228  9:23:32 [ERROR] /usr/sbin/mysqld: Table './testing/1036_contact' is marked as crashed and should be repaired
161228  9:23:32 [Warning] Checking table: './testing/1036_contact'
161228  9:23:32 [ERROR] /usr/sbin/mysqld: Table './testing/801_Contact' is marked as crashed and should be repaired
161228  9:23:32 [Warning] Checking table: './testing/801_Contact'
161228  9:23:32 [ERROR] /usr/sbin/mysqld: Table './testing/801_Interaction' is marked as crashed and should be repaired
161228  9:23:32 [Warning] Checking table: './testing/801_Interaction'
161228  9:23:33 [ERROR] /usr/sbin/mysqld: Table './testing/933_Contact' is marked as crashed and should be repaired
161228  9:23:33 [Warning] Checking table: './testing/933_Contact'
161228  9:23:33 [ERROR] /usr/sbin/mysqld: Table './testing/933_Inbound_201608' is marked as crashed and should be repaired
161228  9:23:33 [Warning] Checking table: './testing/933_Inbound_201608'
161228  9:23:33 [ERROR] /usr/sbin/mysqld: Table './testing/campaign_activity_1163' is marked as crashed and should be repaired
161228  9:23:33 [Warning] Checking table:
'./testing/campaign_activity_1163'
161228  9:23:33 [ERROR] /usr/sbin/mysqld: Table './testing/campaign_activity_1291' is marked as crashed and should be repaired
161228  9:23:33 [Warning] Checking table:
'./testing/campaign_activity_1291'
161228  9:23:34 [ERROR] /usr/sbin/mysqld: Table './testing/campaign_activity_1403' is marked as crashed and should be repaired
161228  9:23:34 [Warning] Checking table:
'./testing/campaign_activity_1403'
161228  9:23:35 [ERROR] /usr/sbin/mysqld: Table './testing/campaign_activity_1408' is marked as crashed and should be repaired
161228  9:23:35 [Warning] Checking table:
'./testing/campaign_activity_1408'
161228  9:23:37 [ERROR] /usr/sbin/mysqld: Table './testing/database_history' is marked as crashed and should be repaired
161228  9:23:37 [Warning] Checking table: './testing/database_history'
161228  9:23:39 [ERROR] /usr/sbin/mysqld: Table './testing/database_update_file' is marked as crashed and should be repaired
161228  9:23:39 [Warning] Checking table: './testing/database_update_file'
161228  9:23:40 [ERROR] /usr/sbin/mysqld: Table './testing/history_activity_1163' is marked as crashed and should be repaired
161228  9:23:40 [Warning] Checking table:
'./testing/history_activity_1163'
161228  9:23:41 [ERROR] /usr/sbin/mysqld: Table './testing/history_activity_1291' is marked as crashed and should be repaired
161228  9:23:41 [Warning] Checking table:
'./testing/history_activity_1291'
161228  9:23:43 [ERROR] /usr/sbin/mysqld: Table './testing/history_activity_1403' is marked as crashed and should be repaired
161228  9:23:43 [Warning] Checking table:
'./testing/history_activity_1403'
161228  9:23:43 [ERROR] /usr/sbin/mysqld: Table './testing/history_activity_1408' is marked as crashed and should be repaired
161228  9:23:43 [Warning] Checking table:
'./testing/history_activity_1408'
161228  9:23:45 [ERROR] /usr/sbin/mysqld: Table './testing/telemarketing_campaign_history' is marked as crashed and should be repaired
161228  9:23:45 [Warning] Checking table:
'./testing/telemarketing_campaign_history'
161228  9:25:03 [ERROR] /usr/sbin/mysqld: Table './testing/template_history' is marked as crashed and should be repaired
161228  9:25:03 [Warning] Checking table: './testing/template_history'
161228  9:25:03 [ERROR] Got an error from unknown thread,
/build/buildd/mysql-5.5-5.5.22/storage/myisam/ha_myisam.cc:870
161228  9:25:03 [Warning] Recovering table: './testing/template_history'
161228  9:25:04 [Note] Found 211218 of 211217 rows when repairing './testing/template_history'
```

---

### Post by darkod on 2016-12-28
Have you tried to google the error? This looks like it can get you started:
[https://dev.mysql.com/doc/refman/5.7/en/myisam-repair.html](https://dev.mysql.com/doc/refman/5.7/en/myisam-repair.html)

It looks like the server or mysql crashed before the database could shut down correctly. Or something like that...

---

