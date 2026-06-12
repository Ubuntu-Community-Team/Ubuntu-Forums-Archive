---
title: "Modify mongodb dbpath to use USB Storage"
date: 2016-08-19
forum: Server Platforms
---

### Post by bharris on 2016-08-19
I have a Meekat Ubuntu 16.01 server that I have running a lot of things.  I am short on disk space on the root filesystem and would like to move the mongodb to an attached USB drive.  I have plenty of other services using it without an issue. I have tried everything that i can find but get a permission denied error message.  I let it start once to copy the data to the new location, note lock file.

Changed dbpath=/var/lib/mongodb in /etc/mongodb.conf to reflect new locations and keep getting a permissions denied.  Even tried a symlink.  User and group memberships look fine.

Error in mongodb.log:mongo2016-08-19T15:32:45.997-0400 [initandlisten] exception in initAndListen std::exception: boost::filesystem::status: Permission denied: "/var/lib/mongodb", terminating

Symlink in /var/lib/: lrwxrwxrwx 1 mongodb nogroup 37 Aug 19 15:29 mongodb -> /media/bharrisii/Hodor 6TB HD/mongodb

Files:
bharrisii@Hodor:/var/lib/mongodb$ ls -al
total 163856
drwxrwxr-x 4 mongodb   nogroup     4096 Aug 19 15:26 .
drwxr-xr-x 5 bharrisii root        4096 Aug 19 15:19 ..
-rw------- 1 mongodb   nogroup 67108864 Aug 19 15:16 graylog.0
-rw------- 1 mongodb   nogroup 16777216 Aug 19 15:16 graylog.ns
drwxr-xr-x 2 mongodb   nogroup     4096 Aug 19 15:16 journal
-rw------- 1 mongodb   nogroup 67108864 Aug 19 15:14 local.0
-rw------- 1 mongodb   nogroup 16777216 Aug 19 15:14 local.ns
-rwxr-xr-x 1 mongodb   nogroup        0 Aug 19 15:16 mongod.lock
drwxr-xr-x 2 mongodb   nogroup     4096 Aug 19 15:14 _tmp

The example are the symlink, but I get the same going directly to the USB storage.  Any help would be appreciated!

---

### Post by howefield on 2016-08-19
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by bharris on 2016-08-24
Thank you for moving to the server forum.  Anyone have a suggestion?  Thanks!

---

