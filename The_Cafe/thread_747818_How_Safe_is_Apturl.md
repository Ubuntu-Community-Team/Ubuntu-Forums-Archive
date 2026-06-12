---
title: "How Safe is Apturl?"
date: 2008-04-06
forum: The Cafe
---

### Post by yizuman on 2008-04-06
Saw this article from a website that has a name "Linux Hack3r" that made me weary of this program called "Apturl".

[http://linuxhack3r.com/2008/04/05/apturl-in-ubuntu/](http://linuxhack3r.com/2008/04/05/apturl-in-ubuntu/)

(Link found from digg.com)

How safe is this program? Can this program be exploited by script kiddies?

Thanks

---

### Post by TeraDyne on 2008-04-06
> **yizuman said:**
> Saw this article from a website that has a name "Linux Hack3r" that made me weary of this program called "Apturl".

[http://linuxhack3r.com/2008/04/05/apturl-in-ubuntu/](http://linuxhack3r.com/2008/04/05/apturl-in-ubuntu/)

(Link found from digg.com)

How safe is this program? Can this program be exploited by script kiddies?

Thanks

It only installs things that are in the repositories, so I doubt it. They'd have to trick the user to add their own repo and then install via apturl, which is a bit long shot in the Linux world. For one thing, most users are security savvy, and for another, they'd be found out too quickly thanks to the communities.

---

### Post by Mr. Picklesworth on 2008-04-07
Personally, I wish it *was* flexible enough to be exploitable (assuming a nitwit blindly clicks through the sanity checks). Suse's one click install is pretty cool.

However, it just installs existing packages; essentially a shortcut (and a front-end) to apt-get install. Handy for documentation, although the functionality appears to be dead in Hardy, now that we've moved to gvfs. Hm...

---

### Post by red_Marvin on 2008-04-07
Apturl is not less safe than a text box that says "type *apt-get install this or that* in the terminal".

---

