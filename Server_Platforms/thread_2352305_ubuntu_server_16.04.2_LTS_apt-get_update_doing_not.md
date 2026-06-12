---
title: "ubuntu server 16.04.2 LTS apt-get update doing nothing"
date: 2017-02-11
forum: Server Platforms
---

### Post by mintz420 on 2017-02-11
```
root@owncloud:/etc/apt# apt-get update
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Ign:4 [https://download.owncloud.org/download/repositories/stable/Ubuntu_16.04](https://download.owncloud.org/download/repositories/stable/Ubuntu_16.04)  InRelease
Hit:5 [https://download.owncloud.org/download/repositories/stable/Ubuntu_16.04](https://download.owncloud.org/download/repositories/stable/Ubuntu_16.04)  Release
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Fetched 306 kB in 0s (368 kB/s)
Reading package lists... Done
root@owncloud:/etc/apt#
```

Always replies this when doing apt-get update.

---

### Post by howefield on 2017-02-11
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by mintz420 on 2017-02-11
ty for moving my thread I'm new.

---

### Post by deadflowr on 2017-02-11
Good, now the package cache is updated, try installing any updates
```
apt-get upgrade
```
apt-get update updates the package lists so that what is on the servers and what your machine knows are the same.
apt-get upgrade will actually install any updates, if any are available for any package you have.

---

### Post by howefield on 2017-02-11
> **mintz420 said:**
> ty for moving my thread I'm new.

You're welcome.

So what's the problem.. apt update can't be accused of "doing nothing" as it is going out and successfully querying your repositories according to the output that you posted. What's your complaint ?

---

### Post by mintz420 on 2017-02-11
already did this

-apt-get update
-apt-get upgrade
-apt upgrade
-apt full-upgrade
-apt-get dist-upgrade
-apt-get clean
-rm -rf /var/lib/apt/lists/*

---

### Post by Bashing-om on 2017-02-11
mintz420; Hello, Welcome to the forum .

" sudo apt update " and what do you expect the result to be ?
All this command does is sync the respective data bases to what is in the mirror . At this point there is no effect on installed packages.
To actually effect the update of installed packages are the commands ( among others ) :
```

sudo apt upgrade
sudo apt full-upgrade

```
giving you, the system administrator, advisement on what will be upgraded if when you "y" to the advisement.

[INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT]

---

### Post by mintz420 on 2017-02-11
already did that too

---

### Post by deadflowr on 2017-02-11
If you get no errors and no listings of new packages when running the upgrade/dist-upgrade commands, then the system is up-to-date.
Quite possible that it was updated automatically with the unattended-upgrades utility.
look in the log file for the unattended-upgrades at
/var/log/unattended-upgrades/unattended-upgrades.log

---

### Post by mintz420 on 2017-02-11
ok thank you ;)

```
2016-11-28 12:33:30,817 INFO Initial blacklisted packages:
2016-11-28 12:33:30,818 INFO Initial whitelisted packages:
2016-11-28 12:33:30,818 INFO Starting unattended upgrades script
2016-11-28 12:33:30,818 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubun$
2016-11-28 12:39:07,448 INFO Packages that will be upgraded: linux-generic linu$
2016-11-28 12:39:07,449 INFO Writing dpkg log to '/var/log/unattended-upgrades/$
2016-11-28 12:40:25,347 INFO All upgrades installed
2016-12-05 12:11:27,157 INFO Initial blacklisted packages:
2016-12-05 12:11:27,157 INFO Initial whitelisted packages:
2016-12-05 12:11:27,157 INFO Starting unattended upgrades script
2016-12-05 12:11:27,158 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubun$
2016-12-05 12:11:30,889 INFO No packages found that can be upgraded unattended $
2017-01-09 12:35:01,333 INFO Initial blacklisted packages:
2017-01-09 12:35:01,348 INFO Initial whitelisted packages:
2017-01-09 12:35:01,349 INFO Starting unattended upgrades script
2017-01-09 12:35:01,349 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubun$
2017-01-09 12:38:19,664 INFO Packages that will be upgraded: apport apt apt-tra$
2017-01-09 12:38:19,665 INFO Writing dpkg log to '/var/log/unattended-upgrades/$
2017-01-09 12:41:13,626 INFO All upgrades installed
```

---

### Post by cariboo on 2017-02-11
This is what the result of:

```
sudo apt update
```

looks like on my zesty laptop:

```
Fetched 37.7 MB in 25s (1,488 kB/s)                                            
Reading package lists... Done
Building dependency tree        
Reading state information... Done
34 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

---

### Post by deadflowr on 2017-02-11
The unattended-upgrades log tells you all updates have been applied.
If there were problems, it would have stated such.
You can dig deeper by looking at the unattended-upgrades-dpkg log.

---

