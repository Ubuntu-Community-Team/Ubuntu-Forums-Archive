---
title: "marathon  /native/libsigar-amd64-linux.so not found."
date: 2017-12-18
forum: Server Platforms
---

### Post by maurice-info on 2017-12-18
After a upgrade of ubuntu server 1604 marathon is update from to   1.4.9-1.0.668.ubuntu1604, 1.5.4. 
When starting marathon the next message appears in the log:

Dec 18 15:59:41 gryw02t marathon[6852]: [2017-12-18 15:59:41,491] ERROR Failed to auto start the [kamon-system-metrics] module. (kamon.ModuleLoaderExtenDec 18 15:59:41 gryw02t marathon[6852]: java.io.FileNotFoundException: /native/libsigar-amd64-linux.so (No such file or directory)

/native/libsigar-amd64-linux.so exists in io.kamon.sigar-loader-1.6.5-rev002.jar and this jar is  in the   app_clashpath 

Does anybody have an idea what could be wrong here ?

Regards, 

Maurice Mahieu

---

### Post by howefield on 2017-12-18
Thread moved to the "*Server Platforms*" forum.

---

