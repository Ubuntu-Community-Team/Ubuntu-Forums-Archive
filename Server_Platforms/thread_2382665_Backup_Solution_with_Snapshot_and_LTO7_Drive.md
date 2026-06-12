---
title: "Backup Solution with Snapshot and LTO7 Drive"
date: 2018-01-16
forum: Server Platforms
---

### Post by faun2 on 2018-01-16
Hello,

I have an Ubuntu Server configuration with a working LTO7 Drive for Backup. I am currently using a Windows Server with Veritas Backup Exec which writes a Snapshot from the Data to a fast Disk Array and then write the Snapshot sequential to the LTO7 Drive. I can directly restore Files from the Snapshot on Tape without copy the whole container on the Tape back to disk.

So I would like to know if there is a good solution for Linux that can handle a huge container file and extract files from the container on the LTO Drive but without copy the whole Archive File from LTO Drive back to HDD to just extract an 100 Kbyte File or example.


I use the Snap Shot to Disk method because the Copy process of the Files  direct on Tape are quiet inefficient becuase I copy about 753 Mio small  Files and 3.4 TByte Data. Datarate about 47-54 MByte/sec. when I safe  the Files to a snap shot on disc and I have only about 20-30 Snapshot  files for example they get about 13 Gbyte/Minute = ~225 MByte/sec write  speed. And tape is written faster!

Thanks for any help or expertise!

---

