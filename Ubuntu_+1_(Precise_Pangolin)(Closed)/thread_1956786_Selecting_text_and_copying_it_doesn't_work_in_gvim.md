---
title: "Selecting text and copying it doesn't work in gvim"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by georgelappies on 2012-04-11
Hi

When you select text in gvim and copy it and then want to paste it for instance in libre office writer it doesn't work. Is this a bug perhaps?

---

### Post by Gregory Lee on 2012-04-11
> **georgelappies said:**
> Hi

When you select text in gvim and copy it and then want to paste it for instance in libre office writer it doesn't work. Is this a bug perhaps?
More likely some mismatch between the vim version and initialization of gvim.  I don't use either libre office writer or gvim, but I had an issue something like yours using vim for copy/paste, which I reported on here, [http://ubuntuforums.org/showpost.php?p=11726012&postcount=10](http://ubuntuforums.org/showpost.php?p=11726012&postcount=10).  So one thing you can do is make sure your version of (g)vim has been compiled with support for the xterm clipboard.  See if "(g)vim --version" shows "+xterm_clipboard" in its output.

---

