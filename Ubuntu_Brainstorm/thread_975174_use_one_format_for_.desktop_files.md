---
title: "use *one* format for .desktop files"
date: 2008-11-08
forum: Ubuntu Brainstorm
---

### Post by pelle.k on 2008-11-08
I was reading up on this, since i felt a bit irritated on the inconsistencies of application names in the gnome menu system.

Now, there are two sets of guidelines on how to name applications;
The GNOME HIG
Freedesktop.org

My idea is to choose *one* standard. Not two (as it is now).
Basically, in a desktop entry, there are
```
name=
genericname=
comment=
```

The GNOME HIG says to name the application (name) as name + genericname. (that's why it is "firefox web browser" instead of just firefox)
```
name=firefox web browser
genericname=web browser
comment=
```

The freedesktop says to name the application and genericname each, and let the menu system add the two should it be neccesary (like the kde menu does it > konqueror - web bowser).
```
name=konqueror
genericname=web browser
comment=
```

I don't particulary care what spec is followed (even though i prefer the freedesktop one), as long as it's done. By default, all applications installed from ubuntu-desktop follow the GNOME HIG, but if you install, say gqview or gftp, those follow the Freedesktop standard - and that looks odd in the menus.

So this is my idea.
Wouldn't it be great if one could choose what should be displayed as well (like in kde), say only name, "firefox", or genericname, "web browser", or both "firefox - web browser". But that is an gnome issue, so i'll just stop here!

---

### Post by smartboyathome on 2008-11-08
If you want this to happen, then you'll have to try to get GNOME and KDE to work together and use one guideline. I think that both use the basic freedesktop.org layout, just different ways of displaying it (like E17 displays Firefox as "Firefox (Web Browser)"). I think that even GNOME uses the same standard now though.

---

