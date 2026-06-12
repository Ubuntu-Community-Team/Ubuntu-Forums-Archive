---
title: "Is USP Open Source?"
date: 2006-12-17
forum: Ubuntu System Panel
---

### Post by coder_ on 2006-12-17
I'm wondering if USP is open source or not?  I've been looking, but can't find the source to compile from... :|  All I see are binary packages.

Thanks in advance.

---

### Post by Malac on 2006-12-17
> **coder_ said:**
> I'm wondering if USP is open source or not?  I've been looking, but can't find the source to compile from... :|  All I see are binary packages.

Thanks in advance.
USP is written in Python the code is just a text file.
If you open the .deb file in Archive Manager you can just read the code or install it and go to /usr/bin the file usp is there open it in Text Editor and voila.

Hope this helps.

---

### Post by coder_ on 2006-12-17
D'oh!  I didn't think of that  :D  Thanks ;)

Wow, I feel stupid :P  I had just read it was written in Python too :D

---

### Post by zietbukuel on 2007-01-05
> **Malac said:**
> USP is written in Python the code is just a text file.
If you open the .deb file in Archive Manager you can just read the code or install it and go to /usr/bin the file usp is there open it in Text Editor and voila.

Hope this helps.
Id like to have a generic tarball too... Thanks.

---

### Post by tuxcantfly on 2007-01-05
just make your own tarball.

dpkg -x /path/to/deb ./

that'll extract it, then just right-click, add to archive, select .tar.gz, compress, and you've got your tarball

---

