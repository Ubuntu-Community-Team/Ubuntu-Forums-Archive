---
title: "Unexpected Packages offered for Autoremove"
date: 2014-08-27
forum: Security
---

### Post by uRock on 2014-08-27
Starting about a week ago the terminal started offering packages available for **apt-get autoremove** and I am not sure when or why they would have been installed in the first place.

Should I be concerned?```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  [COLOR="#000080"]alien at debugedit librpmbuild3 librpmsign1 libsigsegv2 lsb-core
  lsb-security m4 ncurses-term pax rpm[/COLOR]
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Cheers & Beers,
uRock

---

### Post by QIII on 2014-08-27
Have you used alien to convert rpms to debs?

I do think it odd that several things associated with alien are listed there.

---

### Post by uRock on 2014-08-27
> **QIII said:**
> Have you used alien to convert rpms to debs?

I do think it odd that several things associated with alien are listed there.

No, which is why I am scratching my head. I am going to search log files to see if I can find when they were installed to see if they were installed as some kind of dependency when I get done with my honey-do chores.

---

### Post by uRock on 2014-08-27
The logs have proven themselve handy again. the output of```
zcat -f /var/log/dpkg.log* | grep "\ install\ " | sort
```led me to this. Seems like my attempt to install Google Earth, which failed, caused the installation of the above packages. 
```
2014-08-16 16:31:11 install google-earth-stable:amd64 <none> 7.1.2.2041-r0
2014-08-16 16:34:11 install libsigsegv2:amd64 <none> 2.10-2
2014-08-16 16:34:12 install dpkg-dev:all <none> 1.17.5ubuntu5.3
2014-08-16 16:34:13 install po-debconf:all <none> 1.0.16+nmu2ubuntu1
2014-08-16 16:34:14 install debhelper:all <none> 9.20131227ubuntu1
2014-08-16 16:34:14 install dh-apparmor:all <none> 2.8.95~2430-0ubuntu5
2014-08-16 16:34:15 install librpmio3:amd64 <none> 4.11.1-3
2014-08-16 16:34:16 install librpm3:amd64 <none> 4.11.1-3
2014-08-16 16:34:16 install librpmbuild3:amd64 <none> 4.11.1-3
2014-08-16 16:34:17 install librpmsign1:amd64 <none> 4.11.1-3
2014-08-16 16:34:17 install rpm2cpio:amd64 <none> 4.11.1-3
2014-08-16 16:34:17 install rpm-common:amd64 <none> 4.11.1-3
2014-08-16 16:34:18 install debugedit:amd64 <none> 4.11.1-3
2014-08-16 16:34:18 install rpm:amd64 <none> 4.11.1-3
2014-08-16 16:34:19 install alien:all <none> 8.90
2014-08-16 16:34:19 install at:amd64 <none> 3.1.14-1ubuntu1
2014-08-16 16:34:20 install g++-4.8:amd64 <none> 4.8.2-19ubuntu1
2014-08-16 16:34:20 install libstdc++-4.8-dev:amd64 <none> 4.8.2-19ubuntu1
2014-08-16 16:34:22 install build-essential:amd64 <none> 11.6ubuntu6
2014-08-16 16:34:22 install g++:amd64 <none> 4:4.8.2-1ubuntu6
2014-08-16 16:34:22 install heirloom-mailx:amd64 <none> 12.5-2
2014-08-16 16:34:23 install libc6-i386:amd64 <none> 2.19-0ubuntu6.1
2014-08-16 16:34:24 install lib32z1:amd64 <none> 1:1.2.8.dfsg-1ubuntu1
2014-08-16 16:34:24 install libalgorithm-diff-perl:all <none> 1.19.02-3
2014-08-16 16:34:25 install libalgorithm-diff-xs-perl:amd64 <none> 0.04-2build4
2014-08-16 16:34:25 install libalgorithm-merge-perl:all <none> 0.08-2
2014-08-16 16:34:26 install libsys-hostname-long-perl:all <none> 1.4-3
2014-08-16 16:34:27 install libmail-sendmail-perl:all <none> 0.79.16-1
2014-08-16 16:34:27 install m4:amd64 <none> 1.4.17-2ubuntu1
2014-08-16 16:34:28 install ncurses-term:all <none> 5.9+20140118-1ubuntu1
2014-08-16 16:34:29 install lsb-invalid-mta:all <none> 4.1+Debian11ubuntu6
2014-08-16 16:34:29 install pax:amd64 <none> 1:20120606-2+deb7u1
2014-08-16 16:34:30 install lsb-core:amd64 <none> 4.1+Debian11ubuntu6
2014-08-16 16:34:30 install lsb-security:amd64 <none> 4.1+Debian11ubuntu6
2014-08-16 16:38:15 install lib32bz2-1.0:amd64 <none> 1.0.6-5
2014-08-16 16:38:16 install lib32tinfo5:amd64 <none> 5.9+20140118-1ubuntu1
2014-08-16 16:38:17 install lib32ncurses5:amd64 <none> 5.9+20140118-1ubuntu1
2014-08-16 16:38:34 install google-earth-stable:amd64 7.1.2.2041-r0 7.1.2.2041-r0

```

---

### Post by QIII on 2014-08-27
Ah!  Interesting...

Logs are good!

---

