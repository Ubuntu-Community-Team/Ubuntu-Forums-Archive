---
title: "aptitude full-upgrade"
date: 2012-06-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Gregory Lee on 2012-06-26
Since February, I've been keeping my distribution up to date with the software repositories using aptitude (on recommendation from several experts here), and I've noticed a couple of peculiarities in the way aptitude works that make it necessary sometimes to use "aptitude full-upgrade".  I thought other aptitude users might like to know about this, if I'm right.

I use "aptitude update" followed by "aptitude safe-upgrade".  It's good to avoid "aptitude full-upgrade", because occasionally that will have the effect of removing important parts of the software distribution.  But it's harmless to call up "aptitude full-upgrade" from the command line, since it won't actually do anything unless you confirm that you want it to proceed, after looking at the summary it gives you on screen of what it will do if you give it the okay.

Here are two cases where "aptitude safe-upgrade" has refused to update some packages, yet it seems harmless to go ahead with "aptitude full-upgrade":  (1) occasionally, it's apparently a mistake that the safe upgrade left an update undone.  This morning, for instance, when I did "aptitude safe-upgrade", it held back updating "libmusicbrainz4-3", but then "aptitude full-upgrade" offered to do this update without mentioning any removals or other updates.  So I told it to go ahead and do it.

(2) Sometimes aptitude needs to replace a package, by first removing it then downloading a new version.  "aptitude safe-upgrade" won't do it, since it involves removing a package, yet you won't be left without the package, so I think it is okay to let "aptitude full-upgrade" go ahead and do the replacement.  When this happens, you can tell it's going to be a replacement, because the on screen summary will show the package to be replaced with "{a}" after its name and the new package that replaces it will be shown below that with "{b}" after the same name.

---

### Post by philinux on 2012-06-26
After last cycle's discussion I would stick to synaptic or apt-get.

[http://ubuntuforums.org/showpost.php?p=11464224&postcount=22](http://ubuntuforums.org/showpost.php?p=11464224&postcount=22)

---

