---
title: "Disk Space Lost  (Cannot be Found)"
date: 2012-04-07
forum: Server Platforms
---

### Post by leonv12 on 2012-04-07
I recently had to rebuild a server because the old hardware crashed.  I am running Ubuntu Server 10.04.4 LTS.  My sda drive is 500G.  Command du says about 97Gig is used (which is about right)
```
root@bdp111:/# du -sm *
7       bin
30      boot
1       cdrom
1       dev
3       e1000e
5       etc
1       home
0       initrd.img
0       initrd.img.old
224     lib
1       lost+found
1       media
1       mnt
1       opt
du: cannot access `proc/1372/task/1372/fd/3': No such file or directory
du: cannot access `proc/1372/task/1372/fdinfo/3': No such file or directory
du: cannot access `proc/1372/fd/3': No such file or directory
du: cannot access `proc/1372/fdinfo/3': No such file or directory
0       proc
1       root
7       sbin
1       selinux
1       srv
0       sys
1       tmp
555     usr
95956   var
0       vmlinuz
0       vmlinuz.old
root@bdp111:/#
```

BUT df says 237Gig is used.

```
root@bdp111:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            478037952 237481852 216273120  53% /
none                    443132       216    442916   1% /dev
none                    447356         0    447356   0% /dev/shm
none                    447356        48    447308   1% /var/run
none                    447356         0    447356   0% /var/lock
none                    447356         0    447356   0% /lib/init/rw
/dev/sdb1            961433632    204436 912391120   1% /var/weekly
root@bdp111:/#
```

I have rebooted, created forcefsck in / and rebooted, but the disk usage doesn't change.

Where can this disk space be hiding?

---

