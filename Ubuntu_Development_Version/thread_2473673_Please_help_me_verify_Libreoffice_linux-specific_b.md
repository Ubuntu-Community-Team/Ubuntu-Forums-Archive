---
title: "Please help me verify Libreoffice linux-specific bug"
date: 2022-04-10
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2022-04-10
Hello,

I reported a libreoffice bug on the document foundation bugzilla, [here]("https://bugs.documentfoundation.org/show_bug.cgi?id=148433"), regarding keyboard input delay in pragraphs which contain both rtl charcters and numeric characters. This seem to happen only on linux.
I'll be grateful if someone can verify the bug (a testcase is attached to the bug) and confirm it on libreoffice bugzilla.

---

### Post by osse7 on 2022-04-10
I'm using LO on Mate (jammy) with proposed repo enabled. It is an Impish upgrade; and does not hit your issue.
So maybe start with a bleachbit cleanup, use the tweaks app to switch languages a few times; and glance at 'journalctl -b' to try grabbing some helpul error/warning about LO/keyboard.
Note that i have had lot of 'keysyms' garbage logged before getting the latest libx11 upgrades.
As the Mate session is probably using xorg instead of wayland (but im not fully sure about that), you can check logging with xorg to narrow down the problem origin.

If you finally find something specific to Ubuntu, then report on Launchpad too.

---

### Post by Wise Ferret on 2022-04-10
> **osse7 said:**
> maybe start with a bleachbit cleanup, use the tweaks app to switch languages a few times; and glance at 'journalctl -b' to try grabbing some helpul error/warning about LO/keyboard.
I used bleachbit, but to no avail - the problem persists.
I'm not sure what you mean about switching language using the "tweaks" application (gnome-tweaks does not do that). The problem occurs regardless of the gnome session language (Hebrew/English) and regardless of the current input language (Hebrew/English).
journalctl -b and gedit /var/log/Xorg.0.log indicate no errors.

This seems now like a specific issue of libreoffice in gnome. Can someone with the default ubuntu installed check it out?

---

### Post by Wise Ferret on 2022-04-10
Wait, I did find something in the Xorg log!
```
[   865.856] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 32ms, your system is too slow
[  3226.007] (EE) client bug: timer event3 debounce: scheduled expiry is in the past (-90ms), your system is too slow
[  3274.957] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 21ms, your system is too slow
[  3286.328] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 21ms, your system is too slow
[  3392.073] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 33ms, your system is too slow
[  3618.939] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 24ms, your system is too slow
[  3618.939] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: WARNING: log rate limit exceeded (5 msgs per 60min). Discarding future messages.
[  6531.198] (EE) client bug: timer event3 debounce: scheduled expiry is in the past (-58ms), your system is too slow
[  6531.198] (EE) client bug: timer event3 debounce short: scheduled expiry is in the past (-71ms), your system is too slow
[  6924.439] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 36ms, your system is too slow
[  7090.677] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 33ms, your system is too slow
[  7292.991] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 23ms, your system is too slow
[  7654.182] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 22ms, your system is too slow
[  7767.279] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: client bug: event processing lagging behind by 24ms, your system is too slow
[  7767.279] (EE) event6  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: WARNING: log rate limit exceeded (5 msgs per 60min). Discarding future messages.
```
The keyboard is indeed made by Microsoft, but this is clearly not a hardware issue (the keyboard does not know about the content of the current paragraph in libreoffice, and the delay occurs only when the paragraph contains both numeric and rtl characters). Any idea where to go from here?

---

