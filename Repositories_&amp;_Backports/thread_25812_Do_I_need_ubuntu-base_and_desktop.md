---
title: "Do I need ubuntu-base and desktop"
date: 2005-04-10
forum: Repositories &amp; Backports
---

### Post by Campitor on 2005-04-10
I'm upgrading to Hoary with dist-upgrade.  Now that Hoary has been released do I need to include these:

sudo apt-get install ubuntu-base ubuntu-desktop 

?

camp

---

### Post by skoal on 2005-04-11
I had to remove those packages to trim some fat from my install, namely the 400 pound gorilla emacs.  I only need my 20 pound monkey vi.  I haven't had any issues or problems after removing these 2 packages.

---

### Post by Leif on 2005-04-11
I would reinstall them, as the desktop does have new stuff tied to it. You can trim the fat again afterwards.

---

### Post by az on 2005-04-11
Update your repositories to hoary in synaptic.  Select the two packages and you will see everything marked for installation. You can then scroll around and unselet what you do not want.  Thew first thing you unselect will unselect the corresponding metapackage, but not the rest -  that is the beauty of marking packages.  Make it go when you have finished pruning.

---

