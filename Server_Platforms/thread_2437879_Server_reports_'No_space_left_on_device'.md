---
title: "Server reports 'No space left on device'"
date: 2020-03-02
forum: Server Platforms
---

### Post by MickSulley on 2020-03-02
My server runs Ubuntu server 19.10
My desktop runs Mint 19.2
Just tried to sync desktop and server using Unison and it fails with 
Server: Error in saving archive:
No space left on device

Server has a 2Tb disk, if I log on to it it says /home is using 94.9% of 1.79TB, so it is getting a bit full but there is plenty of space for the sync I am trying.

Oddly if I open Disk Usage Analyser on my desktop and look at the server it says that the /proc directory is 143.3TB but it also says 'Could not detect occupied disk sizes' 
If I run 
df -haT
it says that /proc size is zero.

I have just run a smartctl test and it says PASSED

I am pretty sure that there is space to do the sync but the reporting says that there isn't.  Any ideas how I can fix this?

---

### Post by TheFu on 2020-03-02
/proc is a pseudo file system.  It isn't real.  
Post the output  for both systems using this:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```


For example:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   22G  7.1G   14G  34% /
/dev/sdb1                         ext2  720M  239M  445M  35% /boot
/dev/mapper/hadar--vg-libvirt--lv ext4  197G  2.8G  184G   2% /var/lib/libvirt
/dev/mapper/vg--hadar-lv--backups ext4  459G  397G   40G  91% /Backups

```

Please use "code tags", as I've shown.

Facts. Not descriptions, please.

---

### Post by MickSulley on 2020-03-02
By 'both systems' did you mean desktop and server?
Server
```
mick@zen:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb2      ext4  110G  8.7G   96G   9% /
/dev/sdc1      ext4  1.8T  1.7T     0 100% /home
/dev/sda1      ext4  1.8T  650G  1.1T  38% /common
mick@zen:~$ 
```

Desktop
```

mick@Mint19Desk ~ $ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda6      ext4  183G   35G  139G  20% /
/dev/sdb1      ext4  3.6T  2.1T  1.4T  61% /home
/dev/sda1      ext4   21G   15G  5.0G  75% /media/mick/f9e01850-85c5-4a93-aab6-1cd7d92891f0
mick@Mint19Desk ~ $ 
```

---

### Post by TheFu on 2020-03-02
```
/dev/sdc1      ext4  1.8T  1.7T     0 **_100%_** /home
```

Seems full to me.

BTW, having / over 25G is usually a waste.  
```
/dev/sdb2      ext4  110G  8.7G   96G   9% /
```
same for
```
/dev/sda6      ext4  183G   35G  139G  20% /
```
Much too large, IMHO.  What's going on that 35G is being wasted for the OS?

---

