---
title: "dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) [Ubuntu Mate]"
date: 2014-10-10
forum: Ubuntu/Debian BASED
---

### Post by PocketDog on 2014-10-10
Using the software updater, I got a broken dependencies error. Ran **install -f**

```

[user]@TheLappy:~$ sudo apt-get install -f
[sudo] password for [user]: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mate-applets
The following packages will be upgraded:
  mate-applets
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/246 kB of archives.
After this operation, 124 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 369882 files and directories currently installed.)
Preparing to unpack .../mate-applets_1.8.1+dfsg1-1~trusty1_i386.deb ...
Unpacking mate-applets (1.8.1+dfsg1-1~trusty1) over (1.8.0+dfsg1-1~ppa1~trusty1) ...
dpkg: error processing archive /var/cache/apt/archives/mate-applets_1.8.1+dfsg1-1~trusty1_i386.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/cpufreq-selector.1.gz', which is also in package gnome-applets 3.5.92-0ubuntu3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/mate-applets_1.8.1+dfsg1-1~trusty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[user]@TheLappy:~$

```

The only relevant repository I have which can be broken relates to ubuntu-mate, so If I disable that I won't be able to update Mate any more.

Maybe rename '/usr/share/man/man1/cpufreq-selector.1.gz' as .bak and retry?

---

### Post by PocketDog on 2014-10-10
Ok, marked as solved although the fix isn't a good one. It's the fault of [this bug](https://bugs.launchpad.net/ubuntu-mate/+bug/1378666), fixed by purging gnome-applets and running apt-get install -f again.
```

dpkg -P gnome-applets

sudo apt-get install -f

```

This obviously disables applets in Gnome to solve the conflict, which isn't ideal.

---

### Post by slickymaster on 2014-10-10
*Moved to the ***Other Operating Systems and Projects*** sub-forum*

---

