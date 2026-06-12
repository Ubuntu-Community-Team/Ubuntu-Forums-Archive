---
title: "rkhunter on clean, new unstalled systems"
date: 2011-04-06
forum: Security
---

### Post by Soul-Sing on 2011-04-06
[SIZE="4"]results on xubuntu Natty beta. No additional sofware installed.
only ufw enabled.[/SIZE]


[COLOR="Red"]warnings[/COLOR]: 
          /usr/bin/mail
          /usr/bin/bsd/mail-x
          checking /dev for susp. files
          checking hidden files and direct.
          /usr/bin/lwp-request

Would be nice to compare other results/outcomes from "clean", fresh installed ubuntu systems. You could post the results here in this thread.

[SIZE="4"]We could also scan a system with some basic/common configurations.[/SIZE]
- java
- multimedia codecs/ubuntu-restricted-extras
- flash

---

### Post by unspawn on 2011-04-06
> **leoquant said:**
> warnings: 
          /usr/bin/mail
          /usr/bin/bsd/mail-x
          checking /dev for susp. files
          checking hidden files and direct.
          /usr/bin/lwp-request

If you check the full message for each warning / FP from rkhunter.log instead you could try and match them with the white-listing comments in rkhunter.conf as they are populated with common examples. Also the bottom of doc/rkhunter-1.3.8/FAQ has a few "recipes" you could run on your log (but who really reads READMEs and FAQs these days...). Anyway, if these result in white-listing examples and scriptlets specific to your distribution feel free to offer them for inclusion in the Ubuntu package.

---

### Post by ianc1 on 2011-05-03
Hi leoquant.  Just done exactly the same - a fresh Natty install, enabled ufw and installed rkhunter.

Following ```
rkhunter --update rkhunter -c
```  I get /usr/bin mail and /usr/bin/bsd-mailx listed as not been in the rkhunter.dat file.

As far as I am aware rkhunter itself installed bsd-mailx the "parent" package of /usr/bin/bsd-mailx.

Oddly```
dpkg -S /usr/bin/mail
``` doesn't reveal a "parent" package for /usr/bin/mail.

---

### Post by Kokomo Joe on 2011-05-03
:KSHello, In reply to rkhunter-new install, and mail.  The mail we register with somehow glues itself to the install as did happen to me when burning a fedora live disk and then installing it.  
:KSMy i.d. was on the raw image.  The live-cd was burned on a windows machine.
I hope this is the topic of changes from original downloads that had been checked for signatures. 
:KSLater burning a different live cd on a linux machine the 'clean image' started, but the the email i.d. addon with reference to my machine i.d. and a little more was copied to the image also.
:KSMy x- window is most likely being recorded now to be a continuous image recreation of every bit.  I really don't know when I am on a virtual screen or not,
but that's the way it is for users.
:KSGoogle and other browsers and systems activate screen recorders at various times "to help give you a better experience"  Glad to be here with you concerned people.
Thank You,
k.j.

---

### Post by Soul-Sing on 2011-05-04
> **ianc1 said:**
> Hi leoquant.  Just done exactly the same - a fresh Natty install, enabled ufw and installed rkhunter.

Following ```
rkhunter --update rkhunter -c
```  I get /usr/bin mail and /usr/bin/bsd-mailx listed as not been in the rkhunter.dat file.

As far as I am aware rkhunter itself installed bsd-mailx the "parent" package of /usr/bin/bsd-mailx.

Oddly```
dpkg -S /usr/bin/mail
``` doesn't reveal a "parent" package for /usr/bin/mail.

: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=459621](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=459621)
thats what i found on this matter.
afaik rkhunter comes with exim-4.

---

