---
title: "Where are Gnome Shell launcher settings stored?"
date: 2013-03-20
forum: Ubuntu Development Version
---

### Post by sgage on 2013-03-20
I used to be able, after a fresh install, to deja-dup restore my settings and all would be exactly as I liked. For a couple of months now, it seems that a number of settings are not restored. Even if I copy back all of my .files from a grsync copy, no joy.

Let's narrow it down: where are the Gnome Shell launcher settings stored?

---

### Post by sgage on 2013-03-21
> **sgage said:**
> I used to be able, after a fresh install, to deja-dup restore my settings and all would be exactly as I liked. For a couple of months now, it seems that a number of settings are not restored. Even if I copy back all of my .files from a grsync copy, no joy.

Let's narrow it down: where are the Gnome Shell launcher settings stored?

After some testing with a test account, I think I've figured it out. The settings are in ~/.config/dconf, and though it's easy to make a good backup copy of it somewhere, it seems to be resistant to being overwritten in an active session. If you actually delete the dconf directory during a session, it seems to get re-written. If you delete it from a different account, things revert to the default settings. You can copy a dconf directory into an account from another account as well, and its settings will be in effect.

Apparently, this is a change in Raring, because a simple deja-dup restore would restore all the gnome-shell desktop settings just fine. Maybe they moved the location of the settings or something. I'm just glad to have this sorted out - it was driving me nuts...

---

### Post by dino99 on 2013-03-21
if you does not care about your custom settings, in case of a borked system, you can delete that .config, it will be rebuilt with the default system settings on the next boot. (also true for .gnome2, .local & .gconf)

---

### Post by mc4man on 2013-03-21
It's definitely changed at some point in raring - in the past I always used to setup, then backup ~/.config/dconf/user to somewhere else.
Simply replacing user with the backup & logging out/in would then use the back upped copy.
This no longer occurs, the settings in place when logging out are restored on re-login.

As mentioned if done from another install/user then the new one will be used. From a single user/install perspective I believe it can still be done. (at least as seen here.
In that case I first place the backup copy of user in ~/.cache/dconf/ (creating if not there), then open ~/.config/dconf/,  delete user & promptly log out

---

