---
title: "My Meerkat just died!"
date: 2010-08-04
forum: System76 Support
---

### Post by Collin White on 2010-08-04
Well, maybe not died per se. I was doing some browsing with Chrome, had Thunderbird open in the background when everything stopped responding, so I did Ctrl-Prnt Scrn REISUB to reboot.  Now instead of booting to 10.04 as it had prior, I get a screen saying:

No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3 -1ubunut11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _


I typed help but none of the commands seem to be especially useful to me. I've been running Ubuntu since Dapper and have never had anything like this occur. Is it hardware related? How do I sort this out?

Any help would be greatly appreciated.

---

### Post by jml on 2010-08-05
Try booting a live CD.  Either an Ubuntu disc, or one of the more specialized live CD's designed as system rescue distros.  Here is a link to a review of three popular distros:

[http://www.linux.com/archive/feed/45883](http://www.linux.com/archive/feed/45883)

Once its running, you can root around your system to see what is and is not working.  Or, if you already have your data backed up, if an Ubuntu live CD works, you can simply do a clean install.  Good luck.

Joe

---

### Post by Collin White on 2010-08-05
Thanks.  I booted my live CD, which after a couple reboots prompted me to fix some mounting issue with /tmp which seemed to have fixed the problem.

---

### Post by jml on 2010-08-06
Glad to hear it worked.

---

