---
title: "Don't quite understand sources.list syntax"
date: 2005-04-05
forum: Repositories &amp; Backports
---

### Post by stoneguy on 2005-04-05
I'm getting ready for the upgrade to Hoary released by
    1. reviewing the forum
    2. examining my apt files
    3. practicing deep breathing
    4. ordering a refill on my valium scrip :)

At least I restrained myself from using the backports repositories for the warty lifespan. But I **do** have some nonstandard pointers. They're to debian-marillat and to wine.sourceforge.net.

I walked through each of the sites to make sure that the change-all *warty* to *hoary* would get me someplace that existed (I'll add security-updates before the upgrade). Then I noticed that the line for wine ended in *warty/*. Note that trailing **/**.

I tried deleting it just for the heck of it. After all, none of the other lines had it. Bzzt, bad move. So I went to the APT HOWTO to try to find out what it means. No info.

The only thing left was to make a wild guess, and then try to find out if anyone knows the answer. The guess is, since there's no dists subtree at the URL. Is there a convention that if the following parameter has the trailing **/**, it's the name of a directory?

---

### Post by taygan on 2005-04-06
Here's a link to the Debian Repository HOWTO, the "using a repository section" it covers the sources.list syntax, and gives examples of when to use or not use the slash.

[http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#using-a-repository](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#using-a-repository)


a snippet > Example 3. Two Automatic Repositories from my sources.list

deb [ftp://sunsite.cnlab-switch.ch/mirror/debian/](ftp://sunsite.cnlab-switch.ch/mirror/debian/) unstable main contrib non-free
deb-src [ftp://sunsite.cnlab-switch.ch/mirror/debian/](ftp://sunsite.cnlab-switch.ch/mirror/debian/) unstable main contrib non-free

These two lines specify an automatic binary and source repository with root [ftp://sunsite.cnlab-switch.ch/mirror/debian/](ftp://sunsite.cnlab-switch.ch/mirror/debian/), the distribution unstable and the components main, contrib and non-free.

If the repository is not automatic, then the distribution specifies the relative path to the index files and must end with a slash, and no components may be specified.

Example 4. Two Trivial Repositories from my sources.list

deb file:///home/aisotton/rep-exact binary/
deb-src file:///home/aisotton/rep-exact source/

The first of these two lines specifies a binary repository in /home/aisotton/rep-exact/binary on my local machine; the second specifies a source repository in /home/aisotton/rep-exact/source.

Good Luck.

---

### Post by stoneguy on 2005-04-06
Thx Taygan for pointing me to the right HOWTO.

---

