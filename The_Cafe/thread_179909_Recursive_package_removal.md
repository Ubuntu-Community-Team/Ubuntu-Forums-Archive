---
title: "Recursive package removal"
date: 2006-05-21
forum: The Cafe
---

### Post by mint on 2006-05-21
Is it possible to perform recursive removals of packages and their dependencies in Ubuntu?

Specifically, I am looking for a "pacman -Rncs [package_name]" type functionality, whereby the package and all of it's dependencies (that aren't depended on by any other package are removed).

Currently I am using deborphan to try to manage my orphaned packages, but it's a losing battle.

Thanks very much in advance.

---

### Post by Jucato on 2006-05-21
They say that Aptitude has a feature similar to that. Unfortunately, for it to work, those packages must be installed using Aptitude also. 

So far, I have not yet encountered something like this. I think it would be good to have a feature that also uninstalls packages and its dependencies, as long as it's possible. deborphan and kleansweep (a similar KDE app) just look for orphaned packages, which wouldn't exist if they were properly uninstalled.

Btw, there's a trick that I do in Synaptic whenever I'm installing many (more than 10) packages and their dependencies so that I could easily uninstall them later on.

---

### Post by detgar on 2006-05-21
[QUOTE=mint]Is it possible to perform recursive removals of packages and their dependencies in Ubuntu?[/QUOTE]

debfoster seems a good way of doing this. It's in universe.

---

### Post by scooper on 2006-05-21
[QUOTE=mint]Currently I am using deborphan to try to manage my orphaned packages, but it's a losing battle.[/QUOTE]

Just curious why you find using deborphan a "losing battle"?  It's always worked well for me.  I just periodically do something like "sudo apt-get remove $(deborphan)" and keep repeating until it does nothing.  Never had a problem caused by this procedure, and it seems pretty thorough.

---

### Post by mint on 2006-05-21
I guess I just was frustrated by the "manualness" of deborphan.  It just seems like it would be a natural feature with all of the information that a Debian package contains.

I'm going to try using debfoster too.  We'll see if that fixes my "need" for software cleanliness.

[edit]
Debfoster is perfect.  I remembered using it in the past with not terrible results, but using the Prune option makes it do exactly what I want it to.
[/edit]

Thanks very much for the help.

---

### Post by Fabioamd87 on 2012-05-21
there is only a problem, when removing debfoster DOESN'T INTERRUPT ITSELF with control+c

---

### Post by roelforg on 2012-05-21
Doesn't apt-get autodetect this?
If i ever do stuff like that,
sudo apt-get autoremove
always cleans those packages.

---

### Post by oldos2er on 2012-05-21
Old thread is old.

---

