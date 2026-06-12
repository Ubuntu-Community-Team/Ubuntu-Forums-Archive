---
title: "Epiphany using Webkit?"
date: 2008-04-29
forum: The Cafe
---

### Post by sports fan Matt on 2008-04-29
Wasnt there talk awhile back about Epiphany using Webkit?  Im not sure and How often does Epiphany release a new version?

---

### Post by spupy on 2008-04-29
Epiphany with WebKit backend is not officially released, afaik. However, you can compile it. I have right here on Gentoo, but it took me 3 days to find the correct versions. It works with Epiphany 2.22 and the latest WebKit sources from their svn repository: [http://webkit.org/](http://webkit.org/)

This is the guide:
[http://live.gnome.org/Epiphany/WebKit](http://live.gnome.org/Epiphany/WebKit)

It scores 100/100 on the acid3 test: [http://acid3.acidtests.org/](http://acid3.acidtests.org/)
Firefox 3 scores 62, Epiphany with Gecko fails at 52. It also uses gtk widgets like Firefox3 does. It does render sites well, but sites made specially for sucky IE does not look OK all the time.

It is an interesting experiment, but I would not recommend it. It does run very good, still there are some problems:
- can't open links in new tabs
- no cookies
- some Epiphany extensions don't work.

---

### Post by 23meg on 2008-04-29
The GNOME 2.24 roadmap mentions Epiphany switching to WebKit.

[http://live.gnome.org/RoadMap](http://live.gnome.org/RoadMap)

---

### Post by aamukahvi on 2008-04-29
Epiphany in Gnome 2.24 will have only the Webkit backend if everything goes to plan.

[http://blogs.gnome.org/xan/2008/04/06/epiphany-%E2%99%A5-webkit/](http://blogs.gnome.org/xan/2008/04/06/epiphany-%E2%99%A5-webkit/)

And:
[http://live.gnome.org/RoadMap](http://live.gnome.org/RoadMap)

---

### Post by Mateo on 2008-04-29
If you want to see what it's like, just download Midori (it's in the Hardy repos).  It uses Webkit.  Epiphany will be the same, just with more/better features.

It's going to be an interesting transition.  I'll stay with Epiphany/gecko until the release at least an adblocker extension for the webkit version.

---

