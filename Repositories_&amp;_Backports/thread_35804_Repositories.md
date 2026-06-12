---
title: "Repositories"
date: 2005-05-20
forum: Repositories &amp; Backports
---

### Post by dave9191 on 2005-05-20
Hey guys, 

I was just wondering who updates the repositories and how often. 

I also thought about something which is kinda worrying. What if someone puts malicious software (virus / trojan / etc) into the repositories and you install it cause you think its something else. Is that a possible threat or are things put into repositories screened first ?

Dave

---

### Post by ggozad on 2005-05-20
Interesting subject!
I think deb packages *are *signed as in the debian sarge distribution.
You will find more info and a script to check a release [here](http://www.linuxsecurity.com/docs/harden-doc/html/securing-debian-howto/ch7.en.html)

---

### Post by mendicant on 2005-05-20
The main, universe and multiverse repositories shouldn't change for a given version once that version has been released.  Updates should only occur in hoary-security and hoary-updates, and these changes are done by the Ubuntu team.

For other repositories, you'd have to check with the maintainer of those repositories.

---

### Post by dave9191 on 2005-05-22
So it is possible for packages outside the ubuntu team mainted ones to be dangerous for the system. As Linux grows in populariyty this might be exploited to attack Linux computers.

---

### Post by mendicant on 2005-05-22
Sure.  It's also possible that before you get a security update for an Ubuntu package, you'd get an attack via that vector.  So while you should certainly try to figure out what repositories you trust, it's only one part of security.  Maybe you don't need certain packages, maybe you can restrict your services (who, how, when etc), uninstall unused services, only have trusted users allowed to login, etc.

---

### Post by dave9191 on 2005-05-22
Thats sound advice, and Im not too worried about the security of my linux box ( I think that I have it patched up quite well ), but Im worried about new comers to linux who turn away from windows and might end up with similar sorts of security problems if they arent careful.

---

### Post by mendicant on 2005-05-23
That could happen, and for new users, even keeping up with security updates might be a problem.  So sure, newcomers need a little education in what they're doing to their system.

---

