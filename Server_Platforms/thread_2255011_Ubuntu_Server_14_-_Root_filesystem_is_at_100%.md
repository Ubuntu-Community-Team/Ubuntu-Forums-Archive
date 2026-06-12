---
title: "Ubuntu Server 14 - Root filesystem is at 100%"
date: 2014-12-01
forum: Server Platforms
---

### Post by Mike_Burt on 2014-12-01
Hi, Im running a server with ubuntu server 14 (headless) with a raid configuration, the OS itself is install on a 64GB flash drive with 2x 2TB hard drives set in RAID1. I'm using for my Samba file shares and it's was working very well until two days ago it shows up as the root filesystem is a 100% used. I don't understand what happen or whats going on as I checked the var and temp folders there are no big files that are showing up. I restarted the system and it still shows up as being 100% full. Also I have Webmin installed in which I viewed the status and more information about the partitions its reports the root filesystem as full also. Please give me some advice and input on this as I checked google for solutions and ran commands and have yet to find a solution for my problem. Thanks

---

### Post by Habitual on 2014-12-01
Hello Mike:

If you can login using a terminal or console , please run this command and show us the output please:
```
sudo df -hi && df -hT
```

If there are "users" on the system ***AND*** /home is mounted off the / partition, this could account for it.
inodes, or the lack of them, could be an issue.

inodes being all used can show that there is disk space, but the system will report itself as "full".

Please let us know...

---

### Post by Mike_Burt on 2014-12-02
[FONT=Menlo]Filesystem     Inodes IUsed IFree IUse% Mounted on[/FONT]
[FONT=Menlo]/dev/sdc1        3.4M  150K  3.3M    5% /[/FONT]
[FONT=Menlo]none             469K     2  469K    1% /sys/fs/cgroup[/FONT]
[FONT=Menlo]udev             466K   519  465K    1% /dev[/FONT]
[FONT=Menlo]tmpfs            469K   499  468K    1% /run[/FONT]
[FONT=Menlo]none             469K     2  469K    1% /run/lock[/FONT]
[FONT=Menlo]none             469K     2  469K    1% /run/shm[/FONT]
[FONT=Menlo]none             469K     2  469K    1% /run/user[/FONT]
[FONT=Menlo]overflow         469K     2  469K    1% /tmp[/FONT]
[FONT=Menlo]/dev/md0         175M   30K  175M    1% /mnt/fortisdisk[/FONT]
[FONT=Menlo]Filesystem     Type      Size  Used Avail Use% Mounted on[/FONT]
[FONT=Menlo]/dev/sdc1      ext4       53G   53G     0 100% /[/FONT]
[FONT=Menlo]none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup[/FONT]
[FONT=Menlo]udev           devtmpfs  1.9G  4.0K  1.9G   1% /dev[/FONT]
[FONT=Menlo]tmpfs          tmpfs     375M  1.2M  374M   1% /run[/FONT]
[FONT=Menlo]none           tmpfs     5.0M     0  5.0M   0% /run/lock[/FONT]
[FONT=Menlo]none           tmpfs     1.9G  4.0K  1.9G   1% /run/shm[/FONT]
[FONT=Menlo]none           tmpfs     100M     0  100M   0% /run/user[/FONT]
[FONT=Menlo]overflow       tmpfs     1.0M     0  1.0M   0% /tmp[/FONT]
[FONT=Menlo]/dev/md0       ext4      2.7T  654G  2.0T  26% /mnt/fortisdisk[/FONT]
[FONT=Menlo]omar@FortisServer:~$ [/FONT]


Here is the output

---

### Post by volkswagner on 2014-12-02
Try to see if you can drill down on where space is consumed du command can be helpful here.

Since /dev/md0 doesn't seem to be part of the problem you can first exclude it for du to run quicker.

```
sudo du -h / --max-depth=1 --exclude=/mnt/fortisdisk
```

Modify the above command if you find a directory consuming space for example if /var has most space used try:

```
sudo du -h /var --max-depth=1 
```

---

### Post by Mike_Burt on 2014-12-09
Here is the output for the commands above:
[FONT=Menlo]omar@FortisServer:~$ sudo du -h / --max-depth=1 --exclude=/mnt/fortisdisk[/FONT][FONT=Menlo][sudo] password for omar: [/FONT]
[FONT=Menlo]1.5M	/run[/FONT]
[FONT=Menlo]12M	/sbin[/FONT]
[FONT=Menlo]1.1G	/usr[/FONT]
[FONT=Menlo]4.0K	/srv[/FONT]
[FONT=Menlo]56K	/root[/FONT]
[FONT=Menlo]8.0K	/media[/FONT]
[FONT=Menlo]1.1G	/var[/FONT]
[FONT=Menlo]4.0K	/opt[/FONT]
[FONT=Menlo]9.6M	/bin[/FONT]
[FONT=Menlo]8.3M	/etc[/FONT]
[FONT=Menlo]16K	/lost+found[/FONT]
[FONT=Menlo]72M	/boot[/FONT]
[FONT=Menlo]du: cannot access &#8216;/proc/27928/task/27928/fd/4&#8217;: No such file or directory[/FONT]
[FONT=Menlo]du: cannot access &#8216;/proc/27928/task/27928/fdinfo/4&#8217;: No such file or directory[/FONT]
[FONT=Menlo]du: cannot access &#8216;/proc/27928/fd/4&#8217;: No such file or directory[/FONT]
[FONT=Menlo]du: cannot access &#8216;/proc/27928/fdinfo/4&#8217;: No such file or directory[/FONT]
[FONT=Menlo]0	/proc[/FONT]
[FONT=Menlo]50G	/mnt[/FONT]
[FONT=Menlo]4.0K	/lib64[/FONT]
[FONT=Menlo]4.0K	/dev[/FONT]
[FONT=Menlo]0	/sys[/FONT]
[FONT=Menlo]56K	/home[/FONT]
[FONT=Menlo]0	/tmp[/FONT]
[FONT=Menlo]469M	/lib[/FONT]
[FONT=Menlo]53G	/[/FONT]
[FONT=Menlo]omar@FortisServer:~$ sudo du -h / --max-depth=1[/FONT]
[FONT=Menlo]1.5M	/run[/FONT]
[FONT=Menlo]12M	/sbin[/FONT]
[FONT=Menlo]1.1G	/usr[/FONT]
[FONT=Menlo]4.0K	/srv[/FONT]
[FONT=Menlo]56K	/root[/FONT]
[FONT=Menlo]8.0K	/media[/FONT]
[FONT=Menlo]1.1G	/var[/FONT]
[FONT=Menlo]4.0K	/opt[/FONT]
[FONT=Menlo]9.6M	/bin[/FONT]
[FONT=Menlo]8.3M	/etc[/FONT]
[FONT=Menlo]16K	/lost+found[/FONT]
[FONT=Menlo]72M	/boot[/FONT]
[FONT=Menlo]du: cannot access &#8216;/proc/27937/task/27937/fd/4&#8217;: No such file or directory[/FONT]
[FONT=Menlo]du: cannot access &#8216;/proc/27937/task/27937/fdinfo/4&#8217;: No such file or directory[/FONT]
[FONT=Menlo]du: cannot access &#8216;/proc/27937/fd/4&#8217;: No such file or directory[/FONT]
[FONT=Menlo]du: cannot access &#8216;/proc/27937/fdinfo/4&#8217;: No such file or directory[/FONT]
[FONT=Menlo]0	/proc[/FONT]
[FONT=Menlo]705G	/mnt[/FONT]
[FONT=Menlo]4.0K	/lib64[/FONT]
[FONT=Menlo]4.0K	/dev[/FONT]
[FONT=Menlo]0	/sys[/FONT]
[FONT=Menlo]56K	/home[/FONT]
[FONT=Menlo]0	/tmp[/FONT]
[FONT=Menlo]469M	/lib[/FONT]
[FONT=Menlo]707G	/[/FONT]
[FONT=Menlo]omar@FortisServer:~$ cd /var[/FONT]
[FONT=Menlo]omar@FortisServer:/var$ ls[/FONT]
[FONT=Menlo]backups  crash	local  log   opt  spool  webmin[/FONT]
[FONT=Menlo]cache	 lib	lock   mail  run  tmp[/FONT]
[FONT=Menlo]omar@FortisServer:/var$ cd ..[/FONT]
[FONT=Menlo]omar@FortisServer:/$ sudo du -h /var --max-depth=1[/FONT]
[FONT=Menlo]8.2M	/var/backups[/FONT]
[FONT=Menlo]412K	/var/webmin[/FONT]
[FONT=Menlo]4.0K	/var/opt[/FONT]
[FONT=Menlo]36K	/var/spool[/FONT]
[FONT=Menlo]18M	/var/log[/FONT]
[FONT=Menlo]206M	/var/cache[/FONT]
[FONT=Menlo]4.0K	/var/local[/FONT]
[FONT=Menlo]4.0K	/var/mail[/FONT]
[FONT=Menlo]4.0K	/var/tmp[/FONT]
[FONT=Menlo]4.0K	/var/crash[/FONT]
[FONT=Menlo]846M	/var/lib[/FONT]
[FONT=Menlo]1.1G	/var[/FONT]

---

### Post by Mike_Burt on 2014-12-09
Thanks for the help.. I found out where i had the problems..Files were being placed in the wrong place...Thanks a lot guys for your help!!!

---

