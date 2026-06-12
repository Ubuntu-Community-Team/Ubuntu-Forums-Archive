---
title: "SMB/NFS shares with MyISAM tables"
date: 2010-06-29
forum: Server Platforms
---

### Post by Richard1979 on 2010-06-29
This is a bit of a different one.
Basically, I'm creating an NFS or Samba share on a server and mounting it on another server at boot.
Both are using Ubuntu 10 LTS Server x64 with the standard MySQL/NFS/Samba from the repos.

What I'm doing is symlinking from the MySQL data directory to the share.
"ls -l /var/lib/mysql/test/" would look something like:

```
test.MYD -> /data/test/test.MYD
test.MYI -> /data/test/test.MYI
                  test.frm
```/data is the mounted share.

So, I leave the table form there, but the data and indexes are actually on the share.
I've done this before using TempFS and it works well - it's nice for read only tables.

Now, the problem I have is that no matter how I mount the share, or how I set the permissions, MySQL sees the table as Read Only and won't even do a SELECT * FROM test;
I've tried changing everything to 0777, run "flush table test", restarted Samba/MySQL and anything else I can think of, and can even do "touch test.txt" on the client server that has mounted the share.

Bizarre.
Any ideas?

---

