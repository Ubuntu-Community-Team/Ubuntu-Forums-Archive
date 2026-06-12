---
title: "comparing repositories from debian and ubuntu"
date: 2005-12-04
forum: Repositories &amp; Backports
---

### Post by gambarimasu on 2005-12-04
hi,

the impression i get is that ubuntu has fewer supported packages but about the same number of packages overall if you trust universe.  is that correct?  

i'd kinda like to know more about the differences.

is there an easy way to get a big list of packages (just the names) from the various ubuntu repositories and the various debian ones?  i want to do a diff of sarge vs. breezy without universe, sarge vs. breezy with universe, sid vs. breezy, etc.

i'm a debian user considering switching to ubuntu and still learning about ubuntu.  hope my question makes sense and is appropriate to forum.

thanks.

---

### Post by aysiu on 2005-12-04
apt-get.org
packages.ubuntu.com

Those may help.

---

### Post by gambarimasu on 2005-12-04
[QUOTE=aysiu]apt-get.org
packages.ubuntu.com

Those may help.[/QUOTE]

thanks, but i didn't find just lists of differences or lists of package names in downloadable form there that i can run through the command line programs diff, sort, comm, etc.

i think i can get Packages.gz files or something for various things and parse them, but that would take too much time.

i thought there might be a command that got me the package lists.

---

### Post by Galoot on 2005-12-04
Try:

[http://packages.ubuntu.com/breezy/allpackages.en.txt.gz](http://packages.ubuntu.com/breezy/allpackages.en.txt.gz)
and
[http://packages.debian.org/unstable/allpackages.en.txt.gz](http://packages.debian.org/unstable/allpackages.en.txt.gz)

Go up a few directories in each and find the particular distro you're interested in comparing. Look for the link at the bottom of [this page, for example]("http://packages.ubuntu.com/breezy/"), that reads "(compact compressed textlist)"

You'll probably have to mess with the files a bit, but it looks like each line reads:

package_name SPACE (version number) SPACE other_stuff_you_don't_need

It shouldn't be too hard to filter out all but what you want from each list.

---

