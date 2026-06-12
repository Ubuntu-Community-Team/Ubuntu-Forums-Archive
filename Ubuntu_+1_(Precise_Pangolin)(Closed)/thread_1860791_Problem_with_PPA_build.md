---
title: "Problem with PPA build"
date: 2011-10-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sumski on 2011-10-15
I don't know is the problem caused with the new dpkg that entered Precise , or something else , but i can't build kde-workspace:

```
dh_shlibdeps  -plibkdecorations4 -plibkwineffects1abi2 -plibkwineffects1abi2-gles -plibkephal4abi1 -plibkscreensaver5 -plibksgrd4 -plibksignalplotter4 -plibkworkspace4 -pliblsofui4 -plibplasmaclock4abi2 -plibplasma-geolocation-interface4 -plibplasmagenericshell4 -plibprocesscore4abi1 -plibprocessui4a -plibsolidcontrol4abi2 -plibsolidcontrolifaces4abi2 -plibtaskmanager4abi2 -plibweather-ion6 -- -xkde-runtime
```
```
dpkg-shlibdeps: error: package. is not a valid version
```debian/* is the same as in official kubuntu packaging , except the version, and offcourse the different orig.tar.bz2
Didn't have any problems with it on oneiric - here's the entire buildlog:

[https://launchpadlibrarian.net/82812618/buildlog_ubuntu-precise-amd64.kde-workspace_4%3A4.7.2git20111014-precise%7Eppa1_FAILEDTOBUILD.txt.gz]("https://launchpadlibrarian.net/82812618/buildlog_ubuntu-precise-amd64.kde-workspace_4%3A4.7.2git20111014-precise%7Eppa1_FAILEDTOBUILD.txt.gz")

---

### Post by JMB74 on 2011-12-03
Says here that a fixed mesa 7.11-0ubuntu4 was published to fix those build errors.

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/878562](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/878562)

Looking at your build log it still seems to be pulling the old 7.11-0ubuntu[COLOR=Red]**3**[/COLOR] build deps?

EDIT: Never mind. Old thread and probably fixed now. 

The thread was bumped to the top by a spammer, and I didn't notice the date.

---

