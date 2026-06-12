---
title: "wxMaxima with GTK2 in Hoary"
date: 2005-08-20
forum: The Cafe
---

### Post by NeTo on 2005-08-20
I have recently built wxMaxima 0.6.1 with GTK2 box in my Hoary setup. I have mailed the wxMaxima author regarding the package (as I can't and/or don't plan to host it), but I couldn't resist posting a Screenshot of it.

I have to made also a backport of the breezy version of wxWidgets 2.6.0 to hoary, as it is required for GTK2 support in wxMaxima. At I first though on offering both packages (wxMaxima and wxWidgets) on the backports forums, but I noticed that libs aren't supported because compatibility issues.

If someone is interested in hosting or taking a look at package I will gladly mail it.

---

### Post by ow50 on 2005-08-21
[QUOTE=NeTo]I have to made also a backport of the breezy version of wxWidgets 2.6.0 to hoary, as it is required for GTK2 support in wxMaxima.[/QUOTE]
Is wx 2.6.0 really required? A while ago I built wxMaxima against Hoary's wx 2.5.3 and it seems to work fine.

Here's a link to the package I made:
[wxmaxima_0.6.1-2~ots_i386.deb](http://koti.mbnet.fi/~ots/linux/hoary/wxmaxima_0.6.1-2~ots_i386.deb)

---

### Post by NeTo on 2005-08-21
[QUOTE=ow50]Is wx 2.6.0 really required? A while ago I built wxMaxima against Hoary's wx 2.5.3 and it seems to work fine.

Here's a link to the package I made:
[wxmaxima_0.6.1-2~ots_i386.deb](http://koti.mbnet.fi/~ots/linux/hoary/wxmaxima_0.6.1-2~ots_i386.deb)[/QUOTE]
 Funny, I didn't try the obvious. Since the [WxMaxima download page](http://wxmaxima.sourceforge.net/download.html) stated that wxWidgets 2.6.0 was required, I didn't dare to try anything else :p

---

