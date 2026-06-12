---
title: "Debian source?"
date: 2005-01-03
forum: Repositories &amp; Backports
---

### Post by tiiim on 2005-01-03
When we update via SPM it obviously just goes to the 'official' Ubuntu way? But is actually ok if we also dive in the Debian sources as well and add them to the Ubuntu SPM since they are the same core system. I know its not reccomended but is it really that bad? If so how do i go about doing it for i like to get other software that the Unbuntu side dont quite have yet but i know they are similar trees.

---

### Post by Rancoras on 2005-01-03
It's not advisable to use anything from the debian side of things.  There are subtle differences that can wreak havoc on your system.

---

### Post by tiiim on 2005-01-03
[QUOTE=Rancoras]It's not advisable to use anything from the debian side of things.  There are subtle differences that can wreak havoc on your system.[/QUOTE]
 but it is ok to use the universe side of things aint it since that is Debian but on the Unbuntu side? I mean they will follow official Ubuntu ways even though they wont be security updated?

as in de-comment the universe side in the sources.list?

---

### Post by Rancoras on 2005-01-03
Yes, universe is fine, and you're right, no security updates for anything in universe.

---

### Post by jdong on 2005-01-03
I would advise AGAINST doing so period, especially from Sid. It's linked against different library versions than Warty.

---

### Post by CompShrink on 2005-01-11
I would not suggest going beyond universe, and possibly backports and other repos listed in the wiki howto's. I have installed a few things from these, and it seems stable. I would advise not to get anything from the non-ubuntu repos other than what's listed in wiki topics, as those are relatively commonly used, and so you ahve less chance of screwing up your system. 

Still not supported though, so do it at your own risk.

---

### Post by az on 2005-01-11
Speaking of source, you can play it a bit safer and get the source-code packages of things in debian.  You will still be dealing with unstable Sid, but you will be compiling against the libraries on your system.

apt-get build-dep (package)
apt-get source (package)

---

