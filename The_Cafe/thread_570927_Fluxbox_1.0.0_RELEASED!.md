---
title: "Fluxbox 1.0.0 RELEASED!"
date: 2007-10-08
forum: The Cafe
---

### Post by plb on 2007-10-08
[http://fluxbox.sourceforge.net/version-0.9.php](http://fluxbox.sourceforge.net/version-0.9.php)

---

### Post by nest on 2007-10-08
thats good :D

thanks

---

### Post by -grubby on 2007-10-08
I'm gonna get it when the Ubuntu packages come

---

### Post by RAV TUX on 2007-10-08
> **plb said:**
> [http://fluxbox.sourceforge.net/version-0.9.php](http://fluxbox.sourceforge.net/version-0.9.php)

Awesome updating now!

---

### Post by yabbadabbadont on 2007-10-08
Good news, but I'll stick with the SVN version.  :D

---

### Post by phazeman on 2007-10-09
what is the repository that holds those ??

---

### Post by misfitpierce on 2007-10-09
Under debian downloads it still says ubuntu downloads to come... should I wait or try debian installs?

---

### Post by plb on 2007-10-09
All you need aside from build-essential is libx11-dev afaik

---

### Post by fuscia on 2007-10-09
too bad the new corners break my favorite theme (AXONKOLOR).

---

### Post by yabbadabbadont on 2007-10-09
> **plb said:**
> All you need aside from build-essential is libx11-dev afaik

No, you need a bit more than that using the configure defaults.  imlib2-dev for one thing.  The easy way to get what you need is to run in a terminal:
```
sudo apt-get build-dep fluxbox
```

---

### Post by Xappe on 2007-10-10
1.0.0 came into gutsy repositories today, with imlib2 and xinerama support compiled in!

---

### Post by happy-and-lost on 2007-10-10
Yay!

Shame I just replaced my slow Fluxbox machine...

Heck, it's worth a go anyway!

---

### Post by plb on 2007-10-10
It's in debian unstable already :)

---

### Post by bigyoy on 2007-10-10
looks cool i'll give it a go

---

### Post by RedSquirrel on 2007-10-10
> **yabbadabbadont said:**
> Good news, but I'll stick with the SVN version. 

Yeah, me too. :)


> **phazeman said:**
> what is the repository that holds those ??

svn checkout svn://svn.berlios.de/fluxbox/trunk fluxbox

See: [http://fluxbox.sourceforge.net/download.php#svn](http://fluxbox.sourceforge.net/download.php#svn)


> **misfitpierce said:**
> Under debian downloads it still says ubuntu downloads to come... should I wait or try debian installs?

That Debian page hasn't been updated for a while. Check the date: 23Jun2006. :)

I would recommend building your own deb package. It's not that hard. See the first link in my signature. I added some information about compiling. The other option is to wait for gutsy since it seems they have upgraded the package for gutsy.


I'm not all that impressed by the "new" rounded corners. This feature has been in the SVN version for a while, but I think it still looks "jagged" so I've generally stopped using it.

---

