---
title: "Blank update!?"
date: 2021-07-27
forum: Security
---

### Post by triplemaya on 2021-07-27
The software updater is showing 1.3mb of software to be downloaded, but there is no description. The main window area is blank. Should this worry me?

---

### Post by TheFu on 2021-07-27
Run 
```
sudo apt update
sudo apt upgrade
```

Any errors?  Might be useful to throw the output to a log file and review the logs.  That would be :
```
sudo apt update |tee /tmp/log.update
sudo apt upgrade  |tee -a  /tmp/log.update 
```

GUI programs often lie.

---

### Post by deadflowr on 2021-07-27
is it something like this:
[https://ubuntuforums.org/showthread.php?t=2394240]("https://ubuntuforums.org/showthread.php?t=2394240")

---

### Post by triplemaya on 2021-07-28
Thanks for the responses. 

Yes to deadflower, that is exactly what it looks like.

I thought of doing a manual update / upgrade but my whole concern is that the system has been hacked. Massively unlikely I am sure, but surely this is just the kind of thing one should be cautious about. No?

This is the output of sudo apt update |tee /tmp/log.update

Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Get:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease [1,811 B]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Get:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,084 B]
Hit:7 [https://apt.syncthing.net](https://apt.syncthing.net) syncthing InRelease
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [1,127 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 c-n-f Metadata [13.8 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [843 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [626 kB]
Fetched 2,940 kB in 2s (1,530 kB/s)
Reading package lists...
Building dependency tree...
Reading state information...
8 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages will be upgraded:
  aspell libaspell15 libglib2.0-0 libglib2.0-bin libglib2.0-data
  networkd-dispatcher syncthing ubuntu-advantage-tools
8 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
2 standard security updates
Need to get 12.1 MB/12.5 MB of archives.
After this operation, 45.1 kB of additional disk space will be used.
Do you want to continue? [Y/n]

---

### Post by TheFu on 2021-07-28
```
Do you want to continue? [Y/n]
```

Y<enter>


Nothing funny in that output.

---

### Post by triplemaya on 2021-07-28
Sorry, I am being dense. All that is obviously ok. And that I assume is what would normally be in the gui.
So that is all I need to know.
Thanks.

---

