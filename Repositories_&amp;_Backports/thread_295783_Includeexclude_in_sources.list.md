---
title: "Include/exclude in sources.list"
date: 2006-11-08
forum: Repositories &amp; Backports
---

### Post by emdeem on 2006-11-08
I recently switched from Fedora and I'm still learning how apt works.  One nice feature of yum is that you can use "include" and "excluded" directives in the conf file on a per-repo basis.  This provides a nice way to only add certain packages from a repo and thereby eliminate conflicts.  Is there a similar mechanism for sources.list?

---

### Post by an.echte.trilingue on 2006-11-08
Yup.  

You can pin repositories so that apt will look in x repository, then y, then z.  In debian, for example, many people run testing, and in apt they have testings repositories set first, then unstable, then stable, so that apt will update packages from testing if they exist, then you can opt to install things from sid (say you want the 2.6.18 kernel), and then sarge last (for depreciated stuff that you need).  

This function is controlled by a seperate file from sources.list called /etc/apt/preferences.  You can google for it or read the apt-howto in debians docs to use this.  

Honestly, though, I really don't see the need for this in Ubuntu the way its repositories are set up, but the option is there if you want it.

And of course, if you do not want a certain repository at all, just comment it out with "#", or remove the entry.

Take care,

-mat

---

### Post by emdeem on 2006-11-08
Hmm, not quite the same, but it might do what I need.  I'll take a closer look, thanks.

---

### Post by an.echte.trilingue on 2006-11-09
What exactly are you trying to do?

---

### Post by emdeem on 2006-11-09
I would like to enable a couple of third party repos for only one or two packages each.  As an example, suppose I would like to add "deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main" to get only w32codecs.  I could just download and install the deb, but I prefer to list it in sources.list so I won't miss any updates.

In yum, there is a parameter like "include=w32codecs" that will tell it to ignore every package in that repo except for w32codecs.  The purpose of this is to avoid installing a newer version of something (i.e. mplayer) that might be in this repo and conflict with the official ubuntu repos.

---

