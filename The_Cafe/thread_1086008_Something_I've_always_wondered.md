---
title: "Something I've always wondered"
date: 2009-03-03
forum: The Cafe
---

### Post by PurposeOfReason on 2009-03-03
I've always wondered why when you ls a directory, some files are colored while others are not. For example, I can ls one of my image directorys that has png and jpg files, all are white text, but if I do another, some are colored while others in that same directory are still while. Doesn't matter on the type of file.

---

### Post by DirtDawg on 2009-03-03
I thought the file type and permissions were what determined the colors. It's fairly consistent on my system.

---

### Post by billgoldberg on 2009-03-03
> **DirtDawg said:**
> I thought the file type and permissions were what determined the colors. It's fairly consistent on my system.

That would be correct. 

If you don't like the colors being used, by all means change them yourself:

[http://linux-sxs.org/housekeeping/lscolors.html](http://linux-sxs.org/housekeeping/lscolors.html)

---

### Post by PurposeOfReason on 2009-03-03
Thanks for the link, it makes ls browing much easier. I'm having a problem with the LS_COLORS line though. Most of it works, except the *.flac part and *.jpg which don't work. The *.png does though. :/

```

LS_COLORS='di=32;4:fi=34:ln=32;4:pi=5:so=5:bd=5:cd=5:or=31:mi=0:ex=35:*.flac=32;4:*.wma=32:*.png=91:*.jpg=91'
```

---

