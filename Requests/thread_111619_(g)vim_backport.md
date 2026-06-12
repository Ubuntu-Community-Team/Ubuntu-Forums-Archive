---
title: "(g)vim backport"
date: 2006-01-02
forum: Requests
---

### Post by Hezekiah on 2006-01-02
I would like to request a backport of vim and gvim (along with the other vim-related packages as well, though I'm only interested specifically in vim and gvim).  The current Breezy version is 6.3.x, while Dapper currently has 6.4.x.

vim 6.4 has several bugs fixed, mainly to language definitions and syntax highlighting, along with several other improvements.

Thanks!

---

### Post by jdong on 2006-01-02
are 6.3.x vimrc's compatible with 6.4?

---

### Post by GothicX on 2006-01-02
[http://groups.yahoo.com/group/vimannounce/message/144](http://groups.yahoo.com/group/vimannounce/message/144)

I think yes =) because it's mostly bug fixing...

---

### Post by Hezekiah on 2006-01-02
To 'me too' on this, I am pretty sure the .*vimrc files are compatible between 6.3 and 6.4.  I have compiled 6.4 myself from tarball and it worked with all of the plugins and rc files I use on Breezy.

---

### Post by Oxygene on 2006-01-27
I would appreciate a backport too.
There is a bug in 6.3 with mksession not supporting paths with spaces which is fixed in 6.4

---

### Post by Velvet Elvis on 2006-02-01
Don't forget that Cream would likely have to be backported as well.

---

### Post by Hezekiah on 2006-02-05
I don't think that Cream would /require/ a backport, but it probably would be nice to backport it as well.

That said, I am in the middle of compiling a backport of vim-6.4 from Dapper, and the build process requires Dapper's version of make and texi2html to be backported as well.  I don't think they are required to be able to install the final vim* debs, but they are additional requirements for the backport compilation which may prove problematic...

That said, the latest Dapper gtk and gnome vim packages provide a menu icon for gvim (though it is hidden by default) in addition to the numerous fixes vim64 provides over vim63.

---

