---
title: "Problem with installing Liquid War with apt-get"
date: 2005-06-10
forum: Repositories &amp; Backports
---

### Post by timelord726 on 2005-06-10
When I try to install Liquid War with apt-get, I get the following message:
```
danny@danny-cs-ubuntu:~$ sudo apt-get install liquidwar
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liballegro4.1 liquidwar-data
Suggested packages:
  timidity-patches liballegro4.1-plugin-esd liballegro4.1-plugin-arts
Recommended packages:
  liballegro4.1-plugin-jack
The following NEW packages will be installed:
  liballegro4.1 liquidwar liquidwar-data
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 189kB/3230kB of archives.
After unpacking 6636kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hoary/universe liquidwar 5.6.2-1ubuntu1 [189kB]
Fetched 189kB in 1s (112kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/l/liquidwar/liquidwar_5.6.2-1ubuntu1_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I've tried a bunch of different things but I always seem to end up getting that message.  Is that just me, or some kind of problem on the other end?

---

### Post by Xian on 2005-06-10
[QUOTE=timelord726]I've tried a bunch of different things but I always seem to end up getting that message.  Is that just me, or some kind of problem on the other end?[/QUOTE]
It would appear to be a file error on the server. Not your fault.

---

### Post by timelord726 on 2005-06-11
Thanks for setting my mind at ease.  :)

I've just discovered **apt-get install -f** too.  That helps.

---

