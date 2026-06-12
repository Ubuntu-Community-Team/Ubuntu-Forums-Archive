---
title: "file copy error from system to cifs mount"
date: 2012-05-01
forum: Server Platforms
---

### Post by dwpriest on 2012-05-01
When coping a file greater than 64kB from an Ubuntu server to a CIFS mounted windows share, most of the data is copied, but it seems the last chunk doesn't get copied. The size doesn't match, and the md5 check sums don't match. I have plenty of file space, but then I use cp, I get the following...

```
cp: closing `cloudBackup/asdf.txt': No space left on device
```

Using rsync, I get the following...

```

rsync: close failed on "/home/fluffy/cloudBackup/.asdf.txt.qrBWe6": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(752) [receiver=3.0.8]
rsync: connection unexpectedly closed (29 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]
```

I have full read/write permissions on the mounted share. I can copy locally and between the mount and system via SSH just fine. Any ideas? Thank you

---

### Post by papibe on 2012-05-01
Hi dwpriest. Welcome to the forums!

May be another partition is full, like /tmp for example. Could you post the result of this command?
```
df -h
```
Regards.

---

### Post by dwpriest on 2012-05-01
75G free.  Here is the print out...

```
fluffy@ptl-cloud:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              1.8T  128G  1.6T   8% /
udev                  995M  8.0K  995M   1% /dev
tmpfs                 402M  700K  401M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1003M     0 1003M   0% /run/shm
//filestore/cloudBackup
                      7.3T  7.2T   75G  99% /home/fluffy/cloudBackup

```

It should be known that it doesn't matter if I copy over 65kB or 1GB, it copies fine until the last chunk.

---

