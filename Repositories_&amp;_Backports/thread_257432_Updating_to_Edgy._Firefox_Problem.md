---
title: "Updating to Edgy. Firefox Problem"
date: 2006-09-14
forum: Repositories &amp; Backports
---

### Post by damogran on 2006-09-14
Hi,

i just wanted to update my dapper to edgy, but failed at some mozilla package. Now an "apt-get install -f" give me this. 

```
root@baboon:~# apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox gtk2-engines mozilla-firefox-locale-en-gb
Suggested packages:
  latex-xft-fonts libthai0
The following packages will be REMOVED:
  gtk2-engines-clearlooks
The following NEW packages will be installed:
  gtk2-engines
The following packages will be upgraded:
  firefox mozilla-firefox-locale-en-gb
2 upgraded, 1 newly installed, 1 to remove and 685 not upgraded.
3 not fully installed or removed.
Need to get 0B/9481kB of archives.
After unpacking 5927kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: regarding .../mozilla-firefox-locale-en-gb_1.99+2.0b1ubuntu1-2_all.deb containing mozilla-firefox-locale-en-gb:
 mozilla-firefox-locale-en-gb breaks firefox (<< 1.99)
  firefox (version 1.5.dfsg+1.5.0.5-0ubuntu6.06.1) is installed.
dpkg: error processing /var/cache/apt/archives/mozilla-firefox-locale-en-gb_1.99+2.0b1ubuntu1-2_all.deb (--unpack):
 installing mozilla-firefox-locale-en-gb would break firefox, and
 deconfiguration is not permitted (--auto-deconfigure might help)
dpkg: regarding .../firefox_1.99+2.0b1+dfsg-1ubuntu3_i386.deb containing firefox:
 mozilla-firefox-locale-en-gb conflicts with firefox (>> 1.5.z999)
  firefox (version 1.99+2.0b1+dfsg-1ubuntu3) is to be installed.
dpkg: error processing /var/cache/apt/archives/firefox_1.99+2.0b1+dfsg-1ubuntu3_i386.deb (--unpack):
 conflicting packages - not installing firefox
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox-locale-en-gb_1.99+2.0b1ubuntu1-2_all.deb
 /var/cache/apt/archives/firefox_1.99+2.0b1+dfsg-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm bloody new to ubuntu, so maybe someone can help me out here. ^^

cheers
damo

---

### Post by Uncle Spellbinder on 2006-09-14
> **damogran said:**
> I'm bloody new to ubuntu, so maybe someone can help me out here.

Just curious, not trying to be mean or anything here. 

But you say you're "bloody new to Ubuntu", and you're attempting to upgrade to an "experimental" OS (Edgy)? It's not released yet and is basically for testing only.

---

### Post by damogran on 2006-09-15
uhm yes, new to ubuntu but linuxuser for years. 
but thanks for your great and helpful reply.

i solved the problem by removing some packages and using the aptitude problem resolver. great tool.

---

### Post by ~LoKe on 2006-09-17
Any more details on this?  I'm having the same problem.

---

