---
title: "Firefox problems"
date: 2005-10-03
forum: The Cafe
---

### Post by Joenco on 2005-10-03
Hello,

I have problems with firefox crashing.
I'm a ubuntu newbie so have some questions.

I would like to completely remove firefox with all it's associated files and plugins as I suspect the plugins.

How can I do this so I can reinstall firefox fresh.

Thank you,

---

### Post by phen on 2005-10-03
hi joenco!

you can remove the plugins from within firefox. go Extras -> Extensions. afterwards
open a terminal (right click on the desktop) and type

sudo apt-get remove firefox

or

sudo apt-get purge firefox


now you can try to install another browser. 

please post further questions in the beginner forum. it is the right place for problems like yours!

---

### Post by Jussi Kukkonen on 2005-10-03
phen, plugins are not the same thing as extensions, and cannot be removed from the Extensions dialog. They can be disabled from Preferences/Downloads/Plugins. I have no idea how to remove a plugin completely.

The easiest way to remove Firefox and all related settings is to find firefox in Synaptic and select "Mark for Complete Removal" -- beware though, if I recall correctly you'll loose your bookmarks and such.

---

### Post by blueturtl on 2005-10-03
This thread should have been posted under Desktop support, but let me point out that your plugins are stored either

locally under your username
/home/username/.mozilla/firefox/plugins
/home/username/.mozilla/firefox/components

or globally
/usr/lib/mozilla-firefox/plugins
/usr/lib/mozilla-firefox/components

As for Firefox crashing it seems to be a very common problem. I've switched over to Mozilla (which does occationally crash too, but a lot less often). You should try Opera since it's now totally free.

---

### Post by Joenco on 2005-10-03
Sorry for posting in wrong forum.
Thanks for helping.

Joenco

---

