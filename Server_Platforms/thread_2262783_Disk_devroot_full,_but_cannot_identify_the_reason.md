---
title: "Disk /dev/root full, but cannot identify the reason"
date: 2015-01-27
forum: Server Platforms
---

### Post by franck2 on 2015-01-27
Hello,
I need some help to fix some disk space issue.
Actually I'm using a private vps cloud server with 50Gb of disk space.

When I run `df -h`, I get :

    ```
Filesystem      Size  Used Avail Use% Mounted on
    /dev/root        48G   45G  570M  99% /
    devtmpfs        2.0G  4.0K  2.0G   1% /dev
    none            4.0K     0  4.0K   0% /sys/fs/cgroup
    none            395M  524K  395M   1% /run
    none            5.0M     0  5.0M   0% /run/lock
    none            2.0G     0  2.0G   0% /run/shm
    none            100M     0  100M   0% /run/user
```

`df -i` returns :

    ```
Filesystem      Inodes IUsed   IFree IUse% Mounted on
    /dev/root      3141600 78065 3063535    3% /
    devtmpfs        505084  1438  503646    1% /dev
    none            505206     2  505204    1% /sys/fs/cgroup
    none            505206   891  504315    1% /run
    none            505206     2  505204    1% /run/lock
    none            505206     1  505205    1% /run/shm
    none            505206     2  505204    1% /run/user
```

But when I run `du -sh / | sort -nr | head`, I get :

    ```
du: cannot access â/sys/kernel/slab/L2TP/IPv6â: No such file or directory
    du: cannot access â/sys/kernel/slab/L2TP/IPâ: No such file or directory
    du: cannot access â/proc/391/task/391/fd/4â: No such file or directory
    du: cannot access â/proc/391/task/391/fdinfo/4â: No such file or directory
    du: cannot access â/proc/391/fd/4â: No such file or directory
    du: cannot access â/proc/391/fdinfo/4â: No such file or directory
    du: cannot access â/proc/402â: No such file or directory
    du: cannot access â/proc/32350â: No such file or directory
    du: cannot access â/proc/32354â: No such file or directory
    du: cannot access â/proc/32356â: No such file or directory
    du: cannot access â/proc/32360â: No such file or directory
    du: cannot access â/proc/32363â: No such file or directory
    du: cannot access â/proc/32368â: No such file or directory
    8.9G    /
```

So I know that both commands don't return the same kind of informations. The first returns the filesystem disk usage, the other, the space used by files.

There is no mounted drive or device, and logs weight is ~167M.

I tried `cat /proc/mounts` which returns :

    ```
rootfs / rootfs rw 0 0
    /dev/root / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
    devtmpfs /dev devtmpfs rw,relatime,size=2020336k,nr_inodes=505084,mode=755 0 0
    sysfs /sys sysfs rw,relatime 0 0
    none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
    none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
    none /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
    none /sys/fs/cgroup tmpfs rw,relatime,size=4k,mode=755 0 0
    none /sys/fs/fuse/connections fusectl rw,relatime 0 0
    none /sys/kernel/security securityfs rw,relatime 0 0
    none /run tmpfs rw,nosuid,noexec,relatime,size=404168k,mode=755 0 0
    none /sys/fs/pstore pstore rw,relatime 0 0
    none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
    none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
    none /run/user tmpfs rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755 0 0
    systemd /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,name=systemd 0 0
```

So I can I identify what is using so much space, as my `du` seems ok ?
I tried `autoclean` and `autoremove` with no chance, every thing is all right.

BTW I also have a cron which runs datas and mysql dump and send it to Dropbox. But the 7 folders (7 days backup) only use 1.7gb of disk space.

Thanks for helping me out.

---

### Post by darkod on 2015-01-27
There is better command for folder size 'du -sh'. I have never run it on root but it should be like:
cd /
du -sh *

The * is important to tell it to scan all in root. When it finds a folder with big size go into it and run the command again. Until you find what it is. Not sure if its best to use -ash to search hidden files too. Not sure if it leaves them out without the 'a'.

---

### Post by franck2 on 2015-01-27
Hello, thanks for answering. I already tried this on /*, but doesn't return anything usefull.

---

### Post by MAFoElffen on 2015-01-27
If I'm looking for large files... Here (run as root). This will give you your top 40 biggest files:
```

find / -type f  -size +10000k -exec ls -lh {} \; | awk '{print $5 ": " $9}' | sort -nr | head -n 40

```
You can play with that to get more or differing results, depending what you are looking for...

If I'm looking for directory usage... I write it to a file that I can review:
```

du -h / | tee ~/Documents/duResults.txt

```

---

### Post by franck2 on 2015-02-02
Hello, I may explain what happened : I was using a script to launch the backup and sync to dropbox of my app files. But because I didn't manage it well, the script was executing too many times at the same time instead of only once. So it was using too much disk space.
That's it.

---

### Post by MAFoElffen on 2015-02-02
Darn. Hate when that happens... (I can admit that...)

---

