---
title: "Problem with Locales on a fresh install"
date: 2006-09-11
forum: Server Platforms
---

### Post by simone.brunozzi on 2006-09-11
Hi there,
I got the following problem in an ubuntu 6.06 LTS fresh install:

```

root@politika:~# aptitude install man
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_ZW.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
root@politika:~#


```

Any suggestion?

---

### Post by simone.brunozzi on 2006-09-11
Well, partially solved, with these commands:

tzconfig
export LC_CTYPE=C
export LC_MESSAGES=C
export LC_ALL=C
dpkg-reconfigure locales

But, when I log in again, same problem!!!!!

How can I fix it permanently?

Thanks

---

### Post by Iarwain ben-adar on 2006-09-14
Hi,
same error here
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "nl_BE:nl:en_GB:en",
        LC_ALL = "nl_BE.UTF-8",
        LC_MESSAGES = "nl_BE.UTF-8",
        LC_CTYPE = "nl_BE.UTF-8",
        LANG = "nl_BE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Kan LC_ALL niet instellen op standaard locale: Onbekend bestand of map

```

Anyone knows something?


Iarwain

---

