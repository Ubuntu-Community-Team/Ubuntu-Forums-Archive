---
title: "Weird apparmor status output, concerning Firefox"
date: 2010-11-04
forum: Security
---

### Post by MechaMechanism on 2010-11-04
I tried out the apparmor for Firefox in enforce mode and did not care for it.  Instead I put it in complain mode.  Running sudo apparmor_status gives some weird output.  I would like to know if this is normal.

You will find the attached txt file contains the complete output.  Below is a snippet.

386 profiles are in complain mode.
   /usr/bin/xchat
   /usr/bin/xchat//null-10c
   /usr/bin/xchat//null-10d
   /usr/lib/firefox-3.6.12/firefox-*bin
   /usr/lib/firefox-3.6.12/firefox-*bin//firefox_java
   /usr/lib/firefox-3.6.12/firefox-*bin//firefox_openjdk
   /usr/lib/firefox-3.6.12/firefox-*bin//null-10e
   /usr/lib/firefox-3.6.12/firefox-*bin//null-10e//null-10f
   /usr/lib/firefox-3.6.12/firefox-*bin//null-10e//null-110
   /usr/lib/firefox-3.6.12/firefox-*bin//null-10e//null-111
   /usr/lib/firefox-3.6.12/firefox-*bin//null-10e//null-112
   /usr/lib/firefox-3.6.12/firefox-*bin//null-10e//null-112//null-113
   /usr/lib/firefox-3.6.12/firefox-*bin//null-10e//null-112//null-113//null-114
   /usr/lib/firefox-3.6.12/firefox-*bin//null-10e//null-112//null-113//null-114//null-115

---

