---
title: "Grabit issues."
date: 2009-05-11
forum: Wine
---

### Post by acacia09 on 2009-05-11
Hi all,
I have searched and I have found a few people with the same issues but no solution.

I am trying to run grabit but it just shows in the system tray minimized and it wont maximize. I have tried running on a virtual desktop but with no luck.

Does anyone have any suggestions?

Many Thanks

---

### Post by fsando on 2009-07-01
I've found a workaround: I force some errors on GrabIt which tricks it (or Wine?) to show up.
I change some settings in ```
~/.wine/user.reg 
```
There are some sections relating to GrabIt, a large section starting with:
```
[Software\\Shemes\\GrabIt]
```
I usually comment out (';') the last lines in this section (all to do with window size - though I don't think that matters - only that it introduces some errors that gets it past a bug)

Then I start the program. It will temporarily have forgotten all its known servers so I just start up, accept a new server - close down and start up again - this time all is back to normal.

It seems that when the 'Default Server' is set to a non existing server or to a server explicitly named 'Default Server' it agrees to show up.

---

