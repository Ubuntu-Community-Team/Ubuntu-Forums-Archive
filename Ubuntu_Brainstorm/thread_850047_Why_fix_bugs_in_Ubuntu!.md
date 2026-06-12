---
title: "Why fix bugs in Ubuntu?!"
date: 2008-07-05
forum: Ubuntu Brainstorm
---

### Post by v1cho on 2008-07-05
This is something about Ubuntu and every other distro that I simply can't understand. Why do developers fix the bugs only for their own distro? Fix them for the whole Linux community! 
Developers are wasting their time fixing one and the same bug separately. I think that they should contribute to the mother project, not the last one of "chain"

---

### Post by Steveway on 2008-07-05
It seems like you are a bit confused. Why do you assume that the Developers are fixing bugs themselves and don't push them upstream? I give you a clue. Most bugfixes come from upstream and if Distributors fix bugs then they normally also get pushed upstream.

---

### Post by v1cho on 2008-07-05
Hmmmm... You mean that the bug is fixed for Ubuntu and then for the "upstream" (I'm not quite sure about the meaning of this word...English is not my mother language) 
Or you mean that it is fixed for the "upstream" and then for Ubuntu?

---

### Post by Steveway on 2008-07-05
Bugs are normally fixed [Upstream]("http://en.wikipedia.org/wiki/Upstream_(computer_science)") and in the other rare cases it gets handled like in that wikiarticle (see above).

---

### Post by justin whitaker on 2008-07-05
> **v1cho said:**
> Hmmmm... You mean that the bug is fixed for Ubuntu and then for the "upstream" (I'm not quite sure about the meaning of this word...English is not my mother language) 
Or you mean that it is fixed for the "upstream" and then for Ubuntu?

It works in both directions. Ubuntu is based on Debian. So if the Debian developers make a change, they make sure it is communicated to all of their "children" so they can make the appropriate changes. 

Similarly, if Ubuntu's Devs make a change, they communicate the fix "upstream" to the Debian team, who are then free to do with it what they like.

---

### Post by v1cho on 2008-07-11
Oh... That's how I thought it should be...  :)

---

### Post by bruce89 on 2008-07-11
> **justin whitaker said:**
> Similarly, if Ubuntu's Devs make a change, they communicate the fix "upstream" to the Debian team, who are then free to do with it what they like.

I would have thought the upstream project would be the most obvious place.

Most patches that Ubuntu add to packages are from upstream. (GNOME etc.)

---

### Post by ggaaron on 2008-08-21
> **justin whitaker said:**
> It works in both directions. Ubuntu is based on Debian. So if the Debian developers make a change, they make sure it is communicated to all of their "children" so they can make the appropriate changes. 

Similarly, if Ubuntu's Devs make a change, they communicate the fix "upstream" to the Debian team, who are then free to do with it what they like.

I think that question was not about Ubuntu - Debian relation, but Distribution - Package author (GNOME, KDE, X.Org) relation.

---

### Post by smartboyathome on 2008-08-21
> **ggaaron said:**
> I think that question was not about Ubuntu - Debian relation, but Distribution - Package author (GNOME, KDE, X.Org) relation.

Most of the packages are submitted to the projects, its just up to the projects whether they accept or reject them. As with OpenSSL, the project didn't accept the patch, and Debian's version was thus a variant.

---

