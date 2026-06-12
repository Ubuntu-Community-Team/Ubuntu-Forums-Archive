---
title: "Firefox 26 in Trusty"
date: 2014-01-23
forum: Ubuntu Development Version
---

### Post by WebDrake on 2014-01-23
Firefox 26 has been out for a while -- is there a reason why it hasn't made it to the main trusty repository yet?

---

### Post by QIII on 2014-01-23
There may be bigger fish to fry at the moment.  ;)

---

### Post by buzzingrobot on 2014-01-23
See this: [http://ubuntuforums.org/showthread.php?t=2198150&highlight=firefox](http://ubuntuforums.org/showthread.php?t=2198150&highlight=firefox).

And this: [http://ubuntuforums.org/showthread.php?t=2196001&highlight=firefox](http://ubuntuforums.org/showthread.php?t=2196001&highlight=firefox)

AKA, first things first.

(It is reasonable to assume, too, that anyone equipped to deal with a development release more than two months from scheduled release can cope with doing a manual install of Firefox off the Mozilla site.)

---

### Post by mc4man on 2014-01-23
Just lilke a previous thread here, same deal. It's in proposed, if you must have now then get it
(actually already up to 27, myself stopped noticing the diff in FF's every time you look a new version

> apt-cache policy firefox
firefox:
  Installed: 25.0+build3-0ubuntu0.13.10.1
  Candidate: 27.0~b6+build1-0ubuntu1
blah, blah

---

### Post by QDR06VV9 on 2014-01-23
[QUOTE=mc4man;12908588]Just lilke a previous thread here, same deal. It's in proposed, if you must have now then get it
(actually already up to 27, [COLOR=#008080]_myself stopped noticing the diff in FF's every time you look a new version_[[/COLOR]/QUOTE]

+1;)

---

### Post by WebDrake on 2014-01-25
Thanks for the info everyone :-)  FWIW I did search the forums first, but "firefox 26 trusty" resulted in lots of posts that were nothing to do with firefox 26, and didn't get me anywhere near the posts linked to here ... :-(

---

### Post by Cavsfan on 2014-01-25
I enabled proposed to get the beta grub files and thought I disabled it afterwards but I ended up picking up Firefox 27 that way.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy firefox
firefox:
  Installed: 27.0~b6+build1-0ubuntu1
  Candidate: 27.0~b6+build1-0ubuntu1
  Version table:
 *** 27.0~b6+build1-0ubuntu1 0
        100 /var/lib/dpkg/status
     25.0+build3-0ubuntu0.13.10.1 0
        500 http://mirrors.advancedhosters.com/ubuntu/ trusty/main amd64 Packages

```

I thought it was weird because at one point the update wanted to remove ubuntu-desktop and I knew that wasn't right so I checked the proposed in SPM and sure enough it was enabled.

Well at least I got Firefox 27 out of the deal. :)

---

