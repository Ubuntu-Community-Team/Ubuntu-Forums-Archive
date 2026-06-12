---
title: "Error Connecting to Test DB in MongoDB in Ubuntu"
date: 2017-02-28
forum: Ubuntu Application Development
---

### Post by lruihao on 2017-02-28
I am trying to connect to "test" db in MongoDB in Ubuntu. But I am receiving this error:

root@RUIHAO-DELL:/mnt/c/mongo/bin# mongo
MongoDB shell version: 2.4.9
connecting to: test
Wed Mar  1 03:51:03.958 ERROR: can't get TCP_KEEPIDLE: errno:22 Invalid argument
Wed Mar  1 03:51:03.958 ERROR: can't get TCP_KEEPINTVL: errno:22 Invalid argument
> show dbs
local   0.078125GB
>

I am also receiving some errors while establishing listening ports for MongoDB:

root@RUIHAO-DELL:~# mongod --dbpath /mnt/c/data/db
Wed Mar  1 03:48:06.499 [initandlisten] MongoDB starting : pid=3481 port=27017 dbpath=/mnt/c/data/db 64-bit host=RUIHAO-DELL
Wed Mar  1 03:48:06.500 [initandlisten] db version v2.4.9
Wed Mar  1 03:48:06.500 [initandlisten] git version: nogitversion
Wed Mar  1 03:48:06.500 [initandlisten] build info: Linux orlo 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 BOOST_LIB_VERSION=1_54
Wed Mar  1 03:48:06.500 [initandlisten] allocator: tcmalloc
Wed Mar  1 03:48:06.500 [initandlisten] options: { dbpath: "/mnt/c/data/db" }
Wed Mar  1 03:48:06.510 [initandlisten] journal dir=/mnt/c/data/db/journal
Wed Mar  1 03:48:06.511 [initandlisten] recover : no journal files present, no recovery needed
Wed Mar  1 03:48:06.795 [initandlisten] mincore failed: errno:38 Function not implemented
Wed Mar  1 03:48:06.800 [initandlisten] mincore failed: errno:38 Function not implemented 
Wed Mar  1 03:48:06.801 [initandlisten] mincore failed: errno:38 Function not implemented
Wed Mar  1 03:48:06.801 [websvr] admin web console waiting for connections on port 28017
Wed Mar  1 03:48:06.802 [initandlisten] waiting for connections on port 27017

Please assist. Thank you

P.S. This is the [tutorial ]("https://www.youtube.com/watch?v=oVIeMfvgTz8")that I am following.

---

