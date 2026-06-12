---
title: "Backing-up Wine to use on another Ubuntu box."
date: 2009-03-11
forum: Wine
---

### Post by CodyK46 on 2009-03-11
I'm interested in backing-up my Wine files to use on another Ubuntu machine. I have WoW, Steam and a few others that I don't want to download and install on another Ubuntu box. It would be a pain since I don't have the hard-copies of WoW and my Steam Games.  Since I have an external HD, i can back-up my files. So would it work or would Wine decide not to work if I copied and paste the files from my External HD?

---

### Post by DoktorSeven on 2009-03-11
Copying ~/.wine/ and subdirectories should work fine.  Just install Wine on the new machine and put .wine/ into your home directory.

---

### Post by CodyK46 on 2009-03-11
> **DoktorSeven said:**
> Copying ~/.wine/ and subdirectories should work fine.  Just install Wine on the new machine and put .wine/ into your home directory.

I just copied and paste the wine C:\ Drive on my EHD.

---

### Post by hikaricore on 2009-03-12
It would make more sense to copy the whole .wine folder just for simplicity sake, but whatever works for ya.

---

