---
title: "Block Firefox 75 update if you can"
date: 2020-04-09
forum: Ubuntu, Linux and OS Chat
---

### Post by John Nagle on 2020-04-09
Warning: Firefox 75 is automatically installing a forced update on Ubuntu. 

Right click menu are broken on Ubuntu in Firefox 75. Reported to Firefox at link below.

Stop the update if you can. Firefox now has "downgrade protection"; if you install an older version, you lose all your settings. So there's no going back.

[https://bugzilla.mozilla.org/show_bug.cgi?id=1628917](https://bugzilla.mozilla.org/show_bug.cgi?id=1628917)

---

### Post by DuckHook on 2020-04-09
:confused:
I have FF 75 and the right click menu works just fine.

---

### Post by TheFu on 2020-04-09
Forced update?  Not seeing that here.  Can you please expand about that?  Do you have automatic updates enabled in Ubuntu? Or did Mozilla do an update outside the OS process?   Which sort of package?  Deb, snap, Appimage, flatpak?

```
$ dpkg -l|grep firefox
ii  firefox       74.0.1+build1-0ubuntu0.16.04.1     amd64    Safe and easy web browser from Mozilla

```

v74 here.

---

### Post by yetimon_64 on 2020-04-10
> **DuckHook said:**
> ...I have FF 75 and the right click menu works just fine.
Same here. I saw the update for it go through earlier today and all is working fine regarding context menus in firefox.

---

### Post by ajgreeny on 2020-04-10
Is your firefox running from a downloaded archive rather than the normal .deb package installation?
Opening an older version of FF that way will auto update by default but it's  certainly not the normal way to run FF. 

The only other possibility as suggested above, is that you have enabled unattended upgrades, something I  disable always after OS install, preferring to know what's happening.

However my FF 75 is running as it should.

---

### Post by The Cog on 2020-04-10
The bugzilla link in the original post links to a bug report that the poster himself wrote. And that report has a later post stating that the problem has disappeared. So I think this may have been a one-off oddity.

---

### Post by mikewhatever on 2020-04-10
+1
No problems with FF75, and no forced updates either.

---

### Post by ajgreeny on 2020-04-10
Did you perhaps have an instance of FF open during the update and not close and reopen afterwards?

Doing that can cause many problems in FF; it **MUST** be closed and reopened to work properly.

---

### Post by sdsurfer on 2020-04-10
^^ Heh, my FF always freezes or refuses to open new tabs if it's open when it updates, forcing the restart. I think there's something missing there or broken, I seem to recall a page that used to open that said something like "We have just one thing to do . . . " and at least informed you you need to restart.

At any rate, also 75.0 and working fine.

---

