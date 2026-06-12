---
title: "root directory full"
date: 2014-07-15
forum: Server Platforms
---

### Post by warpaper on 2014-07-15
my root directory get 100% and I search around still can't figure which file occupied disk space, would anyone have any suggestion?

[FONT=courier new]root@server:/# df -h[/FONT]
[FONT=courier new]Filesystem                     Size  Used Avail Use% Mounted on[/FONT]
[FONT=courier new]/dev/mapper/server--vg-root     81G   79G     0 [COLOR=#ff0000]100%[/COLOR] /[/FONT]
[FONT=courier new]udev                           488M   12K  488M   1% /dev[/FONT]
[FONT=courier new]tmpfs                          100M  1.1M   99M   2% /run[/FONT]
[FONT=courier new]none                           5.0M     0  5.0M   0% /run/lock[/FONT]
[FONT=courier new]none                           497M     0  497M   0% /run/shm[/FONT]
[FONT=courier new]/dev/mapper/server--vg-tmp     4.8G   10M  4.6G   1% /tmp[/FONT]
[FONT=courier new]/dev/sdd1                      917G  674G  243G  74% /mnt/extD[/FONT]
[FONT=courier new]/dev/sde1                      1.8T  1.8T   51G  98% /mnt/extB1[/FONT]
[FONT=courier new]/dev/sdb1                      917G  725G  193G  80% /mnt/extP[/FONT]
[FONT=courier new]/dev/sdf3                      916G  832G   84G  91% /mnt/extM[/FONT]
[FONT=courier new]/dev/sdg1                      294G  120G  159G  43% /mnt/extB2[/FONT]
[FONT=courier new]/dev/sdc1                      1.8T  674G  1.1T  39% /mnt/extT[/FONT]
[FONT=courier new]/dev/mapper/server--vg-varlog  4.8G  3.5G  1.1G  78% /var/log[/FONT]
[FONT=courier new]/dev/sda1                      236M  139M   85M  63% /boot[/FONT]
[FONT=courier new]root@server:/#[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]root@server:/# sudo find / -name '*' -size +1G | egrep -iv -e home -e mnt[/FONT]
[FONT=courier new]find: `/proc/1185/task/1185/fd/4': No such file or directory[/FONT]
[FONT=courier new]find: `/proc/1185/task/1185/fdinfo/4': No such file or directory[/FONT]
[FONT=courier new]find: `/proc/1185/fd/4': No such file or directory[/FONT]
[FONT=courier new]find: `/proc/2257/task/2257/fd/5': No such file or directory[/FONT]
[FONT=courier new]find: `/proc/2257/task/2257/fdinfo/5': No such file or directory[/FONT]
[FONT=courier new]find: `/proc/2257/fd/5': No such file or directory[/FONT]
[FONT=courier new]find: `/proc/2257/fdinfo/5': No such file or directory[/FONT]
[FONT=courier new]/var/log/lsyncd/lsyncd.log[/FONT]
[FONT=courier new]root@server:/#[/FONT]

---

### Post by steeldriver on 2014-07-15
Hello and welcome to the forums

Since your 'df' output does not appear to show a separate /home partition, you should probably not exclude /home when searching for large files

You could also us 'du' to narrow down the directories in which the disk usage is concentrated, e.g. something like

```

sudo du --exclude={dev,proc,runs,sys} -hxd3 / | sort -hr | head -n 10

```

---

### Post by warpaper on 2014-07-16
Since I create symbolic link under /home/user/extD -> /mnt/extD, where extD is external USB disk which is very large.

Therefore I exclude this in my du search.

Thanks for your reminder.

> **steeldriver said:**
> Hello and welcome to the forums

Since your 'df' output does not appear to show a separate /home partition, you should probably not exclude /home when searching for large files

You could also us 'du' to narrow down the directories in which the disk usage is concentrated, e.g. something like

```

sudo du --exclude={dev,proc,runs,sys} -hxd3 / | sort -hr | head -n 10

```

---

