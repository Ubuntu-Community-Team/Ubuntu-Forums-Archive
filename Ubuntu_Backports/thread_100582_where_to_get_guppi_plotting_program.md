---
title: "where to get guppi plotting program?"
date: 2005-12-07
forum: Ubuntu Backports
---

### Post by incognito on 2005-12-07
Hi:

I want to install guppi, but when I use Synaptic to search updated Ubuntu, multiverse, and universe repositories all I come with are two gtk libraries but no program selection. I manually searched the graphics, science, and mathematics listings in Synaptic without luck. Searching the ubuntu site and these groups was not helpful. When I googled "ubuntu guppi" it seems like there are multiple ubuntu repository references to guppi. How do I get guppi? Thanks in advance.

incognito

---

### Post by 23meg on 2005-12-08
From the guppi site:

> Guppi is a library that can be used to extend other programs. Your own programs can either link directly to Guppi's shared libraries, or can embed Guppi plots via Bonobo, GNOME's component architecture.

> Guppi is still in an early stage of development, and is still missing several important features. We would still like to encourage you to download Guppi and try it out. If you need a fully-functional plotting package right now, you might want to look into some other free plot programs. Perhaps guppi is in development stage at the moment and is only available as a library, without a frontend. There are [other free plotting programs]("http://www.gnome.org/projects/guppi/otherprogs.shtml") though.

---

### Post by macleod199 on 2005-12-09
[QUOTE=incognito]Hi:

I want to install guppi, but when I use Synaptic to search updated Ubuntu, multiverse, and universe repositories all I come with are two gtk libraries but no program selection. I manually searched the graphics, science, and mathematics listings in Synaptic without luck. Searching the ubuntu site and these groups was not helpful. When I googled "ubuntu guppi" it seems like there are multiple ubuntu repository references to guppi. How do I get guppi? Thanks in advance.

incognito[/QUOTE]

I'm pretty sure guppi is no longer maintained/was never ported to gtk2, which is why Gnucash has taken so long to try to migrate to gtk2/gnome2. Debian wants to kill gtk1 totally, and Gnucash is the only thing really saving it.

---

