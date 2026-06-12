---
title: "Apt-get for creating cd repository"
date: 2005-04-05
forum: Repositories &amp; Backports
---

### Post by UbuWu on 2005-04-05
Is it possible to use apt-get to download packages with the needed dependencies, even if you have them already installed? I wanted to make a cd with packages for my home computer, but can't find an easy way to do this except for starting with a clean install, then apt-getting the packages and then put the cached debs on the cd. But I don't want everything on the cd I have currently installed on my system. And besides that I already wiped the cache directory some time ago.

---

### Post by soul_rebel on 2005-04-07
Id like to do this too

---

### Post by mendicant on 2005-04-07
Look at aptitude download and, in utils/universe, apt-rdepends (at least, that's the listing under hoary).
For instance:
% apt-rdepends --state-follow=Installed --state-show=Installed gaim
...
  Depends: gaim-data (= 1:1.1.4-1ubuntu4)
  Depends: libao2 (>= 0.8.5)
  Depends: libaspell15 (>= 0.50.5)
  Depends: libatk1.0-0 (>= 1.9.0)
  Depends: libaudiofile0 (>= 0.2.3-4)
...
You then need to do same parsing on this to extract only the package names, sort and uniq them, then use aptitude download on the resultant list of packages.  You can probably just use something like:

% apt-rdepends --state-follow=Installed --state-show=Installed gaim | cut -d ' ' -f 4 | sort | uniq

---

