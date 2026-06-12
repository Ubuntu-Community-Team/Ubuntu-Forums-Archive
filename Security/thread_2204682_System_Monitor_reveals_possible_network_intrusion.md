---
title: "System Monitor reveals possible network intrusion?"
date: 2014-02-09
forum: Security
---

### Post by michael2009 on 2014-02-09
Hi. i am posting this here because the title fits and I don't want to duplicate it with a new thread. I don't intend to hijack this thread, but if anyone thinks my post should not be here, pls tell me and I'll post it somewhere else.

The Network History bar in System Monitor shows 2-5KiB/s being received continuously even though my browser is closed and there are no downloads or torrents that I have initiated:


[ATTACH=CONFIG]250217[/ATTACH]  


When I checked the running processes I discovered the following process, mission-control-5, and I opened the properties window. Over a period of about ten seconds, the process changed itself twice, from [gnome-shell], to [tracker-miner-fs], then to [mission-control-5], after which the window abruptly closed itself:[INDENT]
[/INDENT]
[INDENT=3][ATTACH=CONFIG]250215[/ATTACH]
[/INDENT]
       [ATTACH=CONFIG]250216[/ATTACH][INDENT=3][ATTACH=CONFIG]250214[/ATTACH]
[/INDENT]
 








[INDENT=2]








[/INDENT]

Is this weird or what?!! 

 
I have been using Ubuntu for five years and never noticed a problem with security. The only possible recent event that I can think of is that I installed the Tor browser about a week ago. Could that be a possible cause?

---

### Post by QIII on 2014-02-09
Moved to its own thread.

---

### Post by fugu2 on 2014-02-09
Don't you just love all the hidden extra goodies that ubuntu decide to throw into their OS? 
```
$ apt-file search mission-control-5
...
telepathy-mission-control-5: /usr/lib/telepathy/mission-control-5
...

```
i havent yet tried to 'sudo apt-get purge telepathy-mission-control-5' usually these things are so
integrated that you'll end up uninstalling half the OS. I usuall just move the file to my garbage directory
```
sudo mv /usr/lib/telepathy/mission-control-5 ~/garbage-bins/
```
you'll find this one floating around there too probably
```
$ apt-file search ubuntu-geoip-provider
geoclue-ubuntu-geoip: /usr/lib/ubuntu-geoip/ubuntu-geoip-provider

```
again, mv

---

### Post by michael2009 on 2014-02-09
Hi. Thanks QIII. 

Umm... Thanks for the reply fugu2. The command didn't work ... :confused:

~$ sudo mv /usr/lib/telepathy/mission-control-5 ~/garbage-bins/
[sudo] password for admin: 
mv: cannot create regular file `/home/admin/garbage-bins/': Not a directory

I checked the processes again. So what is [tracker-miner-fs] ??? :

[ATTACH=CONFIG]250222[/ATTACH]





































I have also noticed that the RAM is currently using over 1GB, which is way above normal for just running the browser. 

I am planning to wipe and reformat the whole disk, and go for a new install, following the security pages advice. I cannot afford to waste time with suspicious internet activity eating into my limited quota of 5GB. The only problem is that I have a lot of useful packages installed and I haven't worked out how to save them. I have a very slow internet connection here, no broadband, so I do not want to have to download them all over again. 

Any advice?

---

### Post by cariboo on 2014-02-09
If you have limited bandwidth, I'd suggest you install one of the other Ubuntu flavours, as they don't include as many applications that phone home. Try Xubuntu or Lubuntu.

As far as saving the packages for applications you have downloaded and installed, if you haven't run:

```
sudo apt-get clean
```

all the archived packages are located in /var/cache/apt/archives. You can copy them all to another location for usage later.

---

### Post by michael2009 on 2014-02-09
Thanks cariboo907. I checked the apt archives, there are some recently installed packages there. I use bleachbit quite often, so I think I probably removed most of the packages I installed a while back. 

I used to have lubuntu installed on an old laptop, but I much prefer Ubuntu LTS. This is a new laptop, with 2GB RAM, and it worked just great with the GNOME desktop, until now. A clean install is what I need. Thanks anyway.

---

### Post by fugu2 on 2014-02-10
> **michael2009 said:**
> Umm... Thanks for the reply fugu2. The command didn't work ... :confused:
~$ sudo mv /usr/lib/telepathy/mission-control-5 ~/garbage-bins/
[sudo] password for admin: 
mv: cannot create regular file `/home/admin/garbage-bins/': Not a directory

I checked the processes again. So what is [tracker-miner-fs] ??? :

Sorry i forgot you need to create a directory garbage-bins before you move stuff into it
(or you can move it anywhere really, just so the startup program can't find it)
```
$ mkdir ~/garbage-bins

```
I'm not sure what [tracker-miner-fs] is...
```
$ apt-file search tracker-miner-fs
libtracker-miner-0.14-dev: /usr/include/tracker-0.14/libtracker-miner/tracker-miner-fs.h
tracker-dbg: /usr/lib/debug/usr/lib/tracker/tracker-miner-fs
tracker-miner-fs: /etc/xdg/autostart/tracker-miner-fs.desktop
tracker-miner-fs: /usr/lib/tracker/tracker-miner-fs
tracker-miner-fs: /usr/share/doc/tracker-miner-fs/changelog.Debian.gz
tracker-miner-fs: /usr/share/doc/tracker-miner-fs/copyright
tracker-miner-fs: /usr/share/lintian/overrides/tracker-miner-fs
tracker-miner-fs: /usr/share/man/man1/tracker-miner-fs.1.gz

```
tracker-miner-fs
metadata database, indexer and search tool - filesystem indexer
 
This package contains the tracker indexer for indexing your files and folders.

Tracker is an advanced framework for first class objects with associated
metadata and tags. It provides a one stop solution for all metadata, tags,
shared object databases, search tools and indexing.
You should try and 
```
$ man tracker-miner-fs
```

---

