---
title: "Strange glitch (maybe) in ubuntu one and 11.10"
date: 2011-10-16
forum: Ubuntu One (CLOSED)
---

### Post by Ken147 on 2011-10-16
so for the past 7 hrs it be "downloading" the same 4 files, and a notification pops up every 2 min say it STILL downloading them. the total size of the 4 files are less then 1 megabyte.

anyone have this problem?

---

### Post by duanedesign on 2011-10-16
Hi,
The servers are under a lot of load lately. i noticed a behavior similar to this yesterday. the engineers are working on handling this increase in load. In the meantime you can look in your ~/.cache/ubuntuone/log/syncdaemon.log
NOTE: I like to run this command, then click connect to monitor the log in realtime:
tail -fn 50 ~/.cache/ubuntuone/log/syncdaemon.log

You will see something like this:
```
2011-10-16 14:19:11,884 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' failed with the error: [('SSL routines', 'SSL23_READ', 'ssl handshake failure')]
2011-10-16 14:19:11,886 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: [('SSL routines', 'SSL23_READ', 'ssl handshake failure')]
2011-10-16 14:20:15,538 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'WAITING'  (queues IDLE  connection 'With User With Network')>; queue: 0; hash: 0) ----
2011-10-16 14:21:11,904 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-2.ubuntuone.com, port 443.
2011-10-16 14:21:12,058 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2011-10-16 14:21:12,058 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-10-16 14:21:33,202 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL23_READ', 'ssl handshake failure')]

```

The disconnects and reconnects are why the notifications keep popping up. Unfortunately their is nothing the user can do about this. If you do not see this in your logs then it may be something client side and we should debug further.

---

### Post by pete04 on 2011-10-17
This was happening to me yesterday. I hope it's just spotty server strain.

Just signed up for U1 last week and have found the android app to work flawlessly, but syncing my photos to my desktop has been really hit or miss. The first time I set up the photo sync, the download took forever. Yesterday, it synced 16 photos to my desktop in 5 minutes. Tried to sync 5 photos three hours later and it never worked (got those frequent disconnect issues).

Really want to use U1 for the photo feature. That download speed just needs to improve.

---

