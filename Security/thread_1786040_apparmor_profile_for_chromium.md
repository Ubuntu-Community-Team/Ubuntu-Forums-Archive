---
title: "apparmor profile for chromium?"
date: 2011-06-19
forum: Security
---

### Post by phatypus on 2011-06-19
Hello,

I've downloaded the extra apparmor profiles using 

```

sudo aptitude install apparmor-profiles

```I enabled the chromium profile and realised it doesn't work out of the box.  I've glanced over the various apparmor docs and added the following rules to /etc/apparmor.d/local/usr.bin.chromium-browser in order to get chromium to work without logging problems:

```

/sys/devices/pci*/**/* r,
/sys/devices/system/cpu/**/* r,
/home/phatypus/.mozilla/firefox/* r,
/usr/bin/xdg-settings ixr,
/usr/bin/xdg-mime ixr,
/bin/which ixr,
/bin/readlink ixr,
/usr/bin/cut ixr,
/usr/bin/basename ixr,
/usr/bin/mawk ixr,
/usr/bin/gconftool-2 ixr,

```I wasn't too sure about my execute rules, so used the same rules as xdg-open found in /etc/apparmor.d/usr.bin.chromium-browser, which was:

```

/usr/bin/xdg-open ixr,

```**Can someone confirm that my additional rules are sound?**


Thanks.


p.s. I presume the profile shipped with apparmor-profiles doesn't work out of the box because it has lagged behind work done on chromium?

---

### Post by bodhi.zazen on 2011-06-19
/home/phatypus/ should be @{HOME}/

otherwise it is up to you to decide what you wish to allow, borwsers are most difficult as use varies.

I suggest you file a bug report on LP re: chromium profile.

---

