---
title: "File preview abilities"
date: 2013-09-29
forum: Ubuntu Development Version
---

### Post by Doug S on 2013-09-29
I wonder if someone using an up to date 13.10 desktop could try something for me and comment back.

Context: There are currently some issues with conditional code in the source files for ubuntu-docs (ends up as the installed yelp help files and the html files on help.ubuntu.com). The result is that information is sometimes included in the unity help that should only be in the GNOME help.

Reference: [https://help.ubuntu.com/13.10/ubuntu-help/files-preview.html](https://help.ubuntu.com/13.10/ubuntu-help/files-preview.html)  (13.10 pages are preliminary).

Please try the procedure described on that page. I suspect it is a GNOME thing and not Unity, but and as mentioned above, the conditional code is giving troubles.
For me, I don't get any file preview using either Unity desktop or GNOME desktop. However, my 13.10 desktop is a VM and I have been having lots of grief with it, so I am looking for someone else to try it.

---

### Post by cariboo on 2013-09-29
It may be a something that Gnome does that Unity doesn't, as I tried the procedure on the wiki page, and nothing happens when I press the space bar, and if I just press the **r** key, it just opens the search bar.

---

### Post by Doug S on 2013-09-29
> **cariboo907 said:**
> It may be a something that Gnome does that Unity doesn't, as I tried the procedure on the wiki page, and nothing happens when I press the space bar, and if I just press the **r** key, it just opens the search bar.Yes, I think you are right, and thanks for trying. I'm looking for someone to confirm that is works for them on GNOME, as it doesn't work for me.

---

### Post by cariboo on 2013-09-30
I'll be installing Gnome later this week, but if someone can chime in before then go ahead.

---

### Post by RavisPohan on 2013-09-30
Works absolutely fine for me on Ubuntu Gnome with next/gnome3/gnome3-staging PPAs.

---

### Post by mc4man on 2013-09-30
Maybe I'm missing something here but I believe the 'file preview' (with space bar) is a function of gnome-sushi. So if it's installed it should work, if not it obviously won't.
(isn't default installed in Ubuntu or installed in Ubuntu when installing gnome-shell Ubuntu repo version
Whether it has glitches in an ubuntu session vs. gnome session I don't know but I gather that's not the question anyway.

---

### Post by Doug S on 2013-09-30
> **mc4man said:**
> Maybe I'm missing something here but I believe the 'file preview' (with space bar) is a function of gnome-sushi...No, it was me that was "missing something". I did not know that GNOME flashback and GNOME are two different things. If I create a fresh GNOME 13.10 computer, then the space bar file preview stuff works fine. So now at least the documentation issues make sense, i.e. that (Unity) help page I referenced in my OP shouldn't be there.

---

