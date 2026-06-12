---
title: "Deactivate a locale."
date: 2009-02-16
forum: Server Platforms
---

### Post by dmizer on 2009-02-16
I need to deactivate an active locale on my WWW server via CLI, and I can't figure out how to do it. I want to remove ja_JP.eucjp but keep ja_JP.utf8.

As far as I can see, ja_JP.eucjp should not be active on my system, but it is indeed quite active.

```
$ ls /var/lib/locales/supported.d
en  ja  local
```
```
$ cat /var/lib/locales/supported.d/en
en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_NG UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8
```
```
$ cat /var/lib/locales/supported.d/ja
ja_JP.UTF-8 UTF-8
```
```
$ cat /var/lib/locales/supported.d/local
en_US.UTF-8 UTF-8
ja_JP.UTF-8 UTF-8
```
```
$ cat /etc/default/locale
LANG="en_US.UTF-8"
```

When I run sudo dpkg-reconfigure locales, I get this:
```
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  ja_JP.UTF-8... up-to-date
Generation complete.
```
But when I list my locales, the ja_JP.eucjp STILL exists:
```
C
POSIX
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
ja_JP
ja_JP.eucjp
ja_JP.utf8
```

How do I get rid of that stubborn ja_JP.eucjp? It's causing my dates to display incorrectly in php.

Edit:
I even installed "localepurge", and deselected ja_JP.eucjp, but it still remains.

---

### Post by dmizer on 2009-02-16
Finally solved this by running this command:
```
sudo dpkg-reconfigure -plow locales
```

---

### Post by dmizer on 2009-02-17
This is completely baffeling to me.

Despite the fact that ja_JP.eucjp is not even enabled on my server, strftime still reports dates in eucjp instead of utf8. How is that even possible?

---

