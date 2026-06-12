---
title: "Ubuntu Server headless 18.04.4 LTS - Segmentation fault (core dumped)"
date: 2020-02-07
forum: Server Platforms
---

### Post by Rui_Duarte on 2020-02-07
Hello,

I have a machine running Ubuntu Server 18.04.4 LTS and I get this error after:

```
XXXX@cooookie:~$ sudo apt-get update
Hit:1 http://pt.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://pt.archive.ubuntu.com/ubuntu bionic-security InRelease
Hit:3 http://pt.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:4 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease
Hit:5 http://ppa.launchpad.net/xapienz/curl34/ubuntu bionic InRelease
Segmentation fault (core dumped)
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'test -x /usr/bin/apt-show-versions || exit 0 ; apt-show-versions -i'
E: Sub-process returned an error code
```

Any clues?

Thanks in advance!

---

### Post by LHammonds on 2020-02-07
Make sure your connection to the Internet is solid and DNS is working flawlessly.

I have not seen that error before but 1st thing I would do is to delete the local cache that "apt-get update" pulls down and try again.  It could be related to locally corrupted list files.

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
```

---

### Post by Rui_Duarte on 2020-02-07
same error..

```
Last login: Fri Feb  7 13:44:50 2020 from xxxxxxxxx
xxxxxx@cooookie:~$ sudo rm -r /var/lib/apt/lists/*
[sudo] password for XXXXX:
xxxxx@cooookie:~$ sudo apt-get clean
xxxxx@cooookie:~$ sudo apt-get update
Get:1 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease [20.8 kB]
Get:2 http://pt.archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:3 http://pt.archive.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Get:4 http://pt.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:5 http://ppa.launchpad.net/xapienz/curl34/ubuntu bionic InRelease [15.9 kB]
Get:6 http://ppa.launchpad.net/ondrej/php/ubuntu bionic/main amd64 Packages [52.0 kB]
Get:7 http://ppa.launchpad.net/ondrej/php/ubuntu bionic/main i386 Packages [52.0 kB]
Get:8 http://ppa.launchpad.net/ondrej/php/ubuntu bionic/main Translation-en [24.8 kB]
Get:9 http://pt.archive.ubuntu.com/ubuntu bionic/universe Sources [9,051 kB]
Get:10 http://pt.archive.ubuntu.com/ubuntu bionic/restricted Sources [5,324 B]
Get:11 http://pt.archive.ubuntu.com/ubuntu bionic/multiverse Sources [181 kB]
Get:12 http://pt.archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1,019 kB]
Get:13 http://pt.archive.ubuntu.com/ubuntu bionic/main i386 Packages [1,007 kB]
Get:14 http://pt.archive.ubuntu.com/ubuntu bionic/main Translation-en [516 kB]
Get:15 http://pt.archive.ubuntu.com/ubuntu bionic/main Translation-en_GB [432 kB]
Get:16 http://pt.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [9,184 B]
Get:17 http://pt.archive.ubuntu.com/ubuntu bionic/restricted i386 Packages [9,156 B]
Get:18 http://pt.archive.ubuntu.com/ubuntu bionic/restricted Translation-en_GB [2,072 B]
Get:19 http://pt.archive.ubuntu.com/ubuntu bionic/restricted Translation-en [3,584 B]
Get:20 http://pt.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [8,570 kB]
Get:21 http://pt.archive.ubuntu.com/ubuntu bionic/universe i386 Packages [8,531 kB]
Get:22 http://pt.archive.ubuntu.com/ubuntu bionic/universe Translation-en [4,941 kB]
Get:23 http://pt.archive.ubuntu.com/ubuntu bionic/universe Translation-en_GB [4,118 kB]
Get:24 http://pt.archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages [144 kB]
Get:25 http://pt.archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [151 kB]
Get:26 http://pt.archive.ubuntu.com/ubuntu bionic/multiverse Translation-en [108 kB]
Get:27 http://pt.archive.ubuntu.com/ubuntu bionic/multiverse Translation-en_GB [82.1 kB]
Get:28 http://pt.archive.ubuntu.com/ubuntu bionic-security/universe Sources [166 kB]
Get:29 http://pt.archive.ubuntu.com/ubuntu bionic-security/restricted Sources [4,528 B]
Get:30 http://pt.archive.ubuntu.com/ubuntu bionic-security/multiverse Sources [3,184 B]
Get:31 http://pt.archive.ubuntu.com/ubuntu bionic-security/main i386 Packages [436 kB]
Get:32 http://pt.archive.ubuntu.com/ubuntu bionic-security/main amd64 Packages [632 kB]
Get:33 http://pt.archive.ubuntu.com/ubuntu bionic-security/main Translation-en [207 kB]
Get:34 http://pt.archive.ubuntu.com/ubuntu bionic-security/restricted amd64 Packages [20.6 kB]
Get:35 http://pt.archive.ubuntu.com/ubuntu bionic-security/restricted i386 Packages [4,280 B]
Get:36 http://pt.archive.ubuntu.com/ubuntu bionic-security/restricted Translation-en [5,872 B]
Get:37 http://pt.archive.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [643 kB]
Get:38 http://pt.archive.ubuntu.com/ubuntu bionic-security/universe i386 Packages [615 kB]
Get:39 http://pt.archive.ubuntu.com/ubuntu bionic-security/universe Translation-en [216 kB]
Get:40 http://pt.archive.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [6,328 B]
Get:41 http://pt.archive.ubuntu.com/ubuntu bionic-security/multiverse i386 Packages [4,284 B]
Get:42 http://pt.archive.ubuntu.com/ubuntu bionic-security/multiverse Translation-en [2,640 B]
Get:43 http://pt.archive.ubuntu.com/ubuntu bionic-updates/restricted Sources [6,520 B]
Get:44 http://pt.archive.ubuntu.com/ubuntu bionic-updates/multiverse Sources [5,840 B]
Get:45 http://pt.archive.ubuntu.com/ubuntu bionic-updates/universe Sources [276 kB]
Get:46 http://pt.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [850 kB]
Get:47 http://pt.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [641 kB]
Get:48 http://pt.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [297 kB]
Get:49 http://pt.archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [29.7 kB]
Get:50 http://pt.archive.ubuntu.com/ubuntu bionic-updates/restricted i386 Packages [9,568 B]
Get:51 http://pt.archive.ubuntu.com/ubuntu bionic-updates/restricted Translation-en [7,848 B]
Get:52 http://pt.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [1,007 kB]
Get:53 http://pt.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,048 kB]
Get:54 http://pt.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [324 kB]
Get:55 http://pt.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [9,704 B]
Get:56 http://pt.archive.ubuntu.com/ubuntu bionic-updates/multiverse i386 Packages [7,480 B]
Get:57 http://pt.archive.ubuntu.com/ubuntu bionic-updates/multiverse Translation-en [4,576 B]
Get:58 http://ppa.launchpad.net/xapienz/curl34/ubuntu bionic/main i386 Packages [1,928 B]
Get:59 http://ppa.launchpad.net/xapienz/curl34/ubuntu bionic/main amd64 Packages [1,936 B]
Get:60 http://ppa.launchpad.net/xapienz/curl34/ubuntu bionic/main Translation-en [1,100 B]
Fetched 47.0 MB in 15s (3,132 kB/s)
Segmentation fault (core dumped)
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'test -x /usr/bin/apt-show-versions || exit 0 ; apt-show-versions -i'
E: Sub-process returned an error code
XXXXX@cooookie:~$

```

---

### Post by Rui_Duarte on 2020-02-14
I managed to fix my problem with reverting to a previous kernel and then fix some errors and then update and all worked.!

---

### Post by LHammonds on 2020-02-14
That's great.  Thanks for letting us know what you did to solve it.  You can edit the thread and select the "[SOLVED]" dropdown so others know.

---

