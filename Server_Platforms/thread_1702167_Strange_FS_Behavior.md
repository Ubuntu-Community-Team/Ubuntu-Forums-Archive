---
title: "Strange FS Behavior"
date: 2011-03-07
forum: Server Platforms
---

### Post by esthermofet on 2011-03-07
We have an app that, for reasons known only to its original developers, has been writing huge debug logs to /tmp. There was only one primary log file called /tmp/service-prod.log. That file was consuming most of the space on the device. So, we use logrotate to rotate, compress, etc. Under normal conditions, this works flawlessly and space is freed automatically.

In some cases, though, where, say, the admin forgets to set up logrotate (yeah, this guy) logs or other debug information quickly turn into very large files. When we try to delete the logs (or just echo /dev/null to them) it looks like ext4 somehow loses its mind and refuses to release space that the files consumed.

For example, here's one file in particular:
```
root@service08c:~# du -ah /tmp
7.1G	/tmp/service-prod.log
```

That could be a problem. So, we look at the partition it's on to see how much space is left:

```
root@service08c:~# df -hT /tmp
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/service08c-tmp
              ext4    7.4G  6.8G  211M  98% /tmp
```

We echo /dev/null to the offending enormous file:

```
root@service08c:~# echo /dev/null > /tmp/service-prod.log
```

And all should be right with the world. We hope:

```
root@service08c:~# df -hT /tmp
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/service08c-tmp
              ext4    7.4G  6.8G  211M  98% /tmp
```

Well, that didn't work.

So, the next thinking is iNodes, but that doesn't seem to be the issue:

```
root@service08c:~# df -i /tmp
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/service08c-tmp
                      488640      19  488621    1% /tmp
```

Yeah, that's not it. Only 19 out of 488640 used.

What if we enumerate files in /tmp to find out which ones are the space hogs?

```
root@service08c:~# du -ah /tmp
2.5M	/tmp/service-prod.log
32K	/tmp/hsperfdata_root/7846
36K	/tmp/hsperfdata_root
4.0K	/tmp/krb5cc_1685591619
0	/tmp/lwidentity.join.log
16K	/tmp/lost+found
4.0K	/tmp/krb5cc_1685591769
2.6M	/tmp
```

Well, that's peculiar! Clearly, it shows that our service-prod.log file is much smaller than it was to begin with, so the service is still writing data to it.

The first utility, **df**, says it's a 7.4GB partition with only 211M available, which would mean that there's 7.2GB in use. Yet, **du** clearly shows that there's only 2.6M in use.

That's odd, for sure, but what happens if we try the academic exercise of just trying to consume that last 211MB of space?

```
root@service08c:~# dd if=/dev/zero of=/tmp/test bs=4096 count=1024000
```

That would try to create a 1024000x4096 byte file -- about 4GB, plenty enough to consume whatever space is remaining. Naturally, the predictable happens:

```
dd: writing `/tmp/test': No space left on device
136502+0 records in
136501+0 records out
559108096 bytes (559 MB) copied, 3.41439 s, 164 MB/s
```

But what's up with that amount copied? I thought it said there was only 211MB left. So how could it copy 559MB?

```
root@service08c:~# ls -alh /tmp/test
-rw-r--r-- 1 root root 534M 2011-03-07 10:26 /tmp/test
```

At any rate, the question is: _What happened to the 7+GB of space once those large files were deleted?_

We do see that a reboot will fix it, but that's not an option on these systems due to our customer's uptime requirements.

Thoughts?

---

### Post by dtfinch on 2011-03-07
If the file is still open (like if the app that wrote the log is still running and writing to it), then deleting it won't free the space until the app closes the file.

If you've already restarted the app after deleting the log file, and the space isn't freed, lsof could tell you if something else has the file open.

---

### Post by esthermofet on 2011-03-11
That would make sense. I thought the service was restarted but may have completely overlooked it. We'll try that.

---

