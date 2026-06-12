---
title: "mono-1.2.2 and deps for edgy here"
date: 2006-12-07
forum: Repositories &amp; Backports
---

### Post by viraptor on 2006-12-07
I've recompiled mono-1.2.2 in edgy from feisty repositories. So far monodoc and xsp packages are outdated (1.2.1, and 1.1.18 ), so there's no point in publishing them. I'll try to update, when they're ready.

Get it, if you're interested:
[http://kni.prz.rzeszow.pl/~viraptor/mono](http://kni.prz.rzeszow.pl/~viraptor/mono)

source packages: mono, cli-common, libgdiplus

---

### Post by viraptor on 2006-12-21
Updated:
mono 1.2.2.1 and deps: cli-common, libgdiplus, sqlite
Place: [http://kni.prz.rzeszow.pl/~viraptor/mono/](http://kni.prz.rzeszow.pl/~viraptor/mono/)

---

### Post by cime on 2006-12-30
Which packages I have to install? Why nobody post this debs in some repository.

---

### Post by hscottyh on 2007-01-18
Thanks for the packages!!

If your looking for a fairly easy way to install these, here is how I did it.

I used the 'downloadthemall' Firefox plugin and very easily got them all at once. You can get this plugin here: [https://addons.mozilla.org/firefox/201/](https://addons.mozilla.org/firefox/201/)

Then from a terminal went to the folder and executed:
sudo dpkg -i *.deb

It got errors installing three of the packages, probably due to dependency problems, but they were unimportant to me. I removed them and ran again and all is well.

Followup:
I had to run this to get updates to work again:
 sudo apt-get install -f

---

### Post by shomati_sen on 2007-01-28
Thanks to viraptor for the packages and hscottyh for the tip. I have beagle-0.2.15.1 running on Edgy with this.

---

### Post by ladenedge on 2007-02-05
Finding this thread just saved me a ton of time - thanks a lot!

---

