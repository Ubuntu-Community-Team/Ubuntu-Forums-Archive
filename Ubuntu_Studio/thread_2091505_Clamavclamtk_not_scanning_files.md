---
title: "Clamav/clamtk not scanning files"
date: 2012-12-05
forum: Ubuntu Studio
---

### Post by Flaggmann on 2012-12-05
I just installed clamav, clamtk, clamd, and freshclam. I updated using freshclam using terminal and all indications are successful update.

Running Recursive Full File system scan manually from clamtk menu results in 0 files scanned. It appears to start as normal, then indicates the total number of signatures, then immediately says scan complete 0 files scanned. 

This is two different boxes with ubuntustudio 12.04 with all updates completed.

ps -A doesn't show any clamavd running but clamtk and freshclam (started as freshclam -c4) are showing as active processes.

Kind of pointless to install if it doesn't scan anything; am I doing a setup wrongs somewhere?

Have installed it on 3 other ubuntustudio boxes the same way as well as another flavor of linux and they all work and scan fine.

Thanks for any tips in advance

---

### Post by CrocoDuck on 2012-12-05
Hi! Open the ClamTk GUI and go to the preferences tab (Ctrl+P should bring you there). Make sure you have set at least one option under the first tab (something like "scanning preferences"). Set the options in this tab according to your needing.

---

### Post by Flaggmann on 2012-12-05
> **CrocoDuck said:**
> Hi! Open the ClamTk GUI and go to the preferences tab (Ctrl+P should bring you there). Make sure you have set at least one option under the first tab (something like "scanning preferences"). Set the options in this tab according to your needing.
_***[SOLVED] ***_  Thnx that did it

---

