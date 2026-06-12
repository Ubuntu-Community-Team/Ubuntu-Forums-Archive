---
title: "Software &amp; Updates dialogue box"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by mayagrafix on 2014-03-30
After updating from 13.10 Saucy to 14.04 Trusty Tahr, a few software repositories are left unchecked. Should I delete them? (the ones that are for Saucy) or should I enable those that seem pertinent?

[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/Softwareupdate-other_tab_zpsb0c85c15.png[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/Softwareupdate-other_tab_zpsb0c85c15.png.html)

---

### Post by bapoumba on 2014-03-30
Moved to Ubuntu +1.

Do not enable them as is, some are for raring, others for saucy. Check if each one of them have a trusty repo, then use that if you want to.

---

### Post by mayagrafix on 2014-03-30
> **bapoumba said:**
> Moved to Ubuntu +1.

Do not enable them as is, some are for raring, others for saucy. **Check if each one of them have a trusty repo,** then use that if you want to.

How would I go about doing that? is there a terminal command line that will tell me if a ppa is good?

---

### Post by grahammechanical on 2014-03-30
You can search for them in Launchpad and see if there is a trusty version of the PPA. For example, the first one in that list is [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu)

I google searched "launchpad ehoover" and I found this link

[https://launchpad.net/~ehoover/+archive/compholio/](https://launchpad.net/~ehoover/+archive/compholio/)

I then click "Technical details about this PPA" and I click the box Choose your Ubuntu version and in the drop down menu list I see a version for trusty. The upgrade will not upgrade software installed through a PPA. So, it is best to uninstall the software and reinstall from the PPA available for the new release of Ubuntu if one is available.

Regards.

---

### Post by mayagrafix on 2014-03-30
Thanks! Great advice.

---

