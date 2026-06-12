---
title: "Extras Mirrors?"
date: 2005-12-06
forum: Ubuntu Backports
---

### Post by Limulus on 2005-12-06
There used to be a list of mirrors for extras on [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php) but they've since renovated and its 404.  Does anyone know where the list moved?  If it was just taken down, could it be put back up somewhere?

---

### Post by tomski on 2005-12-06
add this line :

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

 to :

/etc/apt/sources.list

---

### Post by jdong on 2005-12-06
Note that Breezy Extras don't really exist anymore, and I'm trying hard not to have to resort to it.... There are better, more sound ways of accomplishing what Breezy Extras wanted to do...

---

### Post by tomski on 2005-12-06
or have a look at this 

[http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672)


or you could just completly ignore me as jdong has just replied and well he would know!!!

---

### Post by Limulus on 2005-12-06
tomski: Thanks, but I actually have a repository for extras already:

> deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) breezy-extras main universe multiverse restricted
I just wanted to know what happened to the list :)

jdong: I hadn't realized... Are there actually any packages in Breezy Extras right now?  Or is all the good stuff in PLF? ;)  Are you planning on closing down the extras repo? (if so I won't be sad; it would be one less line to maintain in sources.list ^_-)

---

### Post by jdong on 2005-12-06
Extras is superseded in two ways:

**Restricted Formats**: I'm too cowardly to face potential legal action against me in the US. Consult the Ubuntu PLF for those

**New Packages**: Try to request them from the Ubuntu MOTU team. That'll make all of us happier in the future when it gets into the Ubuntu package collection.

---

### Post by Limulus on 2005-12-06
[Masters of the Universe]("https://wiki.ubuntu.com/MOTU") *heh*

OK, I just looked through all the directories in breezy-extras and breezy-extras-staging and I see what you mean; the only package was in the latter and it was a version of w32codecs, which I can just as easily get from the PLF.

Thank you for pointing this out; I will update [my page](http://members.shaw.ca/Limulus/ubuntu.html) to reflect that and bring the point up in the future when the Extras Repository gets mentioned.

---

### Post by ubuntu_demon on 2005-12-07
[QUOTE=jdong]Extras is superseded in two ways:

**Restricted Formats**: I'm too cowardly to face potential legal action against me in the US. Consult the Ubuntu PLF for those

**New Packages**: Try to request them from the Ubuntu MOTU team. That'll make all of us happier in the future when it gets into the Ubuntu package collection.[/QUOTE]
Are there any useful desktop packages in extras that are not in plf or universe ?

---

### Post by jdong on 2005-12-07
[QUOTE=ubuntu_demon]Are there any useful desktop packages in extras that are not in plf or universe ?[/QUOTE]

For Hoary, yes (a few feature-enhanced gtkpods, freenx, and some others).

For Breezy, no. Breezy Extras is empty, and if at all possible I intend on keeping it that way.

---

### Post by ubuntu_demon on 2005-12-08
[QUOTE=jdong]For Hoary, yes (a few feature-enhanced gtkpods, freenx, and some others).

For Breezy, no. Breezy Extras is empty, and if at all possible I intend on keeping it that way.[/QUOTE]
thnx

---

