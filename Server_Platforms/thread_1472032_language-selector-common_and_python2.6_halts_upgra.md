---
title: "language-selector-common and python2.6 halts upgrade"
date: 2010-05-04
forum: Server Platforms
---

### Post by threadhead on 2010-05-04
Started an upgrade to Lucid today and all went fine until it tried to configure language-selector-common:

```

Setting up language-selector-common (0.5.7) ...
pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/FontConfig.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/ImSwitch.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/LangCache.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/LanguageSelector.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/__init__.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/xkb.py not found.
pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/FontConfig.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/ImSwitch.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/LangCache.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/LanguageSelector.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/__init__.py not found.
   dpkg: /usr/lib/python2.6/dist-packages/LanguageSelector/xkb.py not found.
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
   Errors were encountered while processing:
 language-selector-common
 ubuntu-standard
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried everything I could find and nothing is letting me past this error.

```

#did not work:
sudo apt-get clean
sudo apt-get autoclean
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade

```

All the above pretty much crap out with the same error.

Any other ideas to try?

---

### Post by conorgriffin on 2011-04-19
I got the same errors, did you fix this?

---

### Post by Klau3 on 2011-04-19
Same problem here.

Can I uninstall it?

Launchpad bugreport:
[https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766429](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766429)

---

### Post by gzader on 2011-04-19
This is the actual bug report. The one above is a dupe.  [https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766412](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/766412)  it looks like the issue is identified and that a potential patch is in place.

---

### Post by MusicTR on 2011-04-19
There is a patch but i have no idea how to apply it. Can you explain in plain English please? I appreciate if you could help.
Thanks..

---

### Post by step5 on 2011-04-19
You have to go to the terminal and do the following steps:

```
gksu gedit /var/lib/dpkg/info/language-selector-common.postinst
```

(if you do not have gedit installed use any other editor instead)

search for the line:
 kill $(pgrep -U root '^ls-dbus-backend$') 2>/dev/null

and change it to
 kill $(pgrep -U root '^ls-dbus-backend$') 2>/dev/null || true

save and close

then run

```
sudo apt-get install -f upgrade
```

should work...

---

### Post by Richy on 2011-04-19
It worked with plain 
```
sudo apt-get install -f
```
instead of 

```
sudo apt-get install -f upgrade 
```

Thank you!

---

### Post by MusicTR on 2011-04-19
Thanks alot!

---

