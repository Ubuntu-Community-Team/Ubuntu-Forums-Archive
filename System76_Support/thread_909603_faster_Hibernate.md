---
title: "faster Hibernate?"
date: 2008-09-03
forum: System76 Support
---

### Post by elusivespoon on 2008-09-03
Since it looks like it may be awhile before Suspend functionality is back in daru2 are there any recommendations on speeding up the hibernate process? It's agonizingly long when I want to give my battery a break to hibernate and resume. Thanks.

---

### Post by thomasaaron on 2008-09-04
Not that I'm aware of. Hibernate sort of... is what it is. It stores all of your open apps to disk and then shuts down the computer. So, you still have to deal with the shutdown and start-up time. 

Technically, I don't think it is even *meant* to be faster than a typical shutdown/reboot cycle. I think the purpose is more one of convenience in that you do not have to re-open all your apps. It basically just returns to the state you were in before hibernating.

At least that's my understanding of it.

---

### Post by elusivespoon on 2008-09-04
yeah. It's looking like it might be faster to close everything and shutdown, rather than hibernate.

---

### Post by perce on 2008-09-05
Resuming from hibernation is faster than a normal start-up (at least for me) because you don't have to start the gnome session, which is very slow. When I had an old computer with 256MB of RAM it was a lot faster.

---

### Post by jdb on 2008-09-05
> **perce said:**
> Resuming from hibernation is faster than a normal start-up (at least for me) because you don't have to start the gnome session, which is very slow. When I had an old computer with 256MB of RAM it was a lot faster.

Gnome has a lot of overhead (not as much as KDE).
I used to run Xubuntu which has an xfce4 desktop & it booted a lot faster.
I'm now using a fluxbox desktop on top of Gentoo & it really boots fast.

jdb

---

