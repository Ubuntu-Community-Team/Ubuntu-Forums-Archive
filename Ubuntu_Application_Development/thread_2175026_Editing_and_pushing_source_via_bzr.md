---
title: "Editing and pushing source via bzr"
date: 2013-09-17
forum: Ubuntu Application Development
---

### Post by Lars Noodén on 2013-09-17
I'd like to edit the default bookmarks in Firefox from a bzr branch.  Getting the branch seems easy.  However, it looks like it is necessary to find the original file, patch it, modify it, and then make a new diff.  

```

bzr branch lp:firefox 

```

At that point I am stuck because the file *./firefox/debian/patches/ubuntu-bookmarks.patch* is simply a patch to some other file unfamiliar to me. What are the steps needed to get the source, patch it, (edit it), and then make a new diff?

---

