---
title: "Idea for Package Manager"
date: 2007-07-16
forum: The Cafe
---

### Post by dxdemetriou on 2007-07-16
Hi,
I wanted to ask about some things for a long time ago:
1)When somebody uses "checkinstall", "alien", etc to install a package, and later is replaced by an official Ubuntu's package with different paths, wouldn't this mess up some things and will be two times the same thing in different paths? I am not sure about this, but wouldn't be useful to exist a warning about these cases?
2)Is there a possibility to coexists with synaptic or something, something that can handle SVN, etc with some working tested scripts, to create a deb package, and to work with the normal way we update our system? I have seen the post:
[http://ubuntuforums.org/showpost.php?p=293071&postcount=5](http://ubuntuforums.org/showpost.php?p=293071&postcount=5)
from:
[http://ubuntuforums.org/showthread.php?t=55490](http://ubuntuforums.org/showthread.php?t=55490)
about this. I just ask if it could be at least a temporary solution to can easily somebody install some new package up to the time added to official repos, or just a trunk version.
What do you think about these?
ps. as many times I said, sorry for my English.. :)

---

### Post by FuturePilot on 2007-07-16
About the first point. Usually the only time you would need to use Alien or build something yourself is if it's not in the repos, so you wouldn't have to worry about it getting replaced with an update. But if you did build something from source that is also in the repos, for whatever reason (usually to compile it with extra features) you can lock it in with Synaptic so it won't be updated.

---

### Post by dxdemetriou on 2007-07-16
I asked about this because I have Ubuntu from Breezy upgraded consequently to Feisty, and sure I would make a mistake then I didn't know well some things. From the other hand are deb packages like from medibuntu etc. How can a new user to know which is safe and which needs care? Like the compiz-fusion I know two places:
[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/)
[http://syzygy42.tuxfamily.org/dists/feisty/compiz/](http://syzygy42.tuxfamily.org/dists/feisty/compiz/)
the second one are backported from gutsy, and the first one are built from source, and I don't know if the package names are correct to can be used with gutsy.
It's one example why I asked about the possibility to check the package manager, because as the packages increases becomes more difficult to keep a track

edit: also this one could be a good idea.
[http://ubuntuforums.org/showthread.php?p=3030919#post3030919](http://ubuntuforums.org/showthread.php?p=3030919#post3030919)
Sorry that is not relative to the title, I saw it and I just wanted to say it :)

---

### Post by DeadSuperHero on 2007-07-16
Yeah, sometimes the Package Manager can get frustrating. Luckily, you have the best manual in the world for it.
These forums.
Still, everyone can improve in something.

---

### Post by dxdemetriou on 2007-07-19
ok, but I still think that when will do upgrade distribution, after that all 3rd parties repos are disabled and defined all as local included the actually local, the upgrade must not make that packages if newer packages exists or to ask the user. As I said before, after three upgrades I have so many local packages and is difficult to uninstall them or to check them one by one. At least I haven't problems yet, but I'm sure that some packages are broken by this.

---

