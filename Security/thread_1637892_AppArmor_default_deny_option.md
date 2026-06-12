---
title: "AppArmor default deny option"
date: 2010-12-05
forum: Security
---

### Post by ramujinius on 2010-12-05
Hi All

Could some one let me know, how to enable apparmor such that newly installed programs access to system resource, is denied. In general, for the programs which does not have any profiles, i want apparmor to block its access to the system. Is it possible to do that with any command? As far as  i read the manuals i think for each application we need to create a profile for apparmor to act on it.

---

### Post by bodhi.zazen on 2010-12-05
> **ramujinius said:**
> Hi All

Could some one let me know, how to enable apparmor such that newly installed programs access to system resource, is denied. In general, for the programs which does not have any profiles, i want apparmor to block its access to the system. Is it possible to do that with any command? As far as  i read the manuals i think for each application we need to create a profile for apparmor to act on it.

No, that is the downside of apparmor , you need to write a profile for each application.

In general you only need a profile for applications which access the internet. If you need more then that, look at "jailbash"

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

