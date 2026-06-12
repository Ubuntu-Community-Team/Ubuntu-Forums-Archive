---
title: "Install nightly builds"
date: 2008-07-14
forum: Ubuntuzilla
---

### Post by Sergiodf on 2008-07-14
Seamonkey is approaching a new major release (2.0).

I would like to test pre-alpha releases, and i wonder if Ubuntuzilla can help me installing a nightly.

According to [this thread]("http://ubuntuforums.org/showthread.php?t=627136&highlight=nightly"), it is not possible in "current" (2007-December) version of Ubuntuzilla. There were any changes since then?

---

### Post by nanotube on 2008-07-14
> **Sergiodf said:**
> Seamonkey is approaching a new major release (2.0).

I would like to test pre-alpha releases, and i wonder if Ubuntuzilla can help me installing a nightly.

According to [this thread]("http://ubuntuforums.org/showthread.php?t=627136&highlight=nightly"), it is not possible in "current" (2007-December) version of Ubuntuzilla. There were any changes since then?

no, ubuntuzilla is still only about installing releases.

---

### Post by ernstblaauw on 2009-03-12
Did anything change the latest months? I would really love to install 3.2a1pre ([http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)) using Ubuntuzilla. Or is there any 'hack' to hard code the download location?

---

### Post by nanotube on 2009-03-13
Hi

well, it shouldn't be /too/ hard to change stuff around for the alphas or nightly builds or whatnot. You're welcome to play around with the code and see where you get with it. 

it's not quite as easy as just changing something in one place, though. your best bet may be to add an extra commandline option, which would allow you to specify full path to the download, and when it's present, you'd bypass all the current logic which builds the download url.

---

