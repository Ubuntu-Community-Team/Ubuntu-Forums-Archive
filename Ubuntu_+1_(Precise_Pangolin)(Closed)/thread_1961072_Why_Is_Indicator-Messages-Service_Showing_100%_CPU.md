---
title: "Why Is Indicator-Messages-Service Showing 100% CPU Use?"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by buzzingrobot on 2012-04-18
Why is the Indicator-Messages-Service showing 100% CPU usage in top? (96% in System Monitor).

This is an i7-2600k machine on Beta2.  I'm current with the updates. I've seen this from the start with Beta2, though.   Right now, Firefox is open, Terminal is open, and System Monitor is open.

[EDIT:  OK, immediately after a reboot, it shows 0% usage.  After I launch Liferea, it jumps above 100%. Quit Liferea and it stays there. Although, Liferea will post an updated unread feeds number on its icon in the Launcher after I quite it, so something is still running. Also, on occasion, I see a segmentation fault, blaming colord, a few seconds after launching Liferea. I see old reports on Liferea and CPU use in Launchpad but nothing recent.]

[FIXED: Liferea has an option in Preferences to "Show a status window in the notification area (system tray)."  This appears in the Launcher, not the System Tray, and shows the unread update even when Liferea is closed.  But, in any case, enabling it seems to be what's pegging the CPU meter. ]

---

