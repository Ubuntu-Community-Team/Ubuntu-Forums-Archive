---
title: "Minor bug: custom shortcuts and change of its accelerators (LogOutIn necessary)"
date: 2015-03-08
forum: Ubuntu Development Version
---

### Post by zika on 2015-03-08
LightDM
for sake of being totally precise: gnome-flashback-metacity (but I think, not sure, will check soon as free time appears)
If I change CustomShortcutAccelerator it will not operate (whole ShortCut per se) before I do LogOutIn procedure.
Not a big deal, I do not change that often but just to check if I'm alone before/if making a bug report.
Update&#8321;: Found culprit. See last message down. Since it shifts focus completely I'm marking this thread as „solved“.

---

### Post by ventrical on 2015-03-09
> **zika said:**
> LightDM
for sake of being totally precise: gnome-flashback-metacity (but I think, not sure, will check soon as free time appears)
If I change CustomShortcutAccelerator it will not operate (whole ShortCut per se) before I do LogOutIn procedure.
Not a big deal, I do not change that often but just to check if I'm alone before/if making a bug report.

Could you elaborate so I can try to emulate.

What do I do because I cannot find CustomShortcutAccelerator. Do I have to download a file?

Regards

---

### Post by zika on 2015-03-09
[COLOR=#000000][I]CustomShortcutAccelerator=SystemSettigs>Keyboard>Shortcuts>Custom_Shortcuts>Click_on_Shortcut>Choose_to_change_accelerator...
[/I][/COLOR]

---

### Post by mc4man on 2015-03-09
This started in 13.10 & appears to still be true in gnome-fallback sessions. 
Orig. bug here that was never fixed, just went away in an ubuntu session when they moved to unity-settings-daemon in, I guess,  14.04
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1243532](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1243532)

---

### Post by zika on 2015-03-11
Just to note: It seems that [fcitx]("http://ubuntuforums.org/showthread.php?t=2268776") broke custom shortcuts in Gnome-Flashback-Metacity. They work OK in Cimpiz flavor. I'll see if mere log(out/in) did the trick instead of changing WM.
Update&#8321;: Yes, it just did need LogOut/In... ;)
Update&#8322;: Found culprit. Somehow keyboard (even though it shows latin) goes into cyrillic mode. That is why shortcuts do not work. I will investigate more but I think (my) focus (in regards with this &#8222;problem&#8220;) shifts now.

---

