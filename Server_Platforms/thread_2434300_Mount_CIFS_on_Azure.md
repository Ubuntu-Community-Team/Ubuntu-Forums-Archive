---
title: "Mount CIFS on Azure"
date: 2020-01-03
forum: Server Platforms
---

### Post by kinto2 on 2020-01-03
Hello,
I'm trying to test a share mounted on a Ubuntu Linux VM (Azure Cloud).


The mounted share works well with this options:


```
rw,relatime,vers=3.0,cache=strict,username=XXXXXX,uid=0,noforceuid,gid=0,noforcegid,addr=YYYYYYY,file_mode=0777,dir_mode=0777,soft,persistenthandles,nounix,serverino,mapposix,rsize=1048576,wsize=1048576,bsize=1048576,echo_interval=60,actimeo=1
```


The problem I have encountered is when I try to use a script to copy files from an external FTP server on this share.


All the copied files report the local timestamp (at the moment fo FTP script starts) and not the FTP server timestamp.


If It works with the remote timestamp if I set the local disk as destination.


Can you help me to understand how to obtain the original timestamp? Maybe some modification on the cifs mount option?

Thank you.

---

### Post by kinto2 on 2020-01-08
No suggestions?

Thank you.

---

### Post by slickymaster on 2020-01-09
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2020-01-09
How are you copying files to the mounted location?  There might be optional flags that can be specified to ensure that the timestamp is preserved.

---

