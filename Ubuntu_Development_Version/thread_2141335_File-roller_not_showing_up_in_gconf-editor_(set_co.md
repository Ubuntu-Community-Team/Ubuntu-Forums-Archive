---
title: "File-roller not showing up in gconf-editor (set compression level)"
date: 2013-05-02
forum: Ubuntu Development Version
---

### Post by DenHeldert on 2013-05-02
I want to set the compression level for file-roller.
More precise, I want to disable compression and just store files as an archive. (Compression level 0)
I installed gconf-editor to get the job done as explained [here]("http://ubuntuforums.org/archive/index.php/t-1381517.html").

But when I start gconf-editor and look in the /apps section mentioned, there is no file-roller-entry.
Maybe it has something to do with the Ubuntu release I'm running (13.04) or the fact I use the KDe desktop environment, I don't know.

I removed file-roller and reinstalled, hoping it would show up when installing file-roller after installing gconf-editor. But no luck.
(Initially I installed file-roller first)

**- How do I get file-roller to show in gconf-editor?**

or:

**- Is there another way to set the compression level?**

Any help would be greatly appreciated.

---

### Post by ibjsb4 on 2013-05-02
Its in dconf these days.

[ATTACH=CONFIG]242089[/ATTACH]

---

### Post by DenHeldert on 2013-05-02
> **ibjsb4 said:**
> Its in dconf these days.



Meaning I need to uninstall gconf-editor and install [dconf-editor]("https://apps.ubuntu.com/cat/applications/dconf-tools/")?

---

### Post by ibjsb4 on 2013-05-02
Nope, you can have both. Gconf still has its uses.

---

### Post by DenHeldert on 2013-05-02
> **ibjsb4 said:**
> Its in dconf these days.



Worked like a charm.
Thank you very much for helping me out for the second time today btw.

---

### Post by dino99 on 2013-05-02
gconf was a gtk2 tool; now we are using gtk3 (with dconf instead)

---

### Post by ibjsb4 on 2013-05-02
Welcome :)

---

