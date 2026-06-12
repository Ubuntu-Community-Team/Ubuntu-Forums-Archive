---
title: "Will the latest ghostscript break anything?"
date: 2006-03-24
forum: Ubuntu Backports
---

### Post by archis on 2006-03-24
I thought this might be the right forum to ask the following: 

Will a parallel install of the latest ghostscript break anything in Breezy (CUPS, foomatic) ?

Breezy uses 8.01 and Dapper will apparently use 8.15 -- meanwhile the AFPL-licensed version [is now at 8.53 and the GPLed version at 8.50]("http://www.cs.wisc.edu/~ghost/") (Dec 31 05). There's been a bunch of technical improvements - not just bugfixes - to Ghostscript since 8.01 and 8.15 such as support for PDF v1.4 and 1.5. DTP apps like Scribus [are making use of these improvements]("http://docs.scribus.net/index.php?lang=en&page=toolbox7") and ask their users to upgrade.


AFAIK, ghostscript is a rather delicate part of the infrastructure and messing with it could break all sorts of things. So perhaps the backport team can tell me whether a parallel install -- perhaps using checkinstall -- in /usr/local or similar would actually break anything on Ubuntu Breezy ?

---

### Post by petervk on 2006-03-24
I know I've previously upgraded my ghostscript in Breezy to whatever the current version was then and I didn't have any problems. Can't vouch for the current version at all.

A checkinstall deb shouldn't really mess anything up that much and its easy to downgrade. (in synaptic -> force version) I'd give it a try, and just remove it if it doesn't work. I don't think it's as integrated/crucial as you think. Just install it over the existing one and try it out.

Its up to you though.

---

