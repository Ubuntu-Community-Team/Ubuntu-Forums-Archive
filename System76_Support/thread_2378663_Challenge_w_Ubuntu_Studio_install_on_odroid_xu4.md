---
title: "Challenge w/ Ubuntu Studio install on odroid xu4"
date: 2017-11-25
forum: System76 Support
---

### Post by jagua on 2017-11-25
OS- Ubuntu 16.04 Mate
Hardware- odroid xu4
Challenge- Upgrading to Ubuntu Studio via instructions from this link: [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

I did an update and upgrade in terminal before attemptin the studio upgrade. It all looked like it was going well until I got an error with calligralibs dependency needed for Krita and calligraplan. Now I cant seem to add any new software nor remove those packages. Here is the error when attempting:

```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 krita : Depends: calligra-libs (= 1:2.9.7-0ubuntu12) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
When I try 'apt-get -f install' I get this:

```
Preparing to unpack .../calligra-libs_1%3a2.9.7-0ubuntu12_armhf.deb ...
Unpacking calligra-libs (1:2.9.7-0ubuntu12) ...
dpkg: error processing archive /var/cache/apt/archives/calligra-libs_1%3a2.9.7-0ubuntu12_armhf.deb (--unpack):
 trying to overwrite '/usr/lib/kde4/kplatorcpsscheduler.so', which is also in package calligraplan 1:2.9.7-0ubuntu12
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 /var/cache/apt/archives/calligra-libs_1%3a2.9.7-0ubuntu12_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
What now??? I assume a problem with the odroid arm hardware compatibility? Can it be fixed, Or can I somehow reverse things so I can add other packages and do upgrades again [both seem impossible until these dependencies are dealt with].

---

