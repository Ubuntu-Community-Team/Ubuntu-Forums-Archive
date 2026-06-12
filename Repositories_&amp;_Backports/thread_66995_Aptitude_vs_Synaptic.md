---
title: "Aptitude vs Synaptic"
date: 2005-09-19
forum: Repositories &amp; Backports
---

### Post by pmilin@ptt.yu on 2005-09-19
Hi!
I am newbe and a bit confused with the fact the Ubuntu is forcing Synaptic while on the Net you can find that Aptitude is mostly recommended as better. From my point of view, Synaptic is easier (especially in Search options), but I am ready to get familiar with Aptitute if this is the one. Hence, can anyone explain which of the two is better and why?

Sincerely,
pmilin

---

### Post by ltmon on 2005-09-19
[QUOTE=pmilin@ptt.yu]Hi!
I am newbe and a bit confused with the fact the Ubuntu is forcing Synaptic while on the Net you can find that Aptitude is mostly recommended as better. From my point of view, Synaptic is easier (especially in Search options), but I am ready to get familiar with Aptitute if this is the one. Hence, can anyone explain which of the two is better and why?

Sincerely,
pmilin[/QUOTE]

Synaptic is definately less scary for a newbie.  You have to keyboard navigate in Aptitude.  It also has more advanced searching, and has a sources.list editor built in.

One thing Aptitude does better is remembers the dependencies for each package.  For example:

- install package A
- package A depends on package B so B is installed
- remove package A
- Aptitude remembers that package B is a dependency of package A, and finds that no other packages rely on it, so package B is removed also

Aptitude is faster to use once you get the hang of it.

L.

---

### Post by Endolith on 2008-11-25
> **ltmon said:**
> One thing Aptitude does better is remembers the dependencies for each package.

Why doesn't Synaptic?

---

### Post by Buffalo Soldier on 2008-11-28
> **ltmon said:**
> Aptitude remembers that package B is a dependency of package A, and finds that no other packages rely on it, so package B is removed also

I think since Ubuntu 7.10, Synaptic and Apt-Get has the same capability of removing orphan packages.

Plus, I find that Synaptic and Apt-Get detection of orphan packages is much better than Aptitude.

---

### Post by danf_1979 on 2008-11-30
Buffalo Soldier... link, case?

---

### Post by Buffalo Soldier on 2008-12-01
> **danf_1979 said:**
> Buffalo Soldier... link, case?

Just from my personal experience. Aptitude will sometimes try to uninstall packages that are not actually "orphan". Plus, I'm already used to **sudo apt-get *autoremove*** :D

---

### Post by zwaardmeester on 2008-12-02
I have a question regarding this orphan thing. Somehow it seems that **apt-get autoremove frobnitz** does not remove all dependencies that were installed together with package "frobnitz".

Example. Today I installed the tex-editor Kile. It needed 73 extra packages to be installed as well. When I removed it again I found only 32 packages marked as "no longer required". Among others, the KDE and qt libraries that were installed along with Kile were not marked for removal.

Since I don't have any other programs depending on these KDE libraries, why are they not marked orphan as well?

---

### Post by Buffalo Soldier on 2008-12-02
> **zwaardmeester said:**
> I have a question regarding this orphan thing. Somehow it seems that **apt-get autoremove frobnitz** does not remove all dependencies that were installed together with package "frobnitz".

Example. Today I installed the tex-editor Kile. It needed 73 extra packages to be installed as well. When I removed it again I found only 32 packages marked as "no longer required". Among others, the KDE and qt libraries that were installed along with Kile were not marked for removal.

Since I don't have any other programs depending on these KDE libraries, why are they not marked orphan as well?

_**FIRST** step, remove the application_:
```
sudo apt-get remove frobnitz
```
_OR_
```
sudo apt-get purge frobnitz
```

**remove**: Uninstall without removing configuration files
**purge**: Complete uninstall, remove everything including configuration files

_**SECOND** step, remove any orphaned packaged:_
```
sudo apt-get autoremove
```

---

