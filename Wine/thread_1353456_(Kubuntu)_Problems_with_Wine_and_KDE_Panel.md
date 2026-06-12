---
title: "(Kubuntu) Problems with Wine and KDE Panel"
date: 2009-12-12
forum: Wine
---

### Post by richterlevania3 on 2009-12-12
Hi folks,

I have a problem with any app using Wine in fullscreen mode and the Plasma Panel with the setting "Windows go below" : when I play, e.g. WoW, everything works fine, but if I minimize WoW and focus another window, when I maximize WoW again the Panel will keep showing up at the bottom of the screen. This only happens if I focus another window, if I just minimize to see something and then maximize again, it will do fine.

If I use the Plasma Panel setting "Always visible", the Panel will show up everytime, no matter what I do.

I've tried everything I know: played with the Desktop and Kwin settings, deactivate Desktop Effects, special window behaviour, everything. Nothing works.

Someone has a clue?

Thanks in advance.

PS: I use Kwin Desktop Effects, no Compiz, KDE 4.2.4, Karmic.

---

### Post by hikaricore on 2009-12-12
Disable desktop effects while playing and see if this resolves the issue.
There is a plasmoid in the repos for 1 click enabling and disabling.

From what I understand, kde SHOULD automatically disable effects when something starts fullscreen but it doesn't seem to do this on Kubuntu.

---

