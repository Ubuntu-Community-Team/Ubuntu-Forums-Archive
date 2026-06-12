---
title: "Server- No Precise ppa for Byobu?"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MAFoElffen on 2012-01-16
Added Byobu PPA 3 times... Of course to do that, add-apt-repository was missing so I had to install package python-software-properties.

On aptitude update, they were 404/not found.

To remove from getting that error, installed ppa-purge... which did nothing and had to remove manually from /etc/apt/sources.list.d/

I had also installed the PPA manually, same results.  I guess I could change it to the Oneiric ppa? 

Or just wait for it to show up for Precise...

---

### Post by xyzzyman on 2012-01-16
I looked at the PPA and they don't have it up for Precise. Lots of PPA's don't update until the distro is actually released... I may be reading it wrong but it looks like the binaries for precise were uploading to the main distribution possibly, at least the i386 binaries. You can always compile from the bzr or try installing the oneiric debs which will probably work.

---

