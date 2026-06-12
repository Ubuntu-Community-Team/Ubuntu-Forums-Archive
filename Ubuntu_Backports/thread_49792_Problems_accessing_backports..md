---
title: "Problems accessing backports."
date: 2005-07-17
forum: Ubuntu Backports
---

### Post by aum11 on 2005-07-17
I am a noob so I may be making a stupid mistake.
I always get failed when accessing the mirrormax backports under Synaptic.  I have set it up as per the unofficial guide.
So, today I decided to add the Brianpuccio backports and I get the following problem.

W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-backports/main Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubunt...rts-repository_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-backports/universe Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubunt...rts-repository_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubunt...rts-repository_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-backports/restricted Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubunt...rts-repository_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-extras/main Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubunt...rts-repository_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-extras/universe Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubunt...rts-repository_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubunt...rts-repository_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-extras/restricted Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubunt...rts-repository_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Any suggestions?
Thanks :)

---

### Post by Brian Puccio on 2005-07-18
Slightly diffferent URL:

deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-extras main universe multiverse restricted

---

### Post by aum11 on 2005-07-18
Thanks Brian...all better! :)

---

