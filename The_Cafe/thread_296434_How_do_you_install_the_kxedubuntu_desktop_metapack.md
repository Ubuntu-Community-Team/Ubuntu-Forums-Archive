---
title: "How do you install the k/x/ed/ubuntu desktop metapackages with a server install?"
date: 2006-11-09
forum: The Cafe
---

### Post by user1397 on 2006-11-09
if you install ubuntu in server mode, are there more steps involved to installing those metapackages correctly?

do you have to add repos, or install some kind of base package before you can type "sudo aptitude install ubuntu-desktop"???

(yes, i do realize the irony of having a guide on installing the diff. DE's, but o well, i dont know much about servers....)

---

### Post by funkyade on 2006-11-09
I have always used the server install, and then done -

```
#> sudo aptitude install gdm gdm-themes xubuntu-desktop
```

I have also enabled the universe and multiverse repos straight after the initial install has finished (after the server, but before the desktop). Don't think you need them for the meta packages tho.

hth

++ if you use aptitude all the necessary dependencies, i.e. X11 will be installed also.

---

### Post by aysiu on 2006-11-09
You don't need to enable extra repositories or add GDM or KDM explicitly.

*ubuntu-desktop* and *xubuntu-desktop* both include GDM, and *kubuntu-desktop* includes KDM.

---

### Post by kuja on 2006-11-09
And just what is the point of doing things this way with the server install anyway? You're getting exactly the same effect as a regular(alternate/live) install, are you not?

---

### Post by user1397 on 2006-11-09
> **kuja said:**
> And just what is the point of doing things this way with the server install anyway? You're getting exactly the same effect as a regular(alternate/live) install, are you not?o i was just asking cause i have an ubuntu dvd, but i wanted to install server mode, and then aptitude install kubuntu, so that i wouln't have to download a whole cd.

---

### Post by roderikk on 2006-11-09
> **kuja said:**
> And just what is the point of doing things this way with the server install anyway? You're getting exactly the same effect as a regular(alternate/live) install, are you not?
I usually use this method as well, since it always seems to me that when I do a regular install (especially from the liveCD) things just crash for me. A server install has never crashed on me (/me touches wood ;-) ). Also when you use aptitude to install the meta package you can just as easily remove it and install another meta package (not that I ever did thát..... :-) ).

---

### Post by funkyade on 2006-11-09
> **kuja said:**
> And just what is the point of doing things this way with the server install anyway? You're getting exactly the same effect as a regular(alternate/live) install, are you not?

No. The server install is a minimal command-line environment, that you can then add on the components you need. Using Aptitude allows you to completely remove every single thing that you install in this process, the liveCD installer does not.

e.g.
```
~> sudo aptitude remove ubuntu-desktop
```

will actually remove everything you installed in ubuntu-desktop. Do this on a regular liveCD install, and you'll get all sorts of dependency problems.

---

### Post by user1397 on 2006-11-09
yay, i just installed kubuntu using aptitude, through the server install.  its working great.

---

### Post by funkyade on 2006-11-10
> **aysiu said:**
> You don't need to enable extra repositories or add GDM or KDM explicitly.

*ubuntu-desktop* and *xubuntu-desktop* both include GDM, and *kubuntu-desktop* includes KDM.

This is just an old habit...! Early on in xubuntu-desktop's life you had to, well, I did at least for some reason... my fingers type those things automatically for me... the gdm-themes package is a nice thing to have anyway.

Actually use to use WDM or XDM, which look ugly, but don't have the same amount of bloat.

---

