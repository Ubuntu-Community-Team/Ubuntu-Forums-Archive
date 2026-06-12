---
title: "Strange sticky keys issue"
date: 2012-12-06
forum: System76 Support
---

### Post by kingbanditjing on 2012-12-06
I've been having a weird issue with the keyboard and/or certain keys on my new Gazelle laptop.  This exhibits in the following fashion:

In a browser, I press ctrl-fn-down to switch tabs. Rather than just switching to one tab per one down key click, it quickly flashes through many tabs and only stops when I let go of all the keys.  I then only need to press the ctrl key to make the browser switch through all the tabs.  Pressing a bunch of other keys makes it stop.

This doesn't happen every time, only some of the time. But it also happens for application switching with alt-tab and other key combinations.

This laptop is less than a week old.  Nothing has been spilled on the keyboard.

Thanks for the help!

---

### Post by isantop on 2012-12-07
> **kingbanditjing said:**
> I've been having a weird issue with the keyboard and/or certain keys on my new Gazelle laptop.  This exhibits in the following fashion:

In a browser, I press ctrl-fn-down to switch tabs. Rather than just switching to one tab per one down key click, it quickly flashes through many tabs and only stops when I let go of all the keys.  I then only need to press the ctrl key to make the browser switch through all the tabs.  Pressing a bunch of other keys makes it stop.

This doesn't happen every time, only some of the time. But it also happens for application switching with alt-tab and other key combinations.

This laptop is less than a week old.  Nothing has been spilled on the keyboard.

Thanks for the help!

Does the key physically stick down, or does it pop up afterwards?

---

### Post by kingbanditjing on 2012-12-10
It doesn't physically stick, only effectively does a pagedown continue to be triggered, regardless of the application switched to.

Further encounters with this bug looks like it's mainly (or only) with the page down functionality.

---

### Post by kingbanditjing on 2012-12-11
After messing with this more it's actually easily replicable.  One out of every three or four presses of ctrl-fn-up or ctrl-fn-down will result in the page up or page down key remaining.

This exhibits in two ways, further presses of ctrl-fn by themselves will trigger the next tab functionality in browsers and terminals (the issue exhibits across applications).  Also, the tab brought to focus will be paged up/down immediately with no additional keys pressed.

Let me know any other questions, thanks!

**Update**: Just pressing fn-up or fn-down will occasionally cause the page up/down to stick.  The up/down keys do not stick by themselves however, only when in conjunction with the fn key.

---

### Post by isantop on 2012-12-12
Does it happen if you run Ubuntu from a Live Disk? If so, then you likely have a BIOS or hardware problem, and we'd need to bring it in.

If not, then a reinstall would have it fixed in less than 20 minutes.

---

