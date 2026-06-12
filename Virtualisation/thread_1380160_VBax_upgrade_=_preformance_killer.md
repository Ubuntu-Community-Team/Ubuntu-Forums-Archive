---
title: "VBax upgrade = preformance killer?"
date: 2010-01-13
forum: Virtualisation
---

### Post by Warthaug on 2010-01-13
I just upgraded from virtualbox 3.0.? to the newest 3.1.  To do so I uninstalled 3.0 and then installed 3.1.  All my settings and guest was maintained, but I seem to be suffering a HUGE drop in performance compared to 3.0.  Even the vbox control panel (launcher?) is slow; from clicking on the settings button to loading the settings panel took ~5secs; it used to be instant.

Same goes for booting the guest - from 20-30sec to well over a minute, and the guest is unbelievably sluggish compared to before (it was very snappy in vbox 3.0).  Shutdown is also slow - 2min and counting as of now...still not shut down.

The details:
Host: Ubuntu 9.10, 64bit.  Intel 2-core processor, 2gig RAM, dell XPS M1330 laptop

Guest: WinXP, 32bit.  1gig RAM assigned, VT-x enabled, 12meg video RAM (no acceleration or remote display).

I'm running the non-open source version of VBox.

We're now at ~4min of shutdown, still waiting...

Any advice?  Maybe I should de-upgrade...

Bryan

EDIT: Forgot to add that vbox is also seriously slowing down the host OS as well.

---

### Post by Warthaug on 2010-01-14
So the problem seems to have resolved itself.  Ubuntu did an update last night that required a reboot - and since then VBox seems to be running as it did before the upgrade.

Bryan

---

