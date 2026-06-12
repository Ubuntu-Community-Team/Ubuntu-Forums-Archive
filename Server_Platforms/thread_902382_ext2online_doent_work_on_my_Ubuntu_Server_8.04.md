---
title: "ext2online doent work on my Ubuntu Server 8.04"
date: 2008-08-27
forum: Server Platforms
---

### Post by thejinx on 2008-08-27
Hello, 
 I am trying to reduce my LV, but ext2online doesnt support it. 
 I have ext2online from the ubuntu repo and doesnt do it. 

Here is a sample:

[root@visualserver:~]# ext2online -f /dev/rootvg/tmp_lv 
ext2online v1.1.19 - 2001/03/18 for EXT2FS 0.5b
ext2online: warning - device size 262144, filesystem 524288
error: Invalid argument: seeking to 536869888

this was to reduce the filesystem /tmp from 512mb to 256mb and it doesnt work.

This worked on CentOS 4 and CentOS 5, but it seems on Ubuntu it doesnt. Can anyone help?

---

