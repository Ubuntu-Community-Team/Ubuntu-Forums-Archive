---
title: "Several Crashes Occured on an Unmodified Alpha 1."
date: 2011-12-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2011-12-08
Earlier today I had several crashes occur on an Unmodified Alpha 1 Installation, most of the Bug Reports had already been reported by someone else, some however were related to either Third Party Software and/or Software that needed Updating to a Newer Version, which is not possible because I was offered a Partial Upgrade and the Software Upgrader was one of the Alpha 1 packages that crashed a couple of times! Right now I am Installing today's Nightly Build in order to see if it fixes my problems Or NOT. I will report back just as soon as the install is finished. Just FYI.

---

### Post by jerrylamos on 2011-12-09
Just after installing from .iso or CD on first boot, I choose 
systems settings, software sources, other software 
turn off the two "third party" checkmarks
turn on the two "partner" checkmarks

No idea why the defaults seem exactly backwards.  Why would I ever want "unsupported third party" stuff??  Unless I specifically wanted it. 

then under Updates set "automatically check" to "Never"
and un-check "unsupported".  No clue on that one either.

Even though the .iso might be "today's" I do
sudo apt-get install aptitude 
sudo aptitude update
sudo aptitude safe-upgrade

Usually get a whole pile of updates...

Sometmes an update didn't install, like sometimes a new linux-image, so I do
sudo aptitude full-upgrade
with my fingers crossed....

I update when I want to, usually daily on "unstable", and do NOT want a big "Update" window slamming open on top of what I'm doing.

Jerry

---

### Post by coffeecat on 2011-12-09
> **kevpan815 said:**
> I was offered a Partial Upgrade

It's not clear whether you did proceed with a partial upgrade. You might want to have a look at the sticky on partial upgrades before you do:

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

