---
title: "Firefox (snap) fails to load on kernel 6.1"
date: 2023-03-20
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2023-03-20
Ubuntu 23.04 (development). I was pleased when an update brought in kernel 6.1 but now I find that Firefox (which is a snap packaged app) fails to load. Firefox works fine on kernel 5.19. I understand the 23.04 is supposed to have kernel 6.2 by release day. Let us hope that this problem is sorted out by then.

Regards

---

### Post by TenPlus1 on 2023-03-21
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by guiverc on 2023-03-21
There was an issue with `firefox` a couple of days ago, but for the *life of me* I can't recall any specifics... I remember it impacting one PC, I was *confused* so logged out my *primary *PC, logged in again & ensured the *firefox snap* was updated.. and sure enough it failed to operate on my *primary* box too.  I wasn't alone in having it, as I recall discussions on IRC (-devel channels), the issue was discussed & soon the cause was found, and the following day things were back to normal for me.

This likely isn't your issue  (*it can't have been yesterday for me not to remember specifics I'd hope*), but I access this site & many others only via `firefox` and as my *primary* box runs *lunar*, I'd expect to notice issues pretty soon.

I've been using `firefox` on *lunar* most of today without issue, and I `apt full-upgrade`three times per day, though my normal behavior has me suspend my box most nights (*rebooting often only weekly*) so where kernel changes, or logout/login are required before changes take effect, it may take a few days for me to notice some changes..

(I'm mostly using Lubuntu/LXQt, though in recent ~week due to an `openbox` bug [*now resolved in PPA :P which will get rolled out hopefully soon!*] I was using Xubuntu/Xfce and Ubuntu-Desktop/GNOME  (*they didn't crash if you took a window full screen and...*), but I can't see how the desktop will matter)

We'll have 6.2 before the kernel freeze I bet.. so we'll get it well before release days (*upgrades on 6.1 have stopped, roll out of 6.2 was delayed due to an issue I forget..*)

----  Added later:

Open a terminal & start `firefox` at terminal... I recall doing that to get detail on why `firefox` wasn't starting.. It was the same error message for however many had the issue.

If you provide the paste of the error you get, it may trigger my *bad memory..*  (*I've got a mild headache currently, so I'm not trying to remember anything* *too*).  It'll give me something to search in my *hexchat* logs for the discussion, if you're getting the same issue I (& others) were..

---

### Post by corradoventu on 2023-03-22
Firefox does not start using his .desktop file but start ok with 'snap nun firefox'

---

### Post by corradoventu on 2023-03-22
same problem with kernel 6.2 just arrived

---

### Post by corradoventu on 2023-03-23
Firefox does not start at all using his .desktop file, starts with a black screen the 1st time is started from terminal with 'firefox' or 'snap run firefox' and start fine the 2nd time is started from terminal with 'firefox' or 'snap run firefox'
start ok from terminal with "MOZ_ENABLE_WAYLAND=1 snap run firefox"

edit: see bug [https://bugzilla.mozilla.org/show_bug.cgi?id=1822374](https://bugzilla.mozilla.org/show_bug.cgi?id=1822374)

Edit: ALL snaps fail to start [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2011806](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2011806)

---

