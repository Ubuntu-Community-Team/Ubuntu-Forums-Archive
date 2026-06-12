---
title: "Google Chrome to use gtk3"
date: 2017-03-20
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2017-03-20
It appears that Google Chrome will [soon use gtk3]("https://chromium.googlesource.com/chromium/src/+/master/docs/linux_gtk_theme_integration.md") for theming its UI. At least that's what it is with Version 59.0.3043.0 (Official Build) dev (64-bit). As with all other applications, I was happier with the old gtk2!

Anyway, here's what my UI with google-chrome-unstable looks like after a little tinkering:

---

### Post by uNoubu8a on 2017-03-20
Would be nice if Chrome's window matched the rest of the systems.

---

### Post by speedwell68 on 2017-03-20
> **work-work said:**
> Would be nice if Chrome's window matched the rest of the systems.

I totally agree.

---

### Post by Perfect Storm on 2017-03-20
> **work-work said:**
> Would be nice if Chrome's window matched the rest of the systems.

+1
Now we only need steam making a gtk3 client.

---

### Post by vasa1 on 2017-03-20
For me, the important thing is to reduce the amount of full white on the screen. I've settled for #808080. If I go darker than that, there's some sort of automatic trigger that makes the tab text and the bookmarks text as well as the forward/back, reload, and home icons be drawn bright white.

---

### Post by vasa1 on 2017-03-22
OMG! Ubuntu has a piece on the topic: [http://www.omgubuntu.co.uk/2017/03/google-chrome-chromium-gtk3-by-default](http://www.omgubuntu.co.uk/2017/03/google-chrome-chromium-gtk3-by-default)

Version 59.0.3047.0 (Official Build) dev (64-bit) seems to have reverted to a gtk2 appearance. [The log]("https://chromium.googlesource.com/chromium/src/+log/59.0.3043.0..59.0.3047.0?pretty=fuller&n=10000") has this:```
Revert of Linux UI: Switch to the Gtk3 theme (patchset #3 id:180001 of https://codereview.chromium.org/2670623002/ )

Reason for revert:
Reverting to fix component builds on systems with Mir.
Will reland (probably later today) once https://codereview.chromium.org/2756543002/ lands

```

---

### Post by 6975 on 2017-03-24
hope it won't mess like installing gtk3-engines-xfce and mess whole gtk2 applications.

---

### Post by vasa1 on 2017-03-29
Version 59.0.3053.3 [is back on gtk3]("https://chromium.googlesource.com/chromium/src/+/0ff8b19608421be5fa5b53e90c097e4992723b90").

---

### Post by vasa1 on 2017-03-31
> **vasa1 said:**
> For me, the important thing is to reduce the amount of full white on the screen. I've settled for #808080. If I go darker than that, there's some sort of automatic trigger that makes the tab text and the bookmarks text as well as the forward/back, reload, and home icons be drawn bright white.

But that may be fixed in a future dev version according to [Text in tabs, bookmarks bar and back/forward, reload, home icons change from black to white depending on background color]("https://bugs.chromium.org/p/chromium/issues/detail?id=706448").

---

### Post by vasa1 on 2017-04-07
With Version 59.0.3063.4 (Official Build) dev:

---

### Post by vasa1 on 2017-06-05
[http://www.omgubuntu.co.uk/2017/06/chromium-59-uses-gtk3-on-ubuntu](http://www.omgubuntu.co.uk/2017/06/chromium-59-uses-gtk3-on-ubuntu)

---

