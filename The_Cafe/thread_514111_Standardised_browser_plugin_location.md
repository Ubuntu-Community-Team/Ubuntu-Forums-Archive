---
title: "Standardised browser plugin location"
date: 2007-07-31
forum: The Cafe
---

### Post by ajmas on 2007-07-31
Installing browser plugins on linux seems to be a little problematic, in the sense you install the player and then are told to manually copy files X and link file Y. While this is fine for the seasoned user, this doesn't fit the user-friendly label. 

On MacOS X two standard locations are defined:
   /Library/Internet Plugins
   ~/Library/Internet Plugins

Any program that have supporting plugins put them in there and they are automatically available to any web browser running on the system. From what I can tell there is currently no equivalent, so you the user is left doing some footwork.

Keeping within Linux conventions, is there any equivalent location that could be defined, that is not dependent on any specific browser?

---

### Post by stmiller on 2007-07-31
Linux software that uses plugins is already set up to look in many locations for plugins. Open up Konqueror and go to it's preferences>plugins to see what I mean.

Generally, you will find plugins in /usr/lib/firefox/plugins/

---

