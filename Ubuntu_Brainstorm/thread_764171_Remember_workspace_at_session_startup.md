---
title: "Remember workspace at session startup"
date: 2008-04-23
forum: Ubuntu Brainstorm
---

### Post by Golem XIV on 2008-04-23
I have a bunch of stuff autoloading at login like Evolution, BOINC Manager, etc.  I usually keep this on the last (4th) workspace.

However, at login, these apps all load into the 1st workspace so I have to manually move them to where I want them to be.

It would be nice if the session manager could "remember" or let the user define into which workspace the selected GUI app will load at startup.  IIRC my experiences with Kubuntu Gutsy, KDE already does this.

---

### Post by smartboyathome on 2008-04-23
Check to see if there is a way to build this into Metacity. Ubuntu doesn't make software, it just packages it. If all else fails, file a bug with GNOME.

---

### Post by qamelian on 2008-04-23
Like smartboyathome says, this is a function that would be handled by the window manager and is not something currently supported by Metacity. At the moment, your only real options would be to use an application like Devil's Pie to fine tune the placement of your app windows on startup or use a different window manager to replace Metacity. Sawfish, which was the Gnome window manager prior to the switch to Metacity did support this feature but was lacking in other areas.

---

