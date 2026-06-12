---
title: "Question about how login stats are calculated on 12.04 LTS"
date: 2013-03-09
forum: Server Platforms
---

### Post by MakOwner on 2013-03-09
If you install from the "minimal install" ISO you get a prompt near the end to enable automaigically applying security updates.
I usually elect for that option -- one of the other things that happens when you take that option is that you get a cute little login script that provides some interesting statistics along how many pending updates are available and if a restart is required.  I find this mildy amusing, and other than the extra time it causes at login, never thught too much about it until I noticed this:


```

Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-38-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Mar  9 11:29:28 CST 2013

  System load:  0.0                Processes:            98
  Usage of /:   0.8% of 450.20GB   Users logged in:      0
  Memory usage: 1%                 IP address for bond0: xxx.xxx.xxx.xxx
  Swap usage:   0%

  => /mnt/md0 is using 88.0% of 9.40TB

  Graph this data and manage this system at https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

Last login: Sat Mar  9 10:49:34 2013 from 

:~$ df
Filesystem       1K-blocks       Used Available Use% Mounted on
/dev/sda3        472069424    3686732 444402868   1% /
/dev/md0p1     10095015976 8879129108 703089336  93% /mnt/md0

:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3       451G  3.6G  424G   1% /
/dev/md0p1      9.5T  8.3T  671G  93% /mnt/md0


```



After a certain utilization point on any given system the login descript displays a usage indicator regarding the level of utilization -- in this case the login script is squawking about 88% of /dev/md0p1 being used.
runing 'df' or 'df -h' reveals utilization is actually a bit higher.

Not really a big deal, but it isn an interesting quirk. is this just the difference in calculating MiB vs MB?

Anyone have any experience with the set of packages that provide these login scripts?  I know it's more than one package, as I tried to add it to a server without the option selected during installation.

---

### Post by Cheesemill on 2013-03-09
> **MakOwner said:**
> If you install from the "minimal install" ISO you get a prompt near the end to enable automaigically applying security updates.
I usually elect for that option -- one of the other things that happens when you take that option is that you get a cute little login script that provides some interesting statistics along how many pending updates are available and if a restart is required.

I'm not actually answering your question but this script has nothing to do with whether you select automatic updates or not.

I never choose to have automatic updates when I do a server installation but I still have this information displayed every time I log in.

For more information on the MOTD (message of the day) script see here...
[https://help.ubuntu.com/10.04/serverguide/pam_motd.html](https://help.ubuntu.com/10.04/serverguide/pam_motd.html)

If you want to know exactly where the information is coming from you should take a look at the scripts in the /etc/update-motd.d folder, you may find an answer to your question here.

---

### Post by schragge on 2013-03-09
Sorry, but
```

[COLOR=green]$[/COLOR] expr 8879129108 \* 100 / 10095015976
[COLOR=green]87[/COLOR]
[COLOR=green]$[/COLOR] echo $((8879129108*100/10095015976))
[COLOR=green]87[/COLOR]
[COLOR=green]$[/COLOR] echo 'scale=1;8879129108*100/10095015976'|bc
[COLOR=green]87.9[/COLOR]

```
Don't forget that 5% of space on each ext2/3/4 filesystem are reserved for root user. To see how many bytes are reserved for root, try
```

sudo dumpe2fs -h /dev/md0p1 2>/dev/null|sed -nr 's/^(Reserved block count|Block size): *//p'|paste -sd\*|bc

```

---

### Post by MakOwner on 2013-03-09
Interesting - it may not be associated witth that selection, but selecting 'basic server' and 'openssh' along with that option is the only way I have ever seen it.
I chased the scripts down once, but it was back when 10.04 was fairly new.

---

### Post by MakOwner on 2013-03-09
> **schragge said:**
> Sorry, but
```

[COLOR=green]$[/COLOR] expr 8879129108 \* 100 / 10095015976
[COLOR=green]87[/COLOR]
[COLOR=green]$[/COLOR] echo $((8879129108*100/10095015976))
[COLOR=green]87[/COLOR]
[COLOR=green]$[/COLOR] echo 'scale=1;8879129108*100/10095015976'|bc
[COLOR=green]87.9[/COLOR]

```
Don't forget that 5% of space on each ext2/3/4 filesystem are reserved for root user. To see, how many bytes are reserved for root, try
```

sudo dumpe2fs -h /dev/md0p1 2>/dev/null|sed -nr 's/^(Reserved block count|Block size): *//p'|paste -sd\*|bc

```


And that was the other thing I was thinking about.  
Thanks for the method of calculating root reservation overhead!

---

### Post by schragge on 2013-03-09
> **MakOwner said:**
> Thanks for the method of calculating root reservation overhead!You're welcome. This even may be shortened as
```
sudo tune2fs -l /dev/md0p1|sed -nr 's/(R.*t|B.*e): *//p'|paste -sd\*|bc
``` but the first form is more readable. If the filesystem is mounted, it may be simplified further by using mount point instead of device name:
```
stat -fc'(%f-%a)*%S' /mnt/md0|bc
```

---

### Post by Cheesemill on 2013-03-09
I've tracked down the scripts that display the info, they live in /usr/lib/python2.7/dist-packages/landscape/sysinfo/.
The relevant script for your question is disk.py.
My python isn't too good but I'm sure someone else can figure it out, the script is as follows...
```
from __future__ import division

import os

from twisted.internet.defer import succeed

from landscape.lib.disk import get_mount_info, get_filesystem_for_path


# List of filesystem types authorized when generating disk use statistics.
STABLE_FILESYSTEMS = set(
    ["ext", "ext2", "ext3", "ext4", "reiserfs", "ntfs", "msdos", "dos", "vfat",
     "xfs", "hpfs", "jfs", "ufs", "hfs", "hfsplus"])


def format_megabytes(megabytes):
    if megabytes >= 1024*1024:
        return "%.2fTB" % (megabytes/(1024*1024))
    elif megabytes >= 1024:
        return "%.2fGB" % (megabytes/1024)
    else:
        return "%dMB" % (megabytes)


def usage(info):
    total = info["total-space"]
    used = total - info["free-space"]
    return "%0.1f%% of %s" % ((used / total) * 100, format_megabytes(total))


class Disk(object):

    def __init__(self, mounts_file="/proc/mounts", statvfs=os.statvfs):
        self._mounts_file = mounts_file
        self._statvfs = statvfs

    def register(self, sysinfo):
        self._sysinfo = sysinfo

    def run(self):
        main_info = get_filesystem_for_path("/home", self._mounts_file,
                                            self._statvfs, STABLE_FILESYSTEMS)
        if main_info is not None:
            total = main_info["total-space"]
            if total <= 0:
                root_main_info = get_filesystem_for_path(
                    "/", self._mounts_file, self._statvfs, STABLE_FILESYSTEMS)
                if root_main_info is not None:
                    total = root_main_info["total-space"]
                    main_info = root_main_info
            if total <= 0:
                main_usage = "unknown"
            else:
                main_usage = usage(main_info)
            self._sysinfo.add_header("Usage of " + main_info["mount-point"],
                                     main_usage)
        else:
            self._sysinfo.add_header("Usage of /home", "unknown")

        seen_mounts = set()
        seen_devices = set()
        infos = list(get_mount_info(self._mounts_file, self._statvfs,
                                    STABLE_FILESYSTEMS))
        infos.sort(key=lambda i: len(i["mount-point"]))
        for info in infos:
            total = info["total-space"]
            mount_seen = info["mount-point"] in seen_mounts
            device_seen = info["device"] in seen_devices
            seen_mounts.add(info["mount-point"])
            seen_devices.add(info["device"])
            if mount_seen or device_seen:
                continue

            if total <= 0:
                # Some "virtual" filesystems have 0 total space. ignore them.
                continue

            used = ((total - info["free-space"]) / total) * 100
            if used >= 85:
                self._sysinfo.add_note("%s is using %s"
                                       % (info["mount-point"], usage(info)))
        return succeed(None)
```

---

### Post by schragge on 2013-03-09
landscape.lib.disk comes with the package *landscape-common*. get_mount_info calls [os.statvfs]("http://docs.python.org/2/library/os.html#os.statvfs").
```

Python 2.7.3 (default, Jan  2 2013, 13:56:14)
[GCC 4.7.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> [COLOR=#0000ff]import os, statvfs[/COLOR]
>>> [COLOR=#0000ff]s=os.statvfs("/")[/COLOR]
>>> [COLOR=#0000ff]print s[statvfs.F_BSIZE], s[statvfs.F_BLOCKS], s[statvfs.F_BFREE][/COLOR]
4096 2322270 501922
>>>

```

---

