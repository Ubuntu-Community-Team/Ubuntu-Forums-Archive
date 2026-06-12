---
title: "PHP / Locale"
date: 2010-11-27
forum: Server Platforms
---

### Post by dignus on 2010-11-27
Hi all,

Got a pretty straightforward machine here. Installed some extra locale's, including nl_NL (the one I need):


```
root@dev-web:~# locale -a
C
en_AG
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
nl_AW
nl_BE.utf8
nl_NL.utf8
POSIX

```

To be sure, I ran a locale-gen:

```
root@dev-web:~# locale-gen 
Generating locales...
  en_AG.UTF-8... up-to-date
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
  nl_AW.UTF-8... up-to-date
  nl_BE.UTF-8... up-to-date
  nl_NL.UTF-8... up-to-date
Generation complete.

```

So far so good. From the command line I can change the locale and verify that it's working:

```
root@dev-web:~# export LC_ALL=nl_NL.UTF-8
root@dev-web:~# date +%A
zaterdag
root@dev-web:~# export LC_ALL=en_US.UTF-8
root@dev-web:~# date +%A
Saturday

```

All look  good, right? However.. if I want to use another locale in PHP with setlocale, I don't get the right locale:

```
root@dev-web:~# cat date.php 
<?
setlocale(LC_ALL, 'nl_NL.utf8');
echo date('l');
?>
root@dev-web:~# php date.php 
Saturday
root@dev-web:~# 

```

Any hints? Am I missing something completely obvious here?

---

### Post by wojox on 2010-11-27
Try

[PHP]setlocale(LC_ALL, 'nl_NL');[/PHP]

---

