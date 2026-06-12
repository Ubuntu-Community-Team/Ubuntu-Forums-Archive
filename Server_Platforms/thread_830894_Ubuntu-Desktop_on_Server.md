---
title: "Ubuntu-Desktop on Server"
date: 2008-06-16
forum: Server Platforms
---

### Post by abshirf2 on 2008-06-16
Hello all,

I have installed ubuntu server (Hardy Heron) - because i want to learn about Linux servers. I have put this on my LAN and have installed the ubuntu-desktop.

If i don't startX (X server - I understand it as graphical mode) or if i stop it - does it have the same effect on my server as if the desktop wasn't even installed?

If not, how can I un-install the ubuntu desktop?

Thanks all

---

### Post by blazercist on 2008-06-16
basically, if you don't startx then the only difference is that the packages take up some harddrive space... thats all.

---

### Post by abshirf2 on 2008-06-16
> **blazercist said:**
> basically, if you don't startx then the only difference is that the packages take up some harddrive space... thats all.

Sweet! Thanks for the quick and concise reply! :)

---

### Post by hyper_ch on 2008-06-16
no, the server also uses a different kernel than the desktop... run:

```

uname -a

```

To see what your kernel is. Very likely it's 2.6.24-19-generic. If you want to use the server optimized kernel just install the ...-server one and boot the computer with that one.

---

### Post by blazercist on 2008-06-16
> **hyper_ch said:**
> no, the server also uses a different kernel than the desktop... run:

```

uname -a

```

To see what your kernel is. Very likely it's 2.6.24-19-generic. If you want to use the server optimized kernel just install the ...-server one and boot the computer with that one.

very true but he will notice very little difference in basic user stuff

---

### Post by hyper_ch on 2008-06-16
except if he's using 4+ gb ram ;)

---

