---
title: "Why Gnome 2.20 in Debian Lenny when Hardy has 2.22?"
date: 2008-09-01
forum: The Cafe
---

### Post by kagashe on 2008-09-01
As per [Distrowatch Weekly]("http://distrowatch.com/weekly.php?issue=20080901#feature") Debian Lenny is going to come with Gnome 2.20 whereas Ubuntu Hardy has Gnome 2.22. It is said that Ubuntu begins development taking packages from Debian Sid but even Debian Sid has Gmone 2.20 only.

Does it means that Ubuntu Hardy team would have compiled their own Gnome 2.22. Then how Ubuntu depends upon Debian Sid?
Only for Kernel and Xorg.

Yes. There is something called Debian Experimental. But I think that this is mainly to borrow packages from Ubuntu to Debian and not other way round.

What do you think?

kagashe

---

### Post by Sef on 2008-09-01
Debian prefers stability, so they tend to have older packages.

---

### Post by miggols99 on 2008-09-01
But shouldn't sid (**un**stable) have the latest..everything?

---

### Post by tdrusk on 2008-09-01
> **miggols99 said:**
> But shouldn't sid (**un**stable) have the latest..everything?
He's talking about when they release it as the stable, what Etch is now. After this Sid will be the testing and something else will be unstable.

---

### Post by miggols99 on 2008-09-01
Unstable stays as sid forever according to this page:

[http://www.debian.org/releases/unstable/](http://www.debian.org/releases/unstable/)

---

### Post by Bachstelze on 2008-09-01
> **miggols99 said:**
> But shouldn't sid (**un**stable) have the latest..everything?

No, the belief is common that Sid is always on the bleeding edge, but as you can see, it is not always true.

---

### Post by Biochem on 2008-09-01
I'm using debian lenny amd64 and guess what about gnome says?

2.22.3

Seening it is believing

---

### Post by Erik Trybom on 2008-09-01
Yep, Distrowatch is wrong. Check out the Gnome packages in Lenny here: [http://packages.debian.org/testing/gnome/](http://packages.debian.org/testing/gnome/) (the gnome-about package, among others, gives the version number). 2.22 it is.

Sid happens to have the same version right now. Expect that to change soon after the next Gnome release is ready (scheduled for September 24).

---

### Post by cardinals_fan on 2008-09-01
Sid != Testing

..just thought I'd mention that.

---

### Post by kagashe on 2008-09-01
Sorry for my post. Distrowatch not only mentions this in the news but if you see the [Debian page]("http://distrowatch.com/table.php?distribution=Debian") the libgnome version given is 2.20.1.1 in Lenny as well as Sid.

I think Distrowatch is not updating the package list properly. There were comments on Distrowatch mentioning the mistake so I did not add mine.

kagashe

---

