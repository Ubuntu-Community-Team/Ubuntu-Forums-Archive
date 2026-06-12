---
title: "apt-move and custom packages"
date: 2008-09-04
forum: Repositories &amp; Backports
---

### Post by tommoyer324 on 2008-09-04
Is it possible to create custom packages and then use apt-move to maintain a repository?  Every time I try, it will move debs in but it complains about files being skipped and if I try and delete obsolete packages, it wants to delete every custom package I have in the repository.  I have the packages set up in a repository that is in my sources.list, which seems to indicate to me (from reading the man pages on apt-move) that they should not be considered obsolete.

Any help would be great.  Also if it matters, the custom packages are a mix of custom code in some packages and rebuilds of other packages with custom patches.

---

### Post by OptikKnight on 2008-09-10
I'm interested in this too. Unfortunately I don't have any assistance to offer on the subject, as I'm also new to it.

---

