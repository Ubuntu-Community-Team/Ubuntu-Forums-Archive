---
title: "dist-upgrade blues"
date: 2005-10-14
forum: The Cafe
---

### Post by Brunellus on 2005-10-14
well friends, against my better judgment and carried away by an excess of enthusiasm, I went and upgraded to breezy.

I updated sources.list and ran the appropriate commands in a console, and let it cook overnight.

Woke up this morning, confirmed my choice of wordlist, hit return, watched stuff scroll by as I got dressed and sipped my morning coffee....and did a cold boot before going to work, just to see what a new splash screen looked like.

Nothing.  X didn't start.  suspecting something had gone awry on the update, I did another dist-upgrade and found a screenfull of broken dependencies and a bizarre GPG BADSIG error, which I have reported in the relevant thread in the Breezy Install Support forum.

Is one of the repos down, or something?  I'm really digging the textmode practice I'm getting at home, but I'm going to want X back soon.

---

### Post by Kimm on 2005-10-14
I got pretty much the same thing after upgrading to breezy (although I upgraded before the official release), acctually this seems almost exactly like the same problem.

I suggest you find out what programs are unhappy and then you try to apt-get them, listen to what your package manager tells you and resolve the issue :-P

I remember my problem had something to do with fonts... and I had to remove one package and replace it with something else... that worked rather well.. I think, alteast X works, but I get lots of packages that are "held back"

---

### Post by Stormy Eyes on 2005-10-14
Brunellus, check your xorg.conf file; the new X.org might not like the specified keyboard driver. I had that problem when I upgraded to Breezy back in September. I'm at work, or I'd post the keyboard section of my xorg.conf for you.

---

### Post by Brunellus on 2005-10-14
I'll be sure to check xorg.conf when I get back.  Here's the thing, though--there are a lot of shared dependencies that were either not installed or not downloaded at all, it seems (libcairo and so forth).  What's the deal with all that?

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=Brunellus]I'll be sure to check xorg.conf when I get back.  Here's the thing, though--there are a lot of shared dependencies that were either not installed or not downloaded at all, it seems (libcairo and so forth).  What's the deal with all that?[/QUOTE]

I don't know. I don't remember having that problem when I upgraded, but I used apt-get dselect-upgrade instead of dist-upgrade.

---

