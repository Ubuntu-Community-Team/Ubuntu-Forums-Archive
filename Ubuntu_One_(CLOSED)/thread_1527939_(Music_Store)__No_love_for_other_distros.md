---
title: "(Music Store)  No love for other distros?"
date: 2010-07-09
forum: Ubuntu One (CLOSED)
---

### Post by Darseex on 2010-07-09
Edit:  Fixed, but I'll leave the rest unedited just for kicks.  Apparently after installing all those other packages by hand, my rhythmbox needed updating (or maybe it did before and I didn't notice, but I do recall updating it very recently).  That fixed the gtk-widgets problem; don't ask me how.

Not that I'm anti-Ubuntu, but it's not a distro I spend a lot of time on.  I've installed it on other peoples' PCs, but I tend to prefer a more minimal setup.

One thing I anticipated about 10.04, though, was the Music Store.  I sent an email to Stuart Langridge a while ago about this, and he responded that the music store was basically just a Rhythmbox plugin, so why wouldn't it work?

I'm guessing his vision was a bit different than some others at Canonical though, seeing as how the plugin is anything but simple to get running under, say, the newer Crunchbang (what I'm on, essentially Debian Squeeze).  It's not available in the repos - I wouldn't necessarily expect it to be - and going straight to the source means downloading an extra 14 packages by hand (not including stuff that those packages also download during their respective installations) and the long process of checking which package depends on which and installing them in the proper order.

After all of this, I'm finally able to install the plugin... though naturally, it doesn't work.  Rhythmbox's GUI isn't too helpful here, but a terminal shows me this:

```
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/umusicstore/__init__.py", line 27, in <module>
    from ubuntuone.gtkwidgets import MusicStore as U1MusicStore
ImportError: No module named gtkwidgets

(rhythmbox:11209): Rhythmbox-WARNING **: Could not load plugin umusicstore


(rhythmbox:11209): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Ubuntu One Music Store'
```


So, I guess I have a few questions here.  First, why no plugins for other distros at all?  I can live without the actual Ubuntu One integration if that's the problem, and I bet most others can too if the posts on this forum are any indication.

After that, of course, is the all-important followup:  Are there plugins for non-Ubuntu distros that I'm just not looking in the right places for?  If so, let me know and I'm a happy guy.

Also, assuming nothing can/will be done about the first question and the second question comes up negative, does anyone know how I can fix this gtk-widget problem?  I guess I should mention that I'm running Openbox as my WM, though I'm not sure what the problem is if I've got all the libraries installed.

---

### Post by kyleabaker on 2010-07-12
I think you can count on generic distro plugins in the future, but the plugin for Ubuntu is still very new and isn't even completed yet (still has several bugs and probably a few missing intended features/abilities).

Once it has time to mature in Ubuntu, they may open it up to other distros and make it easier to install....but don't hold me to that. ;) It would be free and easy Ubuntu advertising, so theres no reason why they shouldn't do this.

---

