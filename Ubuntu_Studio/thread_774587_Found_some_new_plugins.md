---
title: "Found some new plugins"
date: 2008-04-29
forum: Ubuntu Studio
---

### Post by Stochastic on 2008-04-29
Here's a couple new plugins, not yet packaged with UbuntuStudio, that people might find useful: [http://calf.sourceforge.net/](http://calf.sourceforge.net/)

They're in the early development phase, but the user-interfaces look interesting/promising.

---

### Post by warbread on 2008-04-30
Very nice.  That vintage delay especially is of interest to me.

---

### Post by Stochastic on 2009-01-14
So I've gone ahead and packaged these for Ubuntu.  There's versions for Hardy, Intrepid, and Jaunty all in my PPA repo.
just add the appropriate repository to your /etc/apt/sources.list
```
deb http://ppa.launchpad.net/stochastic/ubuntu hardy main
deb-src http://ppa.launchpad.net/stochastic/ubuntu hardy main

deb http://ppa.launchpad.net/stochastic/ubuntu intrepid main
deb-src http://ppa.launchpad.net/stochastic/ubuntu intrepid main

deb http://ppa.launchpad.net/stochastic/ubuntu jaunty main
deb-src http://ppa.launchpad.net/stochastic/ubuntu jaunty main
```

then do ```
sudo apt-get update
sudo apt-get install calf-plugins
```

Enjoy, and please let me know if there are any bugs/troubles/etc.. in the packages.

---

### Post by marseille on 2009-06-25
:KS

h0tt! mad thx:) cant wait 2 use this... 

* [http://greyrockstudio.blogspot.com/2009/05/ubuntu-studio-jaunty.html](http://greyrockstudio.blogspot.com/2009/05/ubuntu-studio-jaunty.html)

* [http://calf.sourceforge.net/](http://calf.sourceforge.net/)

still waiting on RT kernel...

---

