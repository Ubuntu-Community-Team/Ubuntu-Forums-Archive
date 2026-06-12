---
title: "Rkhunter failed update"
date: 2014-04-09
forum: Security
---

### Post by cogset on 2014-04-09
I'm getting this message in rkhunter.log when running rkhunter --update

```
Checking file i18n versions                       [ Update failed ]
[10:55:07] Warning: Download of 'i18n.ver' failed: Unable to determine the latest version number.
```

Is there any way to manually update rkhunter files?

---

### Post by 23dornot23d on 2014-04-10
Just so you know I did the check today and mine worked ok

But I only just installed it on this new build today .......

> 
# rkhunter --update
[ Rootkit Hunter version 1.4.0 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ No update ]
  Checking file backdoorports.dat                            [ No update ]
  Checking file suspscan.dat                                 [ No update ]
  Checking file i18n/cn                                      [ No update ]
  Checking file i18n/de                                      [ Updated ]
  Checking file i18n/en                                      [ Updated ]
  Checking file i18n/tr                                      [ Updated ]
  Checking file i18n/tr.utf8                                 [ Updated ]
  Checking file i18n/zh                                      [ No update ]
  Checking file i18n/zh.utf8                                 [ No update ]



---

### Post by cogset on 2014-04-11
Yes,I've noticed that  the first update after a fresh install actually works,but apart from that,I've checked for updates also on another LTS distro (Mint) and I'm getting the very same error

```
Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ No update ]
  Checking file backdoorports.dat                            [ No update ]
  Checking file suspscan.dat                                 [ No update ]
  Checking file i18n versions                                [ Update failed ]
```

If there actually were no updates at all,I think I should not see that last line.

---

### Post by gnanet on 2014-04-30
cat /etc/issue.net
Debian GNU/Linux 6.0

rkhunter --versioncheck
[ Rootkit Hunter version 1.3.6 ]

Checking rkhunter version...
  This version  : 1.3.6
  Latest version: 1.4.2
  Update available

rkhunter --update
[ Rootkit Hunter version 1.3.6 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ No update ]
  Checking file backdoorports.dat                            [ No update ]
  Checking file suspscan.dat                                 [ No update ]
  Checking file i18n versions                                [ Update failed ]


The problem is simply, that rkhunter project removed the old version's directories from sourceforge (the URL was clearly to see in the rkhunter.log ) for this item:
[http://rkhunter.sourceforge.net/1.3/i18n/1.3.6/i18n.ver](http://rkhunter.sourceforge.net/1.3/i18n/1.3.6/i18n.ver)

Refer to this thread:
[http://ubuntuforums.org/showthread.php?t=2180153](http://ubuntuforums.org/showthread.php?t=2180153)
You will have to upgrade rkhunter somehow to at least 1.4.0

---

### Post by cogset on 2014-05-02
Thank you,that explains what is going on:having looked at the thread you've linked,clearly the only way to keep rkhunter up to date on LTS releases is to install the new package yourself from the tarball,something that did not occur to me.

---

