---
title: "Why Rezound is no longer in UbuntuStudio repositories."
date: 2012-05-07
forum: Ubuntu Studio
---

### Post by rbgtoffolo on 2012-05-07
Hello everyone!!

First: Congratulations for this fantastic version of UbuntuStudio. I have installed and it is working great!!

Second: Why Rezound sound editor is no longer in the Ubuntu Studio  repositories? Rezound is a great sound editor, much more stable and  functional than Audacity.

Tanks for attention!!

Best whishes!
Rael Toffolo

---

### Post by sgx on 2012-05-08
[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

it's in the list. Sometimes time is short for packagers
to see why something doesn't work, maybe system libraries
moved on, while an app is abandoned, and others can be used
for the same tasks.

sudo dpkg -i name.deb will install it manually, and if dependencies are needed, it will mention them, and you can download and install them, and their dependencies, if any, til it finally works.

Cheers

---

