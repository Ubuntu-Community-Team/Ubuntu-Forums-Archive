---
title: "VRMS non-free packages with status other than installed"
date: 2008-01-29
forum: The Cafe
---

### Post by zorkerz on 2008-01-29
What does this mean?
"Non-free packages with status other than installed"

for me it lists sun-java6-bin and sun-java6-jre
both of these were installed on my computer previously but are not now. What other status is there for packages besides installed and not installed. Im assuming it does not report not installed packages because then everything in the repository would be reported or some similar result.

---

### Post by az on 2008-01-29
It would report everything in the Multiverse and Restricted repositories.  Everything in Main and Universe is free/libre.

Edit:  I put on my glasses and actually read your post.  Other than installed and not installed there is half-installed (broken) and removed (just config files present).

---

### Post by picpak on 2008-01-29
> **zorkerz said:**
> What does this mean?
"Non-free packages with status other than installed"

for me it lists sun-java6-bin and sun-java6-jre
both of these were installed on my computer previously but are not now. What other status is there for packages besides installed and not installed. Im assuming it does not report not installed packages because then everything in the repository would be reported or some similar result.

The status you'd be looking for in Synaptic is "Not installed (residual config)".

---

### Post by zorkerz on 2008-01-29
Ok for config files that are left over. Are these always left in my home? or could they be anywhere.

-As a side note: Im on this kick of trying to remove any packages that I do not use. A good way to start this for me would be to know which packages I have installed that are not installed by default.

(im less worried about default packages that i do not use than ones i have installed myself over time)
thanks

---

### Post by zorkerz on 2008-01-29
thanks picpak i never new about that

---

### Post by macogw on 2008-01-29
sudo aptitude purge sun-java6-jre

That'd get all the config stuff to go away.

---

### Post by zorkerz on 2008-01-29
wow this is great so many useful tidbits to know.

A little off topic: in synaptic package manager there are two sub categories for installed packages
(auto removable) and (local or obsolete) 

What do these refer to?
Can I assume that they are not critical for any other installed packages?
thanks

---

### Post by frup on 2008-01-29
Is the status of java still not GPL?

---

### Post by samwyse on 2008-01-29
> **zorkerz said:**
> wow this is great so many useful tidbits to know.

A little off topic: in synaptic package manager there are two sub categories for installed packages
(auto removable) and (local or obsolete) 

What do these refer to?
Can I assume that they are not critical for any other installed packages?
thanks

"Auto removable" are packages that were installed to fill dependencies for a package that has been removed and thus are currently not needed. "Local" are packages installed from outside the repos. "Obsolete" are packages that have been removed from the repos, I think.

---

### Post by macogw on 2008-01-29
> **samwyse said:**
> "Auto removable" are packages that were installed to fill dependencies for a package that has been removed and thus are currently not needed. "Local" are packages installed from outside the repos. "Obsolete" are packages that have been removed from the repos, I think.

sudo apt-get autoremove

will remove all of the autoremovable packages.

---

### Post by macogw on 2008-01-29
> **frup said:**
> Is the status of java still not GPL?

I think the *next* version will be, but 6 isn't.  If you want a GPL'd implementation of Java, look at icedtea-java7-jre  It's very good.  Liferea (**Li**nux **Fe**ed **Rea**der) actually crashes on websites with .swf's in them if you use Sun's instead of the fully-FOSS IcedTea.

---

### Post by zorkerz on 2008-01-29
Java continues to be a pain for me using my schools webct. I had icedtea  installed  untill it did not work and sun-java6 installed but that did no better. The only thing that has worked in uninstalling both. [Heres]("http://ubuntuforums.org/showthread.php?t=680856") my post on it.

---

