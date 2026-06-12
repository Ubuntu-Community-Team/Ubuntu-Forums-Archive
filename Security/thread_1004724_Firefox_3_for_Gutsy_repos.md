---
title: "Firefox 3 for Gutsy repos?"
date: 2008-12-07
forum: Security
---

### Post by barboachtraner on 2008-12-07
Mozilla is going to discontinue updates for Firefox 2 after v2.0.0.19 is released this month, so I'd like to be able to switch to Firefox 3 by the next time a security fix comes around. The problem is, I'm using Gutsy Gibbon and the Firefox 3 package in the official repos is still an alpha version. Are there any plans to update this, or will I have to download directly from Mozilla or do a distribution upgrade?

---

### Post by Dr Small on 2008-12-07
Downloading the tarball from the mozilla website is the easiest thing to do. Move it /opt and untar it. Now you can either relink things to use the executable in /opt/firefox or you can move /usr/bin/firefox to something like firefox2 and link /usr/bin/firefox to the one in /opt/firefox

---

