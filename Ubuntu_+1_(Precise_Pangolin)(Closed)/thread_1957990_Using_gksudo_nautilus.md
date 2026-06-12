---
title: "Using gksudo nautilus"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by creosote on 2012-04-13
I'm using using a clean install of Precise fully updated with Gnome shell.

If i do gksudo nautilus, the desktop background changes from what i have selected to the ubuntu default wallpaper and the file manager is then handling drawing of the desktop. I know it's handling the desktop because i have the symptoms described in this thread:
[http://ubuntuforums.org/showthread.php?t=1947969](http://ubuntuforums.org/showthread.php?t=1947969)
and am able to put files on the desktop.

I have to log out and back in to set things right.

This doesn't happen if i were to use gksduo gedit.

Anybody know of anything i can do to use gksduo nautilus and have it leave my wallpaper and desktop handling the way i have it set for my user?

Thanks

---

### Post by mc4man on 2012-04-13
However you are starting your root nautilus try this as command

```
gksudo 'nautilus --no-desktop'
```

---

### Post by creosote on 2012-04-13
> **mc4man said:**
> However you are starting your root nautilus try this as command

```
gksudo 'nautilus --no-desktop'
```

Beautiful! That takes care of it.

Thanks very much.

I thought i had an option to mark this as solved but don't see it now.

---

### Post by dino99 on 2012-04-13
> **creosote said:**
> Beautiful! That takes care of it.

Thanks very much.

I thought i had an option to mark this as solved but don't see it now.

Click on "Tread Tools" on top of this thread (red)

---

