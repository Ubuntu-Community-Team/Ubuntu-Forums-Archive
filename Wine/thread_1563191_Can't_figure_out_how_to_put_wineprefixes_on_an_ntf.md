---
title: "Can't figure out how to put wineprefixes on an ntfs partition"
date: 2010-08-28
forum: Wine
---

### Post by kw2010 on 2010-08-28
For a year now, I've been happily putting all my windows applications in their own wineprefixes, and everything has worked nicely. Now I'm running out of space on my ext3 partition, and I thought that I'd just as well put my wineprefixes on my data drive, which happens to be an ntfs partition. Suddenly Wine throws a fit, saying "wine: /mnt/ntfs/.wineprefixes/spirits  is not owned by you", and sure enough, it's owned by root.

It's only if I try to use wineprefixes, if I use the default, then I have no troubles running games residing on the very same ntfs partition. So my question is, how do I put a wineprefix in an ntfs partition, or am I *really* supposed to do as the error message tells me and run wine as root??? I'd rather not run it as root, so I hope there is a better way. Also if I mount the partition with a specific uid, then no other user can use the wineprefixes but me...

Wine version: 1.2
Terminal output: wine: /mnt/ntfs/.wineprefixes/spirits  is not owned by you
Wine configuration: export WINEPREFIX=/mnt/ntfs/.wineprefixes/spirits (nothing more, once that is done, wine won't even run).
Other Wine applications: None, can't even get the wineprefix to be created.

---

