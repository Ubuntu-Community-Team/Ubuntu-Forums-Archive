---
title: "No space left on device"
date: 2022-11-09
forum: Server Platforms
---

### Post by MickSulley on 2022-11-09
Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-52-generic x86_64)

My server is reporting "No space left on device" and I can't do much with it.

In another post I saw something similar and reference to inotify, which I installed yesterday, so I removed it and rebooted but the problem is still there.  I have manually deleted about 200 mB but it makes no difference.
This is what I see -
```
mick@holly:~$ df
Filesystem                         1K-blocks       Used  Available Use% Mounted on
tmpfs                                1632668       1608    1631060   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  114272420  108431820          0 100% /
tmpfs                                8163324          0    8163324   0% /dev/shm
tmpfs                                   5120          0       5120   0% /run/lock
/dev/sda2                             996780     251952     676016  28% /boot
/dev/sdb1                         3844550452 1433205892 2215977300  40% /home
tmpfs                                1632664          4    1632660   1% /run/user/1000
mick@holly:~$ df -i
Filesystem                           Inodes  IUsed     IFree IUse% Mounted on
tmpfs                               2040831    940   2039891    1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   7299072 139050   7160022    2% /
tmpfs                               2040831      1   2040830    1% /dev/shm
tmpfs                               2040831      5   2040826    1% /run/lock
/dev/sda2                             65536    316     65220    1% /boot
/dev/sdb1                         244195328 581364 243613964    1% /home
tmpfs                                408166     25    408141    1% /run/user/1000
mick@holly:~$ 

```

What can I do?

---

### Post by LHammonds on 2022-11-09
Looks like you have everything but /boot and /home in your root partition...which is about 114 GB

The OS is only taking up about 8 GB so the rest is what you put there.

If you don't know where these 100+ GB is residing, the 1st thing you can do is look at the root folders to see where the bulk of the space is being consumed.

```
du -sh /*
```
This will cause some errors since not all the folders in the root are real / accessible but ignore the errors.

If you find that "/srv" is taking up all the space, then drill into that folder to see what is taking up space there...such as:
```
du -sh /srv/*
```

Continue doing this until you find the biggest space hogs.

Granted, the biggest is not always what you purge first but it helps track down what makes the biggest impact quickly.

If you find that /var/log is taking up a large chunk, investigate what service is going haywire and fix the problem.  

LHammonds

---

### Post by MickSulley on 2022-11-09
It is a 4TB drive and I think it is no more than half full
This is what I see
```
mick@holly:~$ sudo du -sh /*
0	/bin
247M	/boot
4.0K	/cdrom
33M	/common
11M	/core
0	/dev
7.5M	/etc
^C
mick@holly:~$ sudo du -sh /srv/*
du: cannot access '/srv/*': No such file or directory
mick@holly:~$ 

```
/srv is empty.  I can't see anything that is full.

---

### Post by LHammonds on 2022-11-10
```
/dev/mapper/ubuntu--vg-ubuntu--lv  114272420  108431820          0 100% /
```
Just so you are clear, THIS above is what's filled up.  It shows 100% in use and it is 114 GB in size.

Your 4TB is in /home and is only 40% in use but that is not the concern here (other than having allocated too much space to that location and not enough to the root partition but since we do not know "why" root is full yet, that cannot be determined).

```
sudo du -sh /* 0	/bin
247M	/boot
4.0K	/cdrom
33M	/common
11M	/core
0	/dev
7.5M	/etc
**^C**
```
This is NOT all of the folders in the root and looks like you pressed CTRL+C before it could finish.  These folders that we can see are taking up very little space.  You have not found the problem area yet.  But no matter what, ignore "/boot" and "/home" because it is not part of the root partition that is full.

The "/srv" was just an example since I have no idea what location is filling up the partition.  You need to look at the results of the "du" command and see what folders are taking up the most space and drill into those folders based on what you see.  But that "du" command should show you 1.5 to 2 pages of folders at least.

LHammonds

---

### Post by MickSulley on 2022-11-10
Found it!!!

/var/log/minidlna.log was 96 gb.  Stopped minidlna, deleted the log and now it looks OK.

Now I just need to sort out what is wrong with minidlna &#128516;

Thanks for your help

---

### Post by TheFu on 2022-11-10
> **MickSulley said:**
> Found it!!!

/var/log/minidlna.log was 96 gb.  Stopped minidlna, deleted the log and now it looks OK.

Now I just need to sort out what is wrong with minidlna &#128516;

Thanks for your help

I'd ensure logrotate for minidlna was configured and limit the log file size to 10M each.  I'd think minidlna would come with a logrotate config, so perhaps that file is corrupted or was removed?    Perhaps rotating the log daily or weekly would be smart too?  IDK. Up to you.

For lurkers, here's a command to search a system for huge files:
```
sudo find /  -type f -size +3G -exec ls -lh {} \; 
```
Just change the size lower and lower with each run until there are too many files that you need to keep.
To look for big files (logs) in /var/, something like this is useful:
```
sudo find /var  -type f -size +500M -exec ls -lh {} \; 
```
Any log file over 10M is really large, pointing at some other issue.

With systemd, we got a really great log system, journalctl.
```
sudo journalctl --vacuum-size=50M
```
will reduce all systemd managed logs to 50M or less.  Making some changes to /etc/systemd/journald.conf can prevent run-away logging:
```
[Journal]
Storage=persistent
SystemMaxFileSize=50M
SystemMaxFiles=10
```
Of course, if minidlna isn't using systemd for logging, those settings won't help.  Best to use persistent logging on SSD and HDD-based systems, but never on something running from flash microSD/SDHC/USB storage, except for emergency troubleshooting.  Logging to flash storage all the time will wear out that storage much too fast.

---

### Post by MickSulley on 2022-11-12
Thanks for the suggestion.  I already had a script which checked temperature, swap space, home dir space, etc, but it didn't check /var space.  I will add that now.
Cheers
Mick

---

### Post by TheFu on 2022-11-12
> **MickSulley said:**
> Thanks for the suggestion.  I already had a script which checked temperature, swap space, home dir space, etc, but it didn't check /var space.  I will add that now.
Cheers
Mick

Might want to check out 'logwatch'.  This is how to get daily reports about system stuff that needs attention. It was created and updated over decades by expert admins.

---

### Post by ajgreeny on 2022-11-12
Also perhaps worth showing us the content of your /etc/minidlna.conf file.  The lines relating to logs in mine are
```
# Path to the directory that should hold the log file.
#log_dir=/var/log
#
# Type and minimum level of importance of messages to be logged.
#
# The types are "artwork", "database", "general", "http", "inotify",
# "metadata", "scanner", "ssdp" and "tivo".
#
# The levels are "off", "fatal", "error", "warn", "info" or "debug".
# "off" turns of logging entirely, "fatal" is the highest level of importance
# and "debug" the lowest.
log_level=fatal
#
# The types are comma-separated, followed by an equal sign ("="), followed by a
# level that applies to the preceding types. This can be repeated, separating
# each of these constructs with a comma.
#
# The default is to log all types of messages at the "warn" level.
#log_level=general,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=warn

```
My minidlna.log file is very tiny, only 702bytes as I have had no problems with it since installing it though I accept that my log level is ***fatal***, not the default ***warn*** though If I have had problems in the past I lower the level to show more; not had to do that either since installing as it just seems to work for me without problems.

---

