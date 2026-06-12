---
title: "Crontab for update"
date: 2019-01-22
forum: Server Platforms
---

### Post by hack3rcon on 2019-01-22
Hello.
I'm using Ubuntu 18.04 LTS. I wrote a crontab like below:
```

00 6 * * 1 /bin/bash /home/user/update.sh >>/home/user/update.log

```
My "update.sh" file contents are like below:
```

#!/bin/bash
/usr/bin/apt-get update && /usr/bin/apt-get upgrade -y

```
But "update.log" tell me:
```

Ign:1 https://pkg.jenkins.io/debian binary/ InRelease
Hit:2 https://pkg.jenkins.io/debian binary/ Release
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Hit:5 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [705 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [713 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [176 kB]
Fetched 1,841 kB in 9s (200 kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages have been kept back:
  lxd lxd-client
The following packages will be upgraded:
  bsdutils e2fsprogs fdisk jenkins libblkid1 libcom-err2 libcups2 libext2fs2
  libfdisk1 libmount1 libsmartcols1 libss2 libuuid1 linux-firmware mount
  psmisc python3-software-properties software-properties-common util-linux
  uuid-runtime
20 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 75.9 MB/142 MB of archives.
After this operation, 3,245 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 bsdutils amd64 1:2.31.1-0.4ubuntu3.3 [60.4 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libuuid1 amd64 2.31.1-0.4ubuntu3.3 [20.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libblkid1 amd64 2.31.1-0.4ubuntu3.3 [124 kB]
Get:2 https://pkg.jenkins.io/debian binary/ jenkins 2.161 [74.0 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libfdisk1 amd64 2.31.1-0.4ubuntu3.3 [164 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libmount1 amd64 2.31.1-0.4ubuntu3.3 [136 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libsmartcols1 amd64 2.31.1-0.4ubuntu3.3 [83.8 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 fdisk amd64 2.31.1-0.4ubuntu3.3 [108 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 util-linux amd64 2.31.1-0.4ubuntu3.3 [902 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 mount amd64 2.31.1-0.4ubuntu3.3 [106 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 uuid-runtime amd64 2.31.1-0.4ubuntu3.3 [34.8 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libcups2 amd64 2.2.7-1ubuntu2.3 [211 kB]
Fetched 75.9 MB in 13min 28s (94.0 kB/s)
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable
dpkg: error: 2 expected programs not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin

```


What is my problem?

Thank you.

---

### Post by spjackson on 2019-01-22
PATH is different under cron. You can set it either in crontab or in your update.sh script, e.g.
```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

```

---

