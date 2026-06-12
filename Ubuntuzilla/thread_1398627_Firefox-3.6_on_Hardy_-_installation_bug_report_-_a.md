---
title: "Firefox-3.6 on Hardy - installation bug report - apparmor_parser"
date: 2010-02-04
forum: Ubuntuzilla
---

### Post by gmargo on 2010-02-04
I just installed Firefox 3.6+nobinonly-0ubuntu1~mfs~hardy1 on Hardy 8.04.4 (fully up to date), and received a non-fatal error.

The **postinst** script calls **apparmor_parser** with a "-T" option but the apparmor on Hardy (2.1+1075-0ubuntu9.2) does not support a "-T" option.

Text from "aptitude -V -R install firefox firefox-branding":
```

(irrelevant stuff snipped)
The following NEW packages will be installed:
  firefox [3.6+nobinonly-0ubuntu1~mfs~hardy1] firefox-branding [3.6+nobinonly-0ubuntu1~mfs~hardy1]
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.8MB of archives. After unpacking 29.2MB will be used.
Writing extended state information... Done
(Reading database ... 190667 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6+nobinonly-0ubuntu1~mfs~hardy1_i386.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.6+nobinonly-0ubuntu1~mfs~hardy1_i386.deb) ...
Setting up firefox-branding (3.6+nobinonly-0ubuntu1~mfs~hardy1) ...

Setting up firefox (3.6+nobinonly-0ubuntu1~mfs~hardy1) ...
apparmor_parser: invalid option -- T
Novell/SUSE AppArmor parser version 2.1
Copyright (C) 1999, 2000, 2003, 2004, 2005, 2006 Novell Inc.

Usage: apparmor_parser [options] [profile]

Options:
--------
-a, --add               Add apparmor definitions [default]
(balance of usage snipped, but it does not include a -T)

```

---

### Post by nanotube on 2010-02-04
Hi

From the package name, I'm gathering that you did not use the ubuntuzilla repository to install. 

maybe you're using firefox-stable, or the ubuntu-mozilla-daily repository? in either case, your best bet is to ask on the general forum, rather than here on the ubuntuzilla support forum.

or, if you're using 32bit ubuntu, try using the ubuntuzilla repository instead. :)

---

### Post by gmargo on 2010-02-05
Oh, darn, it is firefox-stable; They were both mentioned over in the firefox-3.6 thread, so I somehow confused them and thought they were the same.  Sorry about that.

---

