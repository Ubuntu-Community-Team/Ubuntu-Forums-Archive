---
title: "export XDG_CONFIG_DIRS=::::::; firefox; causes Segmentation fault"
date: 2014-03-07
forum: Ubuntu Development Version
---

### Post by gmoore777 on 2014-03-07
My installation of 64-bit Lubuntu TrustyTahr Beta-1 (with current updates)
cannot run `firefox` without getting:

    Segmentation fault (core dumped).

After a bunch of divide and conquer, I got it narrowed down to the 
XDG_CONFIG_DIRS variable that is set in the environment.

After a bunch of divide and conquer, I got it narrowed down to the
number of directories listed in that variable. 
The values of the directories do not matter. 
(I'm leaving them blank so as to not distract anyone)
If there are exactly 7 directories listed, firefox crashes.
Less than 7, or more than 7, firefox starts up.

These work:
export XDG_CONFIG_DIRS=:::::::; firefox;    # 7 colons
export XDG_CONFIG_DIRS=:::::; firefox;      # 5 colons

This does not:
export XDG_CONFIG_DIRS=::::::; firefox;     # 6 colons

I can reproduce this on 
  64-bit Ubuntu  TrustyTahr 14.04 LiveDVD burned with current build of 2014-03-02

I can NOT reproduce this on "32-bit" Lubuntu TrustyTahr 14.04 beta-1 with updates.
I can NOT reproduce this on 64-bit "PrecisePangolin" 12.04.4.

Can anyone add some insight on who or what product/library/file is causing the  problem
so that I can log a bug in the appropriate product forum?

Can anyone else confirm this exact issue on "any" 64-bit TrustyTahr distribution so
I know it's not my specific machine/setup?

Thank you.

(side note: when running the liveDVD, XDG_CONFIG_DIRS only has 3 directories
listed at the time. So firefox works. 
But after installation, etc., XDG_CONFIG_DIRS
has 7 directories listed, the magic number. So firefox fails.
The value of my XDG_CONFIG_DIRS after installation and logged in as me is:
 /etc/xdg/lubuntu:/etc/xdg:/etc/xdg/lubuntu:/etc/xdg:/etc/xdg/xdg-Lubuntu:/usr/share/upstart/xdg:/etc/xdg
)

---

### Post by gmoore777 on 2014-03-14
I logged this bug describing the above at:
[https://bugzilla.mozilla.org/show_bug.cgi?id=981066](https://bugzilla.mozilla.org/show_bug.cgi?id=981066)
Another similar one exists at:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1278062](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1278062)

---

### Post by Toz on 2014-03-14
*Moved to the **Ubuntu+1** forum.*

---

