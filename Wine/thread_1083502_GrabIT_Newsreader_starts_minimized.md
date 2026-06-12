---
title: "GrabIT Newsreader starts minimized"
date: 2009-03-01
forum: Wine
---

### Post by spliffeh on 2009-03-01
I installed a newsreader (grabit) and it worked fine. Then I moved it onto my 2nd desktop cube, I use compiz.

A while later it disappeared and I could find it, or alt-tab to it. But it was still running fine in the background, i can see it on the process list, completing downloads, and I see it on this little tiny 'application switcher' (I forget what it's called) icon i have on my top bar. When I right click it there my options are to Minimize/Restore, pause downloads, exit grabit, etc. But Minimize/restore does not bring it back.

**The question.... **how can I reset the window settings on this app I am launching in Wine? The app works fine but I think wine or gnome or compiz is hiding it somewhere and wont let it come back out.

---

### Post by fsando on 2009-06-24
bump

---

### Post by stderr on 2009-09-19
I'm aware this is *rather late*, but for anyone else searching for this issue and bumping into this thread, this is a workaround (as opposed to an actual solution):

Uninstall then reinstall Grabit (and from then on, don't minimise the window!)

NB: It's probably possible to edit the config values in the registry ( "wine regedit", under HKEY_CURRENT_USER\Software\Schemes\GrabIt ) to correct this issue, but I haven't yet found any to alter which works. It may be worth exporting that tree when you're experiencing the problem, reinstalling, start and close GrabIt again, and then compare your exported values to the current values. E.g., MinimizeToTray looked promising, but that was set to 0 when I was having the problem - doesn't seem like much to "correct" there. 

I haven't tried the above myself because I've just set everything up again and can't be bothered with the p***ing around :) Please post back if you bump into a simpler solution than reinstalling. Cheers.

edit: TBH, you could probably save yourself a tiny bit of the hassle of reinstalling by just wiping the whole hive from HKEY_CURRENT_USER\Software\Schemes (i.e. delete the "Schemes" entry). I think it should be automatically regenerated; but, of course, you would still lose all your settings.

---

### Post by zainaman on 2009-12-27
Change
HKEY_CURRENT_USER\Software\Shemes\Grabit\WindowState

to 1 and start Grabit again.

---

