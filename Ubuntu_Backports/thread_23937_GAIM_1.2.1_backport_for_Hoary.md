---
title: "GAIM 1.2.1 backport for Hoary"
date: 2005-04-04
forum: Ubuntu Backports
---

### Post by jdong on 2005-04-04
Ok, I've just packaged GAIM 1.2.1 from Debian, for Hoary. It's currently uploading into staging. Thought some of you might want to know!

I did not package this for Warty because:

1. The repository is closed, and the previous GAIM backport is recent enough...
2. Libraries have diverged too much. libglib is the main killer.

---

### Post by IdoMcFly on 2005-04-05
what are the repositories to add ?

---

### Post by panabar on 2005-04-05
Its in the staging area the source line is :

```

deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted 

```
you should also check 
[Backports Page](http://backports.ubuntuforums.org/)

---

### Post by jdong on 2005-04-05
Please do read the bolded warning on the Backports page about the responsibility/risk that you assume when using the 'staging' tree.

---

### Post by jdong on 2005-04-06
I have determined that this backport is stable, so I promoted it :)

---

### Post by Shambler on 2005-04-06
Why isn't GAIM 1.2.1 in Hoary? Too late? Or other reasons?
If it was simply too late, will it be in grumpy/breezy (hell, I don't know the name of the  next release...  :???: )?

---

### Post by jdong on 2005-04-06
It's too late in the release cycle to make such drastic changes.

---

### Post by Gnobody on 2005-04-08
Where is the AMD64 package?  Is there a seperate repository for the AMD64 backports.  Are there any AMD64 packagers?  If not is there a deb-source repository where I can "apt-get source --compile gaim" ?

---

### Post by Eproxus on 2005-04-28
Excuse my stupidity but I can't find Gaim 1.2.1 with apt-get or Synaptic after adding and reloading the backports. Have I done something wrong?

EDIT: Fixed. Ah, staging was not the way to go!

---

### Post by jdong on 2005-04-28
Staging is not comprehensive; it's **incremental** -- designed to be used ALONG with the stable tree. To use Backports, at the very minimum you should include the stable tree. Afterwards, you may elect to help me beta-test by adding the staging tree :)

---

