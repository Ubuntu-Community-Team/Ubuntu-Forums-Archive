---
title: "Failure dbusexceptions"
date: 2011-03-08
forum: Ubuntu One (CLOSED)
---

### Post by dacoolapen on 2011-03-08
Hi,

I use Meerkat and result of u1sdtool -s is:

Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Extra info:

- Tomboy Notes are syncing fine directly

- Folders are synced in cloud, but files not

- Ubuntu one prerences says Disconnected

Tx

---

### Post by dacoolapen on 2011-03-09
UPDATE: I now have this on u1sdtool -s

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH

Ubuntu One preferences says: Synchronization in process

But on my folders it says: "This folder cannot be synchronized because it contains one ore more folders that are already synchronized."

---

### Post by duanedesign on 2011-03-14
Are yo still having issues with Ubuntu One?

What do yo get from this command, it lists the folders you are syncing with Ubuntu One:

```
u1sdtool --list-folders
```


thank you,
duanedesign

---

### Post by dacoolapen on 2011-03-23
hi duanedesign,

tnx for your follow-up; yes I still have the same issue, so not working for me.

according to a colleague the problem is that u1 is choking on some filenaming. it basically is not completing the update of the meta-data, let alone it then starts uploading the actual data.

running your proposed command currently gives me:

Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.TimedOut: Activation of com.ubuntuone.SyncDaemon timed out

---

