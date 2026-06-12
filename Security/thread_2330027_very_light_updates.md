---
title: "very light updates"
date: 2016-07-07
forum: Security
---

### Post by skywalker4 on 2016-07-07
*Security updates
  -Ubuntu base 169kb

*other updates
  -Software & Updates 77kb
-Ubuntu base **_8kb_**

Does it look like standard?? im a n00b but looking at 8kb update feel weird

---

### Post by howefield on 2016-07-07
> **skywalker4 said:**
> Does it look like standard?? im a n00b but looking at 8kb update feel weird

Click on the expand button to get an idea of exactly what part of the Ubuntu Base os being updated... what does it show ?

---

### Post by skywalker4 on 2016-07-07
[IMG]https://s32.postimg.org/ua26ri3hh/ubuntuforums.png[/IMG]

Look like this. thanks for your time

---

### Post by howefield on 2016-07-07
Highlight the "Time zone and daylight-saving time data" line and then on the expand button for "Technical Description", it is probably just a border change or some other tiny little alteration.

---

### Post by skywalker4 on 2016-07-07
> Changes for tzdata versions:
Installed version: 2016d-0ubuntu0.16.04
Available version: 2016f-0ubuntu0.16.04

Version 2016f-0ubuntu0.16.04: 

  * New upstream release, reverting DST change for Africa/Cairo,
    and updating Asia/Novosibirsk to +07 on 2016-07-24 at 02:00.


Version 2016e-0ubuntu0.16.04: 

  * New upstream release, with changes to DST in Africa/Cairo on July 7.



> This package contains data required for the implementation of standard local time for many representative locations around the globe. It is updated periodically to reflect changes made by political bodies to time zone boundaries, UTC offsets, and daylight-saving rules.

so nothing. but it still look weird so light updates. probably because im just an ignorant

---

### Post by mörgæs on 2016-07-07
One of the beauties of open source software is that an application is split into many tiny parts, each of which can be changed or reused by others. 

This in contrast to closed source where you get the application as one big unit. The Windows way of delivering huge chunks of updates is common but not an ideal.

---

### Post by howefield on 2016-07-07
Looks good to me, wish more updates were as small :) 

tzdata is a tiny application to start with.

Description from a 16.10 installation for info.

> hugh@yakkety-laptop:~$ apt show tzdata
Package: tzdata
Version: 2016e-1
Priority: required
Section: libs
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 2,842 kB
Provides: tzdata-stretch
Depends: debconf (>= 0.5) | debconf-2.0
Replaces: libc0.1, libc0.3, libc6, libc6.1
Homepage: [http://www.iana.org/time-zones](http://www.iana.org/time-zones)
Task: minimal
Supported: 9m
Download-Size: 170 kB
APT-Manual-Installed: yes
APT-Sources: [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) yakkety/main amd64 Packages
Description: time zone and daylight-saving time data
 This package contains data required for the implementation of
 standard local time for many representative locations around the
 globe. It is updated periodically to reflect changes made by
 political bodies to time zone boundaries, UTC offsets, and
 daylight-saving rules.


---

