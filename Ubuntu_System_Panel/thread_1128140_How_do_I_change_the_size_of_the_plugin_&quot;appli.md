---
title: "How do I change the size of the plugin &quot;applications&quot;"
date: 2009-04-17
forum: Ubuntu System Panel
---

### Post by Pafrapé on 2009-04-17
I want to change some elements in the plugin "applications":
- How to enlarge the size of the column category?
- How to get the name of the application appears in full and no longer with "..." at the end.

---

### Post by Malac on 2009-04-18
> **Pafrapé said:**
> - How to enlarge the size of the column category?In applications.py
Change [COLOR=Red]Red[/COLOR] number in line 477:
```
CategoryButton = MakeAButton( [COLOR=Red]140[/COLOR], -1, gtk.RELIEF_NONE, "distributor-logo", 0, 0, 16, ["All"], [DirStyle] )
```and line 479:```
CategoryButton = MakeAButton( [COLOR=Red]100[/COLOR], -1, gtk.RELIEF_NONE, "", 0, 0, 0, ["All"], [DirStyle] )
```and line 503:```
CategoryButton = MakeAButton( [COLOR=Red]140[/COLOR], -1, gtk.RELIEF_NONE, child.icon, 0, 0, 16, [child.name], [DirStyle] )
```and line 505:```
CategoryButton = MakeAButton( [COLOR=Red]100[/COLOR], -1, gtk.RELIEF_NONE, "", 0, 0, 0, [child.name], [DirStyle] )
```
> **Pafrapé said:**
> - How to get the name of the application appears in full and no longer with "..." at the end.In easybuttons.py
Change line 50 to:```
[COLOR=Red]#[/COLOR]Label1.set_ellipsize( pango.ELLIPSIZE_END )
``` This will remove the "..." and truncation.

Hope this helps.

---

### Post by Pafrapé on 2009-04-18
Thank you very much.
It's perfect.

---

### Post by Pafrapé on 2009-04-19
It's almost perfect, except for the names of applications: "..." have disappeared, for against the names of the application is not over. How to have it be over?

---

### Post by Malac on 2009-04-21
> **Pafrapé said:**
> It's almost perfect, except for the names of applications: "..." have disappeared, for against the names of the application is not over. How to have it be over?
My apologise I don't understand. Could you post a screenshot?
Thanks.

---

