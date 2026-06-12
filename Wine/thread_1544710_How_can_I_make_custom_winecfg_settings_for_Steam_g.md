---
title: "How can I make custom winecfg settings for Steam games?"
date: 2010-08-02
forum: Wine
---

### Post by Vunutus on 2010-08-02
I know how to do it under normal circumstances using the "add application" menu or whatever it's called to add the EXE for my game then setting my virtual desktop options, but it doesn't work with games launched by steam.

Specifically I'm trying to make TF2 run in a virtual desktop since it doesn't handle minimizing/changing workspaces very well. The process name for it is hl2.exe, so I added it to my app list in winecfg and then set my desktop settings but it apparently doesn't "match" the program and execute my settings. I assume this has something to do with the way programs are launched through steam. EVE Online, for example, works fine with my virtual desktop settings outside steam but if I add it to steam and then execute it via my Steam library my settings are ignored.

How can I fix this?

Also, speaking of TF2, as a secondary question to this topic, how can I fix the fonts for the TF2 menu? This is most noticeable on the server list, all the names are very hard to read but fonts in-game are perfect. I don't have any problems other than this (actually it runs on max settings perfectly despite the appDB entry saying that wouldn't work), so it would be nice to perfect my experience.

EDIT: I forgot to mention that I do have the microsoft fonts installed and have run the usual winetricks font fix

---

### Post by cogadh on 2010-08-02
Have you tried creating a separate "bottle" (a separate Wine prefix) for your Steam games? That way you can make a virtual desktop the default setting for that bottle and you don't have to worry about individual app settings.

---

