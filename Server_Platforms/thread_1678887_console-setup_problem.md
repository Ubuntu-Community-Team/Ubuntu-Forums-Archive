---
title: "console-setup problem"
date: 2011-01-31
forum: Server Platforms
---

### Post by bjh6 on 2011-01-31
dpkg-reconfigure console-setup appears to have corrupted the boot console keyboard. 

When I installed Ubuntu LTS 10.4 Server the keyboard was correctly set to UK Keyboard and all keys functioned as expected.

After running 

dpkg-reconfigure console-setup 

the # key generates <delete-last character> and @ generates <delete-line>. shift-3 which should be pound sterling produces nothing. This only applies on the console of the server itself (tty1-tty6), before login; after login all is ok.

console-setup is:

Keyboard Model: Generic 105-key (INtl) PC   (but others show the same symptoms)
Origin of the keyboard: United Kingdom
Keyboard layout: United Kingdom
AltGR Replacement: Right Alt
Compose key: No compose key
Encoding: UTF-8
Charater set to support: Latin1 and Latin5 - western Europe and Turkic languages
Font: VGA
Font size: 16
Virtual consoles: /dev/tty[1-6]

cached.kmap seems to have to correct settings (keycode 43 U+0023, keycode 40 U+0027 U+0040)

All other keys seem to be ok, esp double quote which is different on UK keyboards

Please advise on where the keyboard mapping information for the boot console keyboard is held, or other ways in which this could be fixed (short of re-installing and never using console-setup!). Is this a Ubuntu bug?

Thanks

---

