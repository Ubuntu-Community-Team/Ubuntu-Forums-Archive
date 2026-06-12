---
title: "jack broken after 11.10 -&gt; 12.04 upgrade"
date: 2012-07-09
forum: Ubuntu Studio
---

### Post by hamnstar on 2012-07-09
Everything worked fine in 11.10.  Upgrading to 12.04 has introduced errors in starting jack??

Initially, I was using QJackctl and found that it was using /usr/bin/jackdmp for the server. This was in the setup>options page. I was getting an error along the lines of 'cannot start server err - file does not exist'.  changing the setting to just 'jackd' or 'jackdmp' alleviated this error message, but no audio was working.  QJackctl did however recognize my audio devices in the connections window.

 A few reboots later, QJackctl just hangs (no GUI, just a gray box with a title bar) and trying to start jackd manually fails:

trdenton@dingler:~$ jackd -dalsa -r48000 -p128 -n3 -D -Chw:0,0 -Phw:0,0
jackdmp 1.9.8
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
`default' server already active
Failed to open server


this seems odd, so i do:
trdenton@dingler:~$ ps aux | grep jack
trdenton  1958  0.1  6.2 326068 91504 ?        SLsl 17:24   0:32 /usr/bin/jackdbus auto
trdenton  2619  0.0  0.2  96032  3796 ?        Ssl  18:33   0:01 /usr/bin/jackdbus auto
trdenton  4155  0.0  0.0   9392   884 pts/3    S+   23:09   0:00 grep --color=auto jack


trying to kill the jackdbus processes does not do anything - the command looks like it succeeded, but when i do another ps listing, the jackdbus entries are still there with the same PIDs.  doing this via sudo gets the same result.


HELP!!!  I just want to make music!! :(

---

### Post by hamnstar on 2012-07-09
Solved.  After another reboot it let QJackCTL work.  The issue was that the interface had defaulted to the usb di box I had hooked up, which doesnt seem to be supported.  Will open a new thread for that.  Setting the interface (setup page) to <default> let it work again.

---

