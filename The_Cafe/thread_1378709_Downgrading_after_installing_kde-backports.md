---
title: "Downgrading after installing kde-backports"
date: 2010-01-11
forum: The Cafe
---

### Post by sandyd on 2010-01-11
I recently noticed that a lot of plasma-desktop crashing going on, so i decided to 
remove the kde-backports ppa.

Afterwords, here was the extremely hard part.
Because most of the packages are linked together by dependencies and what not, each of the packages must be "force version"ed manually. 

I eventually gave up, and tracked down EVERY kde package i could see in synaptic, uninstalled all of them, and im now installing....

is there a better way of doing this?

-->[http://brainstorm.ubuntu.com/idea/23302/](http://brainstorm.ubuntu.com/idea/23302/)

---

### Post by Xbehave on 2010-01-11
ppa-purge (i think i got that from radeon repos though)
or apt pinning
or aptitude and doing it manually but with far fewer moves (downgrading kdebase-* will pull almost everything down but require some time looking at fixes, if you remove the ppa and setup pinning first aptitudes fixes might be simpler, i'm not sure)

---

### Post by nerdy_kid on 2010-01-11
i just went through the same thing with KDE 4.4 beta -- nightmare.  Totally voting for that brainstorm.

---

### Post by NoaHall on 2010-01-11
I think hoppi will agree with you, from what I've heard from him.

---

### Post by nerdy_kid on 2010-01-11
also, ive noticed that downgrading a package will cause all the packages that depend on it to be removed -- which kinda nullifies the whole point.  For example, i upgraded to qt4.6 on kde 4.3, and i tried downgrading for experiments sake (i have no issues at all), and apt-get wanted to take out all of KDE in the downgrade process.  kinda stupid.  If my opinion matters at all, i think that downgrading packages should be just as easy as upgrading them.  That would also make a 'system restore' app more feasible.

---

### Post by Xbehave on 2010-01-11
best solution would be to add ppa-purge to repos, but until then doing this in aptitude isn't too hard (I've done a reasonable amount of downgrading with aptitude) 
1)pick off the leaders (then run it)
2)pick of anything left (then run it)
3)then install anything that went missing. (There is probably a perfect fix in there somewhere but downgrading kdebase-something just offered me >600 (i think there would have been thousands of permutations), so i picked a reasonable one and would need to reinstall a few apps afterwards)

> **nerdy_kid said:**
> also, ive noticed that downgrading a package will cause all the packages that depend on it to be removed -- which kinda nullifies the whole point.
Use aptitude, it is much better at this.

---

### Post by boriskarloffinablender on 2010-01-12
if anyone is having problems with kde 4.4 rc1 on karmic, install [bleachbit](http://sourceforge.net/projects/bleachbit/files/bleachbit/bleachbit_0.7.2-1_all_ubuntu910.deb/download), and do a complete system clean. now everything for me is much more stable. quicker too.

---

### Post by nerdy_kid on 2010-01-12
> **Xbehave said:**
> best solution would be to add ppa-purge to repos, but until then doing this in aptitude isn't too hard (I've done a reasonable amount of downgrading with aptitude) 
1)pick off the leaders (then run it)
2)pick of anything left (then run it)
3)then install anything that went missing. (There is probably a perfect fix in there somewhere but downgrading kdebase-something just offered me >600 (i think there would have been thousands of permutations), so i picked a reasonable one and would need to reinstall a few apps afterwards)


Use aptitude, it is much better at this.




wow, now i know why people use aptitude over apt-get!  that thing is awesome!  It still is a pain to downgrade multiple packages though.

---

### Post by sandyd on 2010-01-12
we need a more user-friendly approach instead of using the commandline. Even though ive been running and tinkering with linux for 2 years, even I taook 4h to figure it out....

---

### Post by sandyd on 2010-02-16
bump.

---

